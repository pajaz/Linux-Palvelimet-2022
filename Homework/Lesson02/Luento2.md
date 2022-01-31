# Luento 2 Kotitehtävät

## CLI

## z) Lue ja tiivistä. Tiivistelmäksi riittää muutama ranskalainen viiva per artikkeli. (Tässä z-alakohdassa ei tarvitse tehdä testejä tietokoneella)
  
* Karvinen 2020: [Command Line Basics Revisited](https://terokarvinen.com/2020/command-line-basics-revisited/)  
* YCombinator Hacker News, [vapaavalintainen artikkeli kommentteineen Linuxin komentokehotteesta](https://hn.algolia.com/?dateEnd=1643270199&dateRange=custom&dateStart=1547942400&page=0&prefix=false&query=command%20line&sort=byPopularity&type=story) (Kommentit aukeavat siitä pienestä "420 comments" linkistä Riittää, kun silmäilet artikkelin ja kommentit soveltuvin osin, osa voi olla kirjan mittaisia etkä ehdi tässä lukea niitä kokonaan. Samoin tiivistelmäksi riittää muutama bulletti, ei tarvitse kattaa koko sisältöä)  
  
## a) FHS. Esittele kansiot, jotka on listattu "Command Line Basics Revisited" kappaleessa "Important directories". Näytä kuvaava esimerkki kunkin tärkeän kansion sisältämästä tiedostosta tai kansiosta. Jos kyseessä on tiedosto, näytä siitä kuvaava esimerkkirivi. Työskentele komentokehotteessa ja näytä komennot, joilla etsit esimerkit.

1. / eli root  
    * Koko Linuxin tiedostojärjestelmän ylin hakemisto eli juuri ja pitää siis sisällään kaikki muut tärkeät ja vähemmän tärkeät kansiot.  
    <span style="color:#d3d3d3">
    pajazzo@derpface:/$ cd /  
    pajazzo@derpface:/$ pwd  
    /  
    pajazzo@derpface:/$ ls  
    bin  boot  dev  etc  home  initrd.img  initrd.img.old  lib  lib32  lib64  libx32  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr var  vmlinuz  vmlinuz.old  
    </span>
    * Operoiminen kansiossa vaatii superuser oikeudet. Esimerkki:  
    pajazzo@derpface:/$ touch test.txt  
    touch: cannot touch 'test.txt': Permission denied (Oikeudet kansion luontiin eivät riitä)  
    pajazzo@derpface:/$ ls -p | grep test  (Huomataan, ettei tiedostoa tosiaan luotu)  
    pajazzo@derpface:$ sudo touch test.txt (Uusi yritys superuserina)  
    pajazzo@derpface:/$ ls -p | grep test   
    test.txt (Tiedosto luotu onnistuneesti)  

2. /home/  
    * Pitää sisällään käyttäjien kotihakemistot, eli jokaisen käyttäjän henkilökohtaisen kansiot/tiedostot.  
    pajazzo@derpface:/home$ cd /home/
    pajazzo@derpface:/home$ pwd
    /home
    pajazzo@derpface:/home$ ls
    lost+found  pajazzo
    pajazzo@derpface:/home$       








## b) My CLI. Keksi jokin asia, jota haluaisit tehdä komentokehotteessa. Etsi ja asenna komentokehotteen paketinhallinnasta ohjelmat, joilla asian voi ratkaista. Asenna ainakin kolme itsellesi uutta komentorivillä (command line interface, CLI) tai tekstitilassa (text user interface, TUI) toimivaa ohjelmaa. Näytä, miten kuvitteellista ongelmaa voi ratkoa näillä ohjelmilla. Voit valita jonkin helpon tai yksinkertaistetun esimerkin.

## c) Tukki. Aiheuta lokiin kaksi eri tapahtumaa: yksi esimerkki onnistuneesta ja yksi esimerkki epäonnistuneesta tai kielletystä toimenpiteestä. Analysoi rivit yksityiskohtaisesti.

## d) The Friendly M. Näytä 2-3 kuvaavaa esimerkkiä grep-komennon käytöstä. Ohjeita löytyy 'man grep' ja tietysti verkosta.

## e) Pwnkit. Päivitä kaikki Linux-ohjelmat ja asenna tietoturvapäivitykset.

## y) cdlspwd! Opettele tärkeimmät komennot ulkoa ja harjoittele suurella määrällä kokeiluja. Opeteltavat komennot ovat artikkelissa Karvinen 2020: Command Line Basics Revisited (tätä y-alakohtaa ei tarvitse raportoida lainkaan)

## Bonus: Recursive. Pystytkö etsimään kaikki rivit, joilla lukee Tero isolla tai pienellä, kun tiedostoja on sisäkkäisissä kansioissa? (Eli tutkimaan jonkin kansion kaikkine alihakemistoineen)

# g) Sshecrets. Vaikeampi vapaaehtoinen bonuskohta, ei ole opetettu vielä: Asenna SSH-demoni. Kokeile omalla ssh-palvelimellasi jotain seuraavista: ssh-copy-id, sshfs, scp tai git. (Helpoin lienee scp: ‘scp foo.txt tero@example.com:’)
