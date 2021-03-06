# Luento 2 Kotitehtävät
  
Osa kurssia Linux Palvelimet ICT4TN021-3018 Haaga-Helia Ammattikorkeakoulussa  
Kurssin vetäjä: [Tero Karvinen](https://terokarvinen.com/2021/linux-palvelimet-ict4tn021-3018/)  
  
## CLI

## z) Lue ja tiivistä. Tiivistelmäksi riittää muutama ranskalainen viiva per artikkeli. (Tässä z-alakohdassa ei tarvitse tehdä testejä tietokoneella)
  
* Karvinen 2020: [Command Line Basics Revisited](https://terokarvinen.com/2020/command-line-basics-revisited/)  
* YCombinator Hacker News, [vapaavalintainen artikkeli kommentteineen Linuxin komentokehotteesta](https://hn.algolia.com/?dateEnd=1643270199&dateRange=custom&dateStart=1547942400&page=0&prefix=false&query=command%20line&sort=byPopularity&type=story) (Kommentit aukeavat siitä pienestä "420 comments" linkistä Riittää, kun silmäilet artikkelin ja kommentit soveltuvin osin, osa voi olla kirjan mittaisia etkä ehdi tässä lukea niitä kokonaan. Samoin tiivistelmäksi riittää muutama bulletti, ei tarvitse kattaa koko sisältöä)  

### 5 Command Line Tools to Break Your Dependence on the GUI (kirjoitettu 3.2.2022)
Artikkeli: https://www.putorius.net/5-cool-command-line-tools.html  
Hackernew kommenttiosio: https://news.ycombinator.com/item?id=21711761  

Artikkeli esittelee Linux sysadmineille erilaisia komentoriviltä pyöriviä sovelluksia jotta nämä eivät joutuisi selainta käyttäessään erilaisten houkutusten, kuten sosiaalisen median vietäviksi tehokkaan työskentelyn sijaan.  
Esitellyt työkalut ovat:  
* wttr.in - käyttö curl wttr.in/ komennolla ja mahdollisilla argumenteilla kuten wttr.in/Helsinki?0 joka palauttaa Helsingin tämän hetkisen sään komentoriville. Vaikuttaa itseasiassa kätevältä. Ilman argumentteja saat IP-osoitteesi paikkakunnan sään ja ennusteen useammalle päivälle.    
* bc komento laskimen käyttöön.  
* dictd sanakirja joka asennetaan apt-get install dictd komennolla. Itselläni tuo ei alkanut asennuksen ja uuden komentokehotteen avaamisenkaan jälkeen toimimaan. Sama kirjoittaja on myös kirjoittanut kyseisestä sovelluksesta aikaisemman [artikkelin](https://www.putorius.net/linux-command-line-dictionary.html) jossa itsekin epäilee sen tarpeellisuutta tänä päivänä.  
* googler eli Google haut komentokehotteelta. En lähde testaamaan, koska en näe itse tarvetta tällaiselle.  
* aspell oikeinkirjoituksen tarkistus -sovellus. En tätäkään lähde asentamaan nyt.  
  
Artikkelin otsikko oli mielenkiintoinen, minkä takia aloinkin sitä lukemaan. En kuitenkaan tunnista ongelmaa, jonka kirjoittaja esittää. Jos etsin  ratkaisua selaimen kanssa, harvemmin eksyn sivuraiteille, koska olen keskittynyt ongelmanratkaisuun (enkä käytä juurikaan googlea joka artikkelilla mainitaan pahana mainosten syöttäjänä). Samanlaista kommentointia löytyy myös Hackernewsin [kommenttiosastolta](https://news.ycombinator.com/item?id=21711761). Mm. kommentti käyttäjältä pjmlp "I love my dependence on the GUI, otherwise would still be stuck using MS-DOS." on varsin osuva, koska GUI ei todellakaan ole ikävä asia vaan kehityksen mukanaan tuoma helpotus käyttäjille.  
Oma näkemykseni on kuitenkin kuten artikkelin kirjoittajallakin, että komentoriviltä voi suorittaa useita asioita paljon GUI:ta kätevämmin (kirjoitin itsekin pienen skriptin, jolla saan kurssin sivulta kätevästi määrittämäni viikon kotitehtävät haluamaani tiedostoon selkokielisenä). Kuitenkin kirjoittajan lähestymitapa ongelmaan ei juurikaan puhuttele minua.  

## a) FHS. Esittele kansiot, jotka on listattu [Command Line Basics Revisited](https://terokarvinen.com/2020/command-line-basics-revisited/) kappaleessa "Important directories". Näytä kuvaava esimerkki kunkin tärkeän kansion sisältämästä tiedostosta tai kansiosta. Jos kyseessä on tiedosto, näytä siitä kuvaava esimerkkirivi. Työskentele komentokehotteessa ja näytä komennot, joilla etsit esimerkit.

1. / eli root  
    * Koko Linuxin tiedostojärjestelmän ylin hakemisto eli juuri ja pitää siis sisällään kaikki muut tärkeät ja vähemmän tärkeät kansiot.
    pajazzo@derpface:/$ cd /  
    pajazzo@derpface:/$ pwd  
    /  
    pajazzo@derpface:/$ ls  
    bin  boot  dev  etc  home  initrd.img  initrd.img.old  lib  lib32  lib64  libx32  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr var  vmlinuz  vmlinuz.old  

    * Operoiminen kansiossa vaatii superuser oikeudet. Esimerkki:  
    pajazzo@derpface:/$ touch test.txt  
    touch: cannot touch 'test.txt': Permission denied *(Oikeudet kansion luontiin eivät riitä)*  
    pajazzo@derpface:/$ ls -p | grep test  *(Huomataan, ettei tiedostoa tosiaan luotu)*  
    pajazzo@derpface:$ sudo touch test.txt *(Uusi yritys superuserina)*  
    pajazzo@derpface:/$ ls -p | grep test   
    test.txt *(Tiedosto luotu onnistuneesti)*  

2. /home/  
    * Pitää sisällään käyttäjien kotihakemistot, eli jokaisen käyttäjän henkilökohtaiset kansiot/tiedostot sekä [lost+found](https://www.howtogeek.com/282374/what-is-the-lostfound-folder-on-linux-and-macos/) hakemiston, johon järjestelmä yrittää pelastaa korruptoituneita tai mahdollisesti korruptoituneita tiedostoja esim. kun tietokoneen virta katkeaa yllättäen kesken suorituksen.  
    pajazzo@derpface:/home$ cd /home/  
    pajazzo@derpface:/home$ pwd  
    /home  
    pajazzo@derpface:/home$ ls  
    lost+found  pajazzo  
    pajazzo@derpface:/home$   
    * Oletuksena uusilla luoduilla käyttäjäprofiileilla on oikeus katsella toisen käyttäjän home kansion tiedostoja, mutta ei kirjoitusoikeuksia (demonstraatio edellä).  
        - Luodaan uusi käyttäjä koneelle:  
        pajazzo@derpface:/$ sudo adduser watcher  
        Adding user \`watcher' ...  
        Adding new group \`watcher' (1001) ...  
        Adding new user \`watcher' (1001) with group \`watcher' ...  
        Creating home directory \`/home/watcher' ...  
        Copying files from \`/etc/skel' ...  
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
            
        - Rivien selitykset [tästä](https://medium.com/@scottdebian/the-ls-command-in-linux-and-all-its-options-17ba8784a709):  
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
            pajazzo@derpface:/home$ sudo chmod -R o-rx watcher/  *(chmodin -R rekursiivisesti kaikille sijainnin tiedostoille, -o oikeuksia others ryhmälle ja -rx poistetaan read ja execute oikeudet, lähteenä man chmod ja oma muisti chmodin käytöstä)*  
            pajazzo@derpface:/home$ ls  
            lost+found  pajazzo  watcher  
            pajazzo@derpface:/home$ ls -l  
            total 24  
            drwx------  2 root    root    16384 Jan 20 12:31 lost+found  
            drwxr-xr-x 27 pajazzo pajazzo  4096 Jan 31 13:29 pajazzo  
            drwxr-x--- 15 watcher watcher  4096 Jan 31 13:40 watcher  
            pajazzo@derpface:/home$ cd watcher/  
            bash: cd: watcher/: Permission denied  
            pajazzo@derpface:/home$ su  
            Password:   
            root@derpface:/home# cd watcher/   
            root@derpface:/home/watcher# ls -l  
            total 32  
            drwxr-x--- 2 watcher watcher 4096 Jan 31 13:36 Desktop  
            drwxr-x--- 2 watcher watcher 4096 Jan 31 13:36 Documents  
            drwxr-x--- 2 watcher watcher 4096 Jan 31 13:36 Downloads  
            drwxr-x--- 2 watcher watcher 4096 Jan 31 13:36 Music  
            drwxr-x--- 2 watcher watcher 4096 Jan 31 13:36 Pictures  
            drwxr-x--- 2 watcher watcher 4096 Jan 31 13:36 Public  
            drwxr-x--- 2 watcher watcher 4096 Jan 31 13:36 Templates  
            drwxr-x--- 2 watcher watcher 4096 Jan 31 13:36 Videos  
              
            Kuten nähdään oikeudet on nyt poistettu sekä kotikansiosta, että sen alikansioilta. Tein samat komennot käyttäjälle pajazzo, koska en jaksa alkaa leikkimään enempää tuolla uudella tunnuksella. Eli poistin others ryhmältä rekursiivisesti kaikki oikeudet käyttäjän pajazzo home -kansioon.  
            Nyt ongelmana on, että uusia tiedostoja luodessani on others -ryhmällä ja pajazzon käyttäjäryhmällä kuitenkin lukuoikeus näihin tiedostoihin:  
            pajazzo@derpface:\~$ pwd  
            /home/pajazzo  
            pajazzo@derpface:\~$ touch test.txt   
            pajazzo@derpface:\~$ ls -l | grep test  
            -rw-r--r-- 1 pajazzo pajazzo 0 Jan 31 15:21 test.txt  

            Käytetään [umask komentoa](https://geek-university.com/linux/set-the-default-permissions-for-newly-created-files/) määrittämään uusien tiedostojen luvat.  
              
            pajazzo@derpface:\~$ umask (tarkistetaan mitkä umask oikeudet ovat tällä hetkellä)
            0022 (samat oikeudet kuin root käyttäjällä. Kaksi kakkosta perässä tarkoittavat, että käyttäjän ryhmällä sekä others -ryhmällä ei ole kirjoitusoikeutta (x = 1, w = 2, r = 4) uusiin tiedostoihin. Suoritusoikeus (x = execute) on oletuksena poissa tiedostoilta)  
            pajazzo@derpface:\~$ nano .bashrc  > Lisätään tiedoston loppuun rivi umask 077 (4+2+1= 7 eli poistetaan kaikki oikeudet sekä ryhmältä, että käyttäjiltä uusiin tiedostoihin ja kansioihin, tallennetaan ja avataan uusi terminaali)  
            pajazzo@derpface:\~$ umask  
            0077  
            pajazzo@derpface:\~$ touch test1.txt && mkdir test1  
            pajazzo@derpface:\~$ ls -l | grep test  
            drwx------ 2 pajazzo pajazzo     4096 Jan 31 15:37 test1  
            -rw------- 1 pajazzo pajazzo        0 Jan 31 15:37 test1.txt  

            Oikeudet näyttäisi olevan kunnossa, koska ensimmäisen kolumnin kolme viimeistä merkkiä ovat --- ja home -sijainti siis vain pajazzon käytössä.  

    * Tämä tehtävä lähti vähän laukalle, koska minua alkoi kiinnostaa tiedostojen pääsyoikeudet.  


3. /home/pajazzo/  
    * Käyttäjän oma kansio johon käyttäjä voi tallentaa dataa pysyvästi kuten käyttäjän itse luomat tiedostot, sovellusten käyttäjäkohtaiset tiedostot tai vaikka scriptejä jotka ajetaan käyttäjän määrittämänä ajankohtana (esim. sisäänkirjautuessa)  
    * Esimerkki hyödyllisestä/tärkeästä tiedostosta:  
        + pajazzo@derpface:\~$ ls -la | grep bash  
        -rw-------  1 pajazzo pajazzo 24598 Jan 31 16:06 .bash_history  
        -rw-r-----  1 pajazzo pajazzo   220 Jan 20 12:44 .bash_logout  
        **-rw-r-----  1 pajazzo pajazzo  3537 Jan 31 15:34 .bashrc**  
        + [.bashrc](https://cloudzy.com/knowledge-base/what-is-linux-bashrc-and-how-to-use-it-full-guide/) tiedoston sisältö suoritetaan joka kerta, kun uusi terminaali-istunto avataan (kuten edellisessä tehtävässä huomattiin, kun muokattuani tiedostoa, käynnistin uuden terminaali-istunnon)  

4. /etc/  
    * Kaikkea kivaa eli järjestelmän konfiguraatiot.  
    * Koska en käyttänyt non-free ratkaisua oman Debian asennukseni tekemiseksi jouduin käydä muokkaamassa seuraavaa tiedostoa, jotta saan joitain proprietary ajureita asennuttua:   
    pajazzo@derpface:/$ cd etc/apt/  
    pajazzo@derpface:/etc/apt$ ls  
    apt.conf.d  auth.conf.d  listchanges.conf  listchanges.conf.d  preferences.d  sources.list  sources.list\~  sources.list.d  trusted.gpg  trusted.gpg~  trusted.gpg.d  
    pajazzo@derpface:/etc/apt$ cat sources.list |grep non-free  (en laita koko grep palautetta tähän, vain esimerkkirivin)  
    deb http://deb.debian.org/debian/ bullseye main contrib non-free  

    Ainakin NVidian ajureiden kanssa piti useampaan aptin lähteeseen lisätä vaihtoehdot contrib ja non-free jotta tarvittavat ajurit saadaan asennettua. En toki ole saanut kunnolla hommaa vielä pelaamaan (esim. ulkoiset näytöt eivät tällä hetkellä toimi). Koska tietokoneeni näytöohjainarkkitehtuuri on mallia [NVidia Optimus](https://wiki.debian.org/NVIDIA%20Optimus) ja sen kanssa säätäminen Linux puolella on aiemmin ollut tuskallista katselen tätä joskus paremmalla ajalla.  

5. /media/  
    * Ulkoiset mediat kuten jaetut kovalevyt, usb-tikut jne.
    * Itselläni tuolta löytyy yksi ositus HDD levystä, jota käytän jakona Windowsin ja Linuxin välillä. Pitää laittaa se auto-mounttaavaksi (/etc/fstab) jossain välissä vaikka aika vähän tuota tulee käytettyä.  
    * Tässä kuitenkin komennot joilla mounttaan sen tarvittaessa luku- ja kirjoitusoikeuksin.  
    pajazzo@derpface:/$ sudo mount -o rw /dev/sda3 /media/pajazzo/Shared  
    pajazzo@derpface:/$ cd media/pajazzo/  
    pajazzo@derpface:/media/pajazzo$ ls -l  
    drwxrwxrwx 1 root root 8192 Jan 24 21:06 Shared  

6. /var/log/  
    * Järjestelmän lokitiedostoja.  
    * Täältä voi löytää apua erinäisten ongelmatilanteiden selvittelyyn. Jos esimerkiksi Linuxin käynnistyksenvaiheessa tapahtuu jotain odottamatonta, löytyy sijainnista boot.log.#.tmp tiedostoja.  Tai jos esimerkiksi käyttöoikeuksien kanssa on ongelmaa löytyy auth.log tiedostoja.  
    * Tässä pieni testi. Kirjauduin sisään käyttäjänä watcher ja yritin päästä käsiksi käyttäjän pajazzo home -kansioon sudo käyttäjänä. Tämä epäonnistui ja sain ilmoituksen, että tapahtumasta kirjoitetaan raportti auth.logiin. Tässä auth logiin tallennettu rivi:  
        + pajazzo@derpface:/$ cd var/log  
        pajazzo@derpface:/var/log$ sudo ls |grep auth  
        auth.log  
        auth.log.1  
        pajazzo@derpface:/var/log$ sudo cat auth.log | grep watcher  (en laita tähän koko grepattua lokia vaan vain tuon kiinnostavan rivin)  
        `Jan 31 15:37:41 derpface sudo:  watcher : user NOT in sudoers ; TTY=pts/2 ; PWD=/home/pajazzo ; USER=root ; COMMAND=/usr/bin/touch test.txt`  
        Kuten nähdään, käyttäjä watcher yritti sudo oikeuksia käyttäen luoda test.txt tiedoston käyttäjän pajazzo kotihakemiston juureen. Toiminta estettiin puuttuvien oikeuksien takia ja asia raportoitiin lokiin.  


## b) My CLI. Keksi jokin asia, jota haluaisit tehdä komentokehotteessa. Etsi ja asenna komentokehotteen paketinhallinnasta ohjelmat, joilla asian voi ratkaista. Asenna ainakin kolme itsellesi uutta komentorivillä (command line interface, CLI) tai tekstitilassa (text user interface, TUI) toimivaa ohjelmaa. Näytä, miten kuvitteellista ongelmaa voi ratkoa näillä ohjelmilla. Voit valita jonkin helpon tai yksinkertaistetun esimerkin.  
  
#### Mahdollisuus monitoroida työympäristön käyttäjien toimintaa vaivattomasti. Esimerkiksi selvittää kuka meni poistamaan jonkin tärkeä tiedoston.  
[Acct](https://www.tecmint.com/how-to-monitor-user-activity-with-psacct-or-acct-tools/) vaikuttaisi käytännölliseltä työkalulta tähän.      

Seuraavaksi esimerkiksi kaikki rm komennot käyttäjältä watcher. Tästä ei saa tietoa, mitä on poistettu, mutta komento, ajankohta ja mitä terminaalia on käytetty selviää kyselystä. Ehkä tähän tarkoitukseen löytyisi kätevämpiäkin ratkaisuja.  

pajazzo@derpface:\~$ sudo apt-get install acct  
pajazzo@derpface:\~$ sudo lastcomm watcher | grep rm  
pool-gnome-term      X watcher  __         1.72 secs Mon Jan 31 17:41  
rm                     watcher  pts/2      0.00 secs Mon Jan 31 17:45  
rm                     watcher  pts/2      0.00 secs Mon Jan 31 17:45  
rm                     watcher  pts/2      0.00 secs Mon Jan 31 17:45  
rm                     watcher  pts/2      0.00 secs Mon Jan 31 17:45  
rm                     watcher  pts/2      0.00 secs Mon Jan 31 17:44  
rm                     watcher  pts/2      0.00 secs Mon Jan 31 17:44  
rm                     watcher  pts/2      0.00 secs Mon Jan 31 17:43  
rm                     watcher  __         0.00 secs Mon Jan 31 17:41  
rm                     watcher  pts/2      0.00 secs Mon Jan 31 17:31  
rm                     watcher  __         0.00 secs Mon Jan 31 17:30  
  
Sovelluksella pystyisi myös suorittamaan työajanseurantaa, koska komennolla `sa -d username` saa listauksen käyttäjän päivittäisestä kirjautuneena olosta.  
`pajazzo@derpface:~$ ac -d watcher`  
`Today	total        0.20`  
  
#### Haluan hallita Github repositorioitani komentoriviltä  
[git](https://docs.github.com/en/get-started/quickstart/set-up-git)  
  
git on komentorivillä toimiva sovellustyökalu, joka tulee asennettua aina uuteen Linux asennukseen, koska sen kautta pystyy ssh yhteydellä helposti luomaan, kloonamaan, päivittämään jne .omia Github repositorioitaan. Käyn tässä asennuksen ja konfiguraation läpi. Poistin ennen aloittamista koneeltani gitin, luodut salausavaimet, sekä ssh-agentille tallennetut tunnistetiedot.  
  
`pajazzo@derpface:~$ sudo apt-get install git`  
`pajazzo@derpface:~$ git config --global user.name pajaz`  
`pajazzo@derpface:~$ git config --global user.email omaemail@domain.fi/com/org`  
  
Siinä perus Git setuppi, mutta jatketaan vielä ja laitetaan SSH yhteys kuntoon. Tätä varten pitää luoda salausavainpari ja esimerkiksi [täältä](https://linuxkamarada.com/en/2019/07/14/using-git-with-ssh-keys/#.YfgvkvexVJc) löytyy erittäin hyvin selitetty ohje avainparin luomiseksi ja koko SSH yhteyden muodostamiseksi githubiin.  
  
`pajazzo@derpface:~$ ssh-keygen -t rsa -b 4096 -C "omaemail@domain.fi/com/org"` (Tässä luodaan rsa salausta käyttävä 4096 bittinen salausavain, jonka perään laitetaan kommentiksi -C oma sähköpostiosoite)     
`Generating public/private rsa key pair.`  
`Enter file in which to save the key (/home/pajazzo/.ssh/id_rsa): `    
`Created directory '/home/pajazzo/.ssh'.`  
`Enter passphrase (empty for no passphrase): `  
`Enter same passphrase again: `  (Kannattaa muistaa tämä tai pitää ainakin saatavilla. Jouduin tekemään tämän osion uusiksi jätettyäni salasanan toisella laitteella sijaitsevaan salasanamanageriin..)  
`Your identification has been saved in /home/pajazzo/.ssh/id_rsa`  
`Your public key has been saved in /home/pajazzo/.ssh/id_rsa.pub`  
  
Private ja public keyt luotu. Seuraavaksi asetetaan Githubiin juuri luotu public key.  
  
`pajazzo@derpface:~$ cat ~/.ssh/id_rsa.pub`  
Kopioi terminaaliin tulostuva sekava, omaan sähköpostiosoitteeseen päättyvä viesti ja liitä se oman Github profiilin asetuksista löytyvään [SSH and GPG Keys](https://github.com/settings/keys) valikon kohtaan SSH keys (New SSH key). Anna koneelle nimi ja klikkaa tallenna.  
  
Lisätään vielä ssh-agenttiin käytön helpottamiseksi luotu private key (salasanaa ei tarvitse jatkuvasti syötellä).  
  
`pajazzo@derpface:~$ ssh-add ~/.ssh/id_rsa`  
`Enter passphrase for /home/pajazzo/.ssh/id_rsa: ` (Aiemmin luotu salasana)  
`Identity added: /home/pajazzo/.ssh/id_rsa `  
  
Yhteyden testaus:  
`pajazzo@derpface:~$ ssh -T git@github.com`  
`The authenticity of host 'github.com (140.82.121.3)' can't be established.`  
`ECDSA key fingerprint is SHA256:p2QAMXNIC1TJYWeIOttrVc98/R1BUFWu3/LiyKgUfQM.`  
`Are you sure you want to continue connecting (yes/no/[fingerprint])? yes`  
`Warning: Permanently added 'github.com,140.82.121.3' (ECDSA) to the list of known hosts.`  
`Hi pajaz! You've successfully authenticated, but GitHub does not provide shell access.`  
  
Toimii. Seuraavaksi kloonaan repositorion githubista koneelleni, päivitän nämä ja edellisen tehtävän muistiinpanot oikeaan tiedostoon ja päivitän pushilla kyseiseen repositorioon. (laitan vain komennot ilman palautetta tähän. Paitsi, jos tulee virheitä)    
`pajazzo@derpface:~$ cd Projects/`  
`pajazzo@derpface:~/Projects$ git clone git@github.com:pajaz/Linux-Palvelimet-2022.git`  
`pajazzo@derpface:~/Projects/Linux-Palvelimet-2022$ git commit -a -m "Luento2.md acct ja git asennukset ok"`  
`pajazzo@derpface:~/Projects/Linux-Palvelimet-2022$ git push origin main`  
`pajazzo@derpface:~/Projects/Linux-Palvelimet-2022$ `  

Ei virheitä ja Githubin puolellakin muutamia kirjoitusvirheitä lukuunottamatta kaikki näyttää hyvältä.   

#### Muistiinpanojen hallinta komentokehotteen kautta
[taskwarrior](https://taskwarrior.org/)  
Basic commands can be found [here](https://taskwarrior.org/docs/commands/)  

Asennus:  
pajazzo@derpface:~$ sudo apt-get install taskwarrior  
  
Käyttö:  
pajazzo@derpface:~$ task version  
A configuration file could not be found in   
Would you like a sample /home/pajazzo/.taskrc created, so Taskwarrior can proceed? (yes/no) Yes  
task 2.5.3 built for Linux  
Copyright (C) 2006 - 2021 P. Beckingham, F. Hernandez.  

Taskwarrior may be copied only under the terms of the MIT license, which may be  
found in the Taskwarrior source kit.  
  
Documentation for Taskwarrior can be found using 'man task', 'man taskrc', 'man  
task-color', 'man task-sync' or at http://taskwarrior.org  
  
pajazzo@derpface:\~$ task add "Return Linux homework" due:2022-02-01T15:00  
Created task 1.  
pajazzo@derpface:\~$ task add "Go to work" due:2022-02-02T08:00  
Created task 2.  
pajazzo@derpface:\~$ task add "Buy milk"  
Created task 3.  
pajazzo@derpface:\~$ task list  
  
ID Age   Due        Description               Urg   
 1 36s   2022-02-01 Return Linux homework     8.77  
 2 12s   2022-02-02 Go to work                8.45  
 3  2s              Buy milk                     0  
  
3 tasks  
pajazzo@derpface:\~$ task 3  
No command specified - assuming 'information'.  
  
Name          Value                                 
ID            3                                     
Description   Buy milk  
Status        Pending                               
Entered       2022-02-01 13:26:49 (17s)  
Last modified 2022-02-01 13:26:49 (17s)             
Virtual tags  LATEST PENDING READY UNBLOCKED  
UUID          1bf1e273-42fa-4764-b1f7-60d3e2ff9f2d  
Urgency          0  
  
pajazzo@derpface:~$ task done 3  
Completed task 3 'Buy milk'.  
Completed 1 task.  
You have more urgent tasks.  
  
## c) Tukki. Aiheuta lokiin kaksi eri tapahtumaa: yksi esimerkki onnistuneesta ja yksi esimerkki epäonnistuneesta tai kielletystä toimenpiteestä. Analysoi rivit yksityiskohtaisesti.

Esimerkki epäonnistuneesta tapahtumasta ja lokirivin analyysi tulikin jo tehtyä tämä dokumentin /var/log/ esittelykohdassa.  
Käytetty komento oli seuraava:  
watcher@derpface:/$ sudo touch pajazzo/test.txt  

Ja lokin tutkinta:  
pajazzo@derpface:/$ cd var/log  
pajazzo@derpface:/var/log$ sudo ls | grep auth  
auth.log  
auth.log.1  
pajazzo@derpface:/var/log$ sudo cat auth.log | grep watcher  _(en laita tähän koko grepattua lokia vaan vain tuon kiinnostavan rivin)_  
Jan 31 15:37:41 derpface sudo:  watcher : user NOT in sudoers ; TTY=pts/2 ; PWD=/home/pajazzo ; USER=root ; COMMAND=/usr/bin/touch test.txt  

Kuten nähdään, käyttäjä watcher yritti ilmoitettuna ajankohtana derpface hostilla, sudo oikeuksia käyttäen luoda test.txt tiedoston touch sovellusta käyttäen (touch -sovelluksen tiedostosijainti /usr/bin/touch) käyttäjän pajazzo kotihakemiston juureen käyttäen terminaali istuntoa pts/2 (tämän voi aukiolevassa terminaalissa tarkistaa tty komennolla). Toiminta estettiin puuttuvien oikeuksien takia (user NOT in sudoers eli käyttäjältä puuttu superuser oikeudet) ja asia raportoitiin lokiin. USER kohtaa en oikein osaa analysoida, mutta veikkaan, että tuo on lokitiedon lisännyt käyttäjä, tässä tapauksessa root.  
  
  
Onnistunut tapahtuma(**Lisätty 2.2.2022 illalla**):  
Jan 29 13:33:45 derpface sudo:  pajazzo : TTY=pts/0 ; PWD=/home/pajazzo/DataSecurityCourse2022 ; USER=root ; COMMAND=/usr/bin/apt-get update  

Tässä siis taasen käyttäjä pajazzo ilmoitettuna ajankohtana derpface hostilla ja käyttäen pts/0 terminaali-istuntoa, on suorittanut root oikeuksilla apt-get update komennon eli päivittänyt paketinhallinnan tiedot uusimpaan. Käyttäjä on komennon aikaan ollut kansiossa /home/pajazzo/DataSecurityCourse2022, mutta se on tämän kannalta epäoleellinen tieto.  

## d) The Friendly M. Näytä 2-3 kuvaavaa esimerkkiä grep-komennon käytöstä. Ohjeita löytyy 'man grep' ja tietysti verkosta.

Itse käytän grep komentoa aika paljon, lähinnä siistiäkseni jonkin toisen komennon tulosteesta näkyville vain itseäni kiinnostavat rivit.  Esimerkki vaikkapa tämän dokumentin [Acct asennus kohdasta](https://github.com/pajaz/Linux-Palvelimet-2022/blob/main/Homework/Lesson02/Luento2.md#mahdollisuus-monitoroida-ty%C3%B6ymp%C3%A4rist%C3%B6n-k%C3%A4ytt%C3%A4jien-toimintaa-vaivattomasti-esimerkiksi-selvitt%C3%A4%C3%A4-kuka-meni-poistamaan-jonkin-t%C3%A4rke%C3%A4-tiedoston) jossa olen pipelinannut lastcomm:in palautteen näyttämään vain tiettyä komentoa koskevat tiedot.  

Laitan toiseksi esimerkiksi kuinka grepillä voi jättää tuloksista pois ehtoon asetetun rivin:  
Minulla on tiedosto text.txt kotihakemistossani. Tiedosto on täynnä numero rivejä, mutta seassa on joitain rivejä joissa on sanoja. Grepin avulla voidaan jättää tulostuksesta pois rivit jotka sisältävät numeroita.  
pajazzo@derpface:\~$ grep -c "" text.txt  
697 (Tiedosto sisältää 697 riviä. -c ilmoittaa rivimäärän joka täsmää ehtoon)  
pajazzo@derpface:\~$ grep -v "\[0-9\]" text.txt    
Tämä  
On  
Tiedosto  
  
Jonka  
Sanoma  
On  
Vaikeasti  
Luettavissa.  
  
(-v:llä käännetään ehto toisinpäin ja \[0-9\] pitää sisällään kaikki numerot)  
  
pajazzo@derpface:\~$ grep -v "\[0-9\]" text.txt | grep -iv vaikeasti   
Tämä  
On  
Tiedosto  
  
Jonka  
Sanoma  
On  
Luettavissa.  
  
(|-operaattorin avulla annetaan ensimmäisen grepin tuloste toisen grepin käsiteltäväksi ja -i kertoo komennolle, ettei sen tarvitse välittää isoista ja pienistä kirjaimista)  
  

## e) Pwnkit. Päivitä kaikki Linux-ohjelmat ja asenna tietoturvapäivitykset.
  
Suoritettu komennot:  
sudo apt-get update  
sudo apt-get upgrade 
sudo apt-get -y dist-upgrade  

Upgraded palauttivat, koska taisin tehdä tuon jo viime viikolla:  
`0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.`  


## y) cdlspwd! Opettele tärkeimmät komennot ulkoa ja harjoittele suurella määrällä kokeiluja. Opeteltavat komennot ovat artikkelissa Karvinen 2020: Command Line Basics Revisited (tätä y-alakohtaa ei tarvitse raportoida lainkaan)

## Bonus: Recursive. Pystytkö etsimään kaikki rivit, joilla lukee Tero isolla tai pienellä, kun tiedostoja on sisäkkäisissä kansioissa? (Eli tutkimaan jonkin kansion kaikkine alihakemistoineen)

**Tämä tehty 2.2.2022 illalla**

Loin tällaisen testikansio kokonaisuuden komennoilla:  
mkdir \[0...9\]
touch {0..9}/teksti.txt  
lisäsin sattumanvaraisesti tiedostoihin joko numeroita tai nimen Mikko tai mikko nanoa käyttäen ja vielä muutaman tiedoston manuaalisesti.  

pajazzo@derpface:\~/Projects$ cd test/  
pajazzo@derpface:\~/Projects/test$ pwd  
/home/pajazzo/Projects/test  
pajazzo@derpface:\~/Projects/test$ ls *  
teksti2.txt  teksti.txt  
0:  
teksti.txt  
  
1:  
teksti.txt  
  
2:  
teksti.txt  
  
3:  
teksti.txt  
  
4:  
teksti.txt  
  
5:  
teksti.txt  
  
6:  
teksti.txt  
  
7:  
teksti.txt  
  
8:  
teksti.txt  
  
9:  
teksti.txt  
  
* Listasin kaikki tiedostot testi ja sen alikansioissa.  

pajazzo@derpface:~/Projects/test$ find -type f -exec  cat {} \;  
Mikko  
Mikko  
Mikko   
mikko  
mikko  
Mikko  
32412421421    
124124214   
Mikko124124214  
  
* find eli etsi, kaikki tiedostot tyyppiä f eli file ja aja kaikille tuloksille komento cat parametrilla {}. {} kohdalle sijoitetaan findin tulos. exec vaatii vielä loppuun argumentin \; [toimiakseen](https://www.baeldung.com/linux/find-exec-command).  

pajazzo@derpface:~/Projects/test$ find -type f -exec cat {} \; | grep -i mikko  
Mikko  
Mikko  
Mikko  
mikko  
mikko  
Mikko  
Mikko124124214  

* Koska aiempi tulos piti sisällään kaikkien tiedostojen sisällön, pipelinetin tuloksen vielä grepille -i optiolla, joka jättää isot ja pienet kirjaimet huomiotta.  



##   g) Sshecrets. Vaikeampi vapaaehtoinen bonuskohta, ei ole opetettu vielä: Asenna SSH-demoni. Kokeile omalla ssh-palvelimellasi jotain seuraavista: ssh-copy-id, sshfs, scp tai git. (Helpoin lienee scp: ‘scp foo.txt tero@example.com:’)
