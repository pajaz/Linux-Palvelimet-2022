# Luento 2 Kotitehtävät

## CLI

## z) Lue ja tiivistä. Tiivistelmäksi riittää muutama ranskalainen viiva per artikkeli. (Tässä z-alakohdassa ei tarvitse tehdä testejä tietokoneella)
  
* Karvinen 2020: [Command Line Basics Revisited](https://terokarvinen.com/2020/command-line-basics-revisited/)  
* YCombinator Hacker News, [vapaavalintainen artikkeli kommentteineen Linuxin komentokehotteesta](https://hn.algolia.com/?dateEnd=1643270199&dateRange=custom&dateStart=1547942400&page=0&prefix=false&query=command%20line&sort=byPopularity&type=story) (Kommentit aukeavat siitä pienestä "420 comments" linkistä Riittää, kun silmäilet artikkelin ja kommentit soveltuvin osin, osa voi olla kirjan mittaisia etkä ehdi tässä lukea niitä kokonaan. Samoin tiivistelmäksi riittää muutama bulletti, ei tarvitse kattaa koko sisältöä)  
  
## a) FHS. Esittele kansiot, jotka on listattu "Command Line Basics Revisited" kappaleessa "Important directories". Näytä kuvaava esimerkki kunkin tärkeän kansion sisältämästä tiedostosta tai kansiosta. Jos kyseessä on tiedosto, näytä siitä kuvaava esimerkkirivi. Työskentele komentokehotteessa ja näytä komennot, joilla etsit esimerkit.

1. / eli root  
    * Koko Linuxin tiedostojärjestelmän ylin hakemisto eli juuri ja pitää siis sisällään kaikki muut tärkeät ja vähemmän tärkeät kansiot.
    pajazzo@derpface:/$ cd /  
    pajazzo@derpface:/$ pwd  
    /  
    pajazzo@derpface:/$ ls  
    bin  boot  dev  etc  home  initrd.img  initrd.img.old  lib  lib32  lib64  libx32  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr var  vmlinuz  vmlinuz.old  

    * Operoiminen kansiossa vaatii superuser oikeudet. Esimerkki:  
    pajazzo@derpface:/$ touch test.txt  
    touch: cannot touch 'test.txt': Permission denied _(Oikeudet kansion luontiin eivät riitä)_  
    pajazzo@derpface:/$ ls -p | grep test  _(Huomataan, ettei tiedostoa tosiaan luotu)_  
    pajazzo@derpface:$ sudo touch test.txt _(Uusi yritys superuserina)_  
    pajazzo@derpface:/$ ls -p | grep test   
    test.txt _(Tiedosto luotu onnistuneesti)_  

2. /home/  
    * Pitää sisällään käyttäjien kotihakemistot, eli jokaisen käyttäjän henkilökohtaisen kansiot/tiedostot sekä lost+found hakemiston, johon järjestelmä yrittää pelastaa korruptoituneita tai mahdollisesti korruptoituneita tiedostoja esim. kun tietokoneen virta katkeaa yllättäen kesken suorituksen.  
    pajazzo@derpface:/home$ cd /home/  
    pajazzo@derpface:/home$ pwd  
    /home  
    pajazzo@derpface:/home$ ls  
    lost+found  pajazzo  
    pajazzo@derpface:/home$   
    * Oletuksena uusilla luoduilla käyttäjäprofiileilla on oikeus katsella toisen käyttäjän home kansion tiedostoja, mutta ei kirjoitusoikeuksia.  
        - Luodaan uusi käyttäjä koneelle:  
        pajazzo@derpface:/$ sudo adduser watcher  
        Adding user `watcher' ...  
        Adding new group `watcher' (1001) ...  
        Adding new user `watcher' (1001) with group `watcher' ...  
        Creating home directory `/home/watcher' ...  
        Copying files from `/etc/skel' ...  
        New password:   
        Retype new password:   
        passwd: password updated successfully  
        Changing the user information for watcher  
        Enter the new value, or press ENTER for the default  
        Full Name []: WW    
        Room Number []:  
        Work Phone []:  
        Home Phone []:  
        Other []:  
        Is the information correct? [Y/n] Y  
        pajazzo@derpface:/home$ ls -l  
        total 24  
        drwx------  2 root    root    16384 Jan 20 12:31 lost+found  
        drwxr-xr-x 27 pajazzo pajazzo  4096 Jan 31 13:29 pajazzo  
        drwxr-xr-x 15 watcher watcher  4096 Jan 31 13:40 watcher  
            
        - Rivien selitykset:
            1. Ensimmäinen kolumni ilmoittaa kansioiden ja tiedostojen käyttöoikeudet ja sen ensimmäinen merkki ilmoittaa tiedostotyypin.  
                * d = directory eli kansio. Home kansiossa ei ole muun tyyppisiä.  
                * Ensimmäiset kolme merkkiä tyypin jälkeen ovat tiedoston omistajan oikeudet (tässä tapauksessa read, write ja execute eli täydet oikeudet).  
                * Seuraavat kolme ilmoittavat tiedoston käyttäjäryhmään kuuluvien käyttäjien oikeudet (tässä tapauksessa read ja execute).  
                * Viimeiset kolme ilmoittavat muiden käyttäjien oikeudet, jotka ovat tässä samat kuin ryhmäkäyttäjillä.  
            2. Seuraava kolumni ilmoittaa tiedostoon osoittavien hard-linkien määrän. Eli kuinka monessa paikassa tiedostojärjestelmässä on viittaus tähän tiedostoon. Kun Linuxissa tiedoston poistaa, laskee tämä luku yhdellä ja sen pudotessa nollaan toteaa järjestelmä, että tiedostoa ei enää tarvita ja poistaa sen. [Lähde](https://linuxconfig.org/understanding-of-ls-command-with-a-long-listing-format-output-with-permission-bits)  
            3. Omistaja  
            4. Käyttäjäryhmä johon tiedosto kuuluu  
            5. Koko  
            6. Edellinen muokkauspäivä  
        - Voin siis mennä katselemaan käyttäjänä pajazzo käyttäjän watcher tiedostoja ja jopa suorittaa niitä, mutta en muokata.   
            - Otetaan nuo oikeudet pois:  
            pajazzo@derpface:/home$ sudo chmod o-rx watcher/  _(chmodin -o tarkoittaa oikeuksia others ja -rx poistetaan read ja execute oikeudet)_  
            pajazzo@derpface:/home$ ls  
            lost+found  pajazzo  watcher  
            pajazzo@derpface:/home$ ls -l  
            total 24  
            drwx------  2 root    root    16384 Jan 20 12:31 lost+found  
            drwxr-xr-x 27 pajazzo pajazzo  4096 Jan 31 13:29 pajazzo  
            drwxr-x--- 15 watcher watcher  4096 Jan 31 13:40 watcher  
            pajazzo@derpface:/home$ cd watcher/  
            bash: cd: watcher/: Permission denied  
                












## b) My CLI. Keksi jokin asia, jota haluaisit tehdä komentokehotteessa. Etsi ja asenna komentokehotteen paketinhallinnasta ohjelmat, joilla asian voi ratkaista. Asenna ainakin kolme itsellesi uutta komentorivillä (command line interface, CLI) tai tekstitilassa (text user interface, TUI) toimivaa ohjelmaa. Näytä, miten kuvitteellista ongelmaa voi ratkoa näillä ohjelmilla. Voit valita jonkin helpon tai yksinkertaistetun esimerkin.

## c) Tukki. Aiheuta lokiin kaksi eri tapahtumaa: yksi esimerkki onnistuneesta ja yksi esimerkki epäonnistuneesta tai kielletystä toimenpiteestä. Analysoi rivit yksityiskohtaisesti.

## d) The Friendly M. Näytä 2-3 kuvaavaa esimerkkiä grep-komennon käytöstä. Ohjeita löytyy 'man grep' ja tietysti verkosta.

## e) Pwnkit. Päivitä kaikki Linux-ohjelmat ja asenna tietoturvapäivitykset.

## y) cdlspwd! Opettele tärkeimmät komennot ulkoa ja harjoittele suurella määrällä kokeiluja. Opeteltavat komennot ovat artikkelissa Karvinen 2020: Command Line Basics Revisited (tätä y-alakohtaa ei tarvitse raportoida lainkaan)

## Bonus: Recursive. Pystytkö etsimään kaikki rivit, joilla lukee Tero isolla tai pienellä, kun tiedostoja on sisäkkäisissä kansioissa? (Eli tutkimaan jonkin kansion kaikkine alihakemistoineen)

# g) Sshecrets. Vaikeampi vapaaehtoinen bonuskohta, ei ole opetettu vielä: Asenna SSH-demoni. Kokeile omalla ssh-palvelimellasi jotain seuraavista: ssh-copy-id, sshfs, scp tai git. (Helpoin lienee scp: ‘scp foo.txt tero@example.com:’)
