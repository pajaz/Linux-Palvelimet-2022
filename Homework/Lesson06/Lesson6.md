# Luento 6 Kotitehtävät
  
Osa kurssia Linux Palvelimet ICT4TN021-3018 Haaga-Helia Ammattikorkeakoulussa  
Kurssin vetäjä: [Tero Karvinen](https://terokarvinen.com/2021/linux-palvelimet-ict4tn021-3018/)  

## a) Kaikki tehtävät arvioitavaksi. Palauta linkit kaikkiin kotitehtäväraportteihisi. Arviointi tehdään ensisijaisesti tästä linkistä. (tässä alakohdassa ei tarvitse tehdä testejä koneella)
Done.  

## b) Tarkista, että olet viitannut jokaisessa tehtävässä kaikkiin lähteisiin. Esimerkiksi kurssiin, tehtävänantoihin, käyttämiisi toisten kotitehtävärapotteihin, manuaalisivuihin, kotisivuihin... (tässä alakohdassa ei tarvitse tehdä testejä koneella.
Done.  

## c) Uusi komento Linuxiin. Tee uusi komento, joka tulostaa käyttäjälle hyödyllistä tietoa. Kokeile, että komento toimii kaikista hakemistoista ja muillakin käyttäjillä kuin omallasi.  
## d) Parametreja. Tee skripti, joka ottaa komentoriviparametreja. Esim. 'greetuser Tero' joka tulostaa "moi" ja parametrinä olevan nimen, esim "moi Tero".  
  
Tein kurssin aikana aika monimutkaisen Bash -skriptin, jonka avulla voin hakea käymieni kurssien sivuilta haluamaani tiedostoon, haluamani viikon/viikkojen tehtävät, joutumatta käyttämään selainta.  
Esimerkkikomento:  
fhwk -s h1 -e h2 -u https://terokarvinen.com/2021/linux-palvelimet-ict4tn021-3018/ -f Viikko1.md  
  
Selitykset:  
-s = start  
-e = end  
-u = url (minulla on valmiit lyhenteet käymilleni kursseille, joten koko URL pätkää en tarvitse)  
-f = tiedostopolku, johon tieto kirjoitetaan.  
  
Tuloste:  
Fetching site: https://terokarvinen.com/2021/linux-palvelimet-ict4tn021-3018/  
Output file: Viikko1.md  
Starting from line containing 'h1' to the line containing 'h2'  
  
Skripti käyttää sovelluksia:  
w3m, sivun hakeminen dump tiedostoon, joka poistetaan lopuks    
grep, head ja cut pipeline, jotta dump -tiedostosta saadaan haettavat rivinumerot.  
sed joka rivinumeroiden avulla trimmaa halutut rivit haluttuun tiedostoon.  
  
* Määritettyjä handleja url:aa lukuunottamatta ei ole pakko käyttää ja käyttäjä voi määrittää vain alun tai lopun, tai ei kumpaakaan.  
* Skripti hakee vain haetun termin ensimmäisen esiintymisen.  
* Vaatii toimiakseen staattisen sivun.  
  
Komennon määritys kaikille käyttäjille (tiedosto on jo tässä vaiheessa luotuna):  
pajazzo@derpface:\~/.myscripts$ ls -l  
total 4  
-rw-r--r-- 1 pajazzo pajazzo 1924 Mar 14 12:49 fhwk  
pajazzo@derpface:\~/.myscripts$ chmod 755 fhwk   
pajazzo@derpface:\~/.myscripts$ ls -l  
total 4  
-rwxr-xr-x 1 pajazzo pajazzo 1924 Mar 14 12:49 fhwk  
pajazzo@derpface:\~/.myscripts$ ls -l /usr/local/bin/ | grep fhwk  
-rwxr-xr-x 1 pajazzo pajazzo 1924 Mar 14 12:49 fhwk  
pajazzo@derpface:\~/.myscripts$ fhwk  
Fetching site: https://terokarvinen.com/2021/data-security-2022p3-ict4tf022-3008/  
Output file: fhwkDefault.md  
  
Testasin toimintaa myös toisella käyttäjällä ja tämä näyttäisi toimivan.  
  
## e) Ratkaise valitsemasi vanha arvioitava laboratorioharjoitus tältä kurssilta. (Löytyy DuckDuckGolla, Googlella, linkeistä tältä sivulta tai hakemalla yläreunan hakutoiminnolla). Sovella tarvittaessa tehtäviä tähän toteutukseen sopivaksi, esimerkiksi PHP:n tilalta voi tehdä vastaavan Pythonilla; Flaskin tilalta käyttää Djangoa. Tai jättää pois jonkin epärelevantin kohdan.

Installation process is explained [Here](Homework/Lesson01/Luento1.md) in section A.  
System: Debian 11 Bullseye non-free  
RAM: 2gb  
Disk size: 15Gb  

## Tehtävä 2021 kevään kurssilta
  
Tervetuloa Leili Oy:n tietohallintojohtajaksi!  
  
Onnea! Olet nyt Leili Oy:n tietohallintojohtaja (ja -osasto). Oma käyttäjä  
  
#### Tee järjestelmään oma käyttäjä, jolla on tiedoissa oma nimesi. Laita tälle käyttäjälle ylläpito-oikeudet (sudo).  
  
mp@2021lab:\~$ sudo adduser pajunmi  
[sudo] password for mp:   
Adding user `pajunmi' ...  
Adding new group `pajunmi' (1001) ...  
Adding new user `pajunmi' (1001) with group `pajunmi' ...  
Creating home directory `/home/pajunmi' ...  
Copying files from `/etc/skel' ...  
New password:   
Retype new password:   
passwd: password updated successfully  
Changing the user information for pajunmi  
Enter the new value, or press ENTER for the default  
	Full Name []: Mikko Pajunen  
	Room Number []:  
	Work Phone []:  
	Home Phone []:   
	Other []:   
Is the information correct? [Y/n] Y  
mp@2021lab:\~$ sudo adduser pajunmi sudo  
Adding user `pajunmi' to group `sudo' ...  
Adding user pajunmi to group sudo  
Done.  
  
#### Laita tämän käyttäjäsi kotihakemistoon dokumentti 'lab.txt'. Laita tiedoston alkuun oma nimesi ja linkki kotitehtäväpakettiisi. 
  
mp@2021lab:\~$ sudo nano /home/pajunmi/lab.txt  
mp@2021lab:\~$ cat /home/pajunmi/lab.txt  
Mikko Pajunen  
https://github.com/pajaz/Linux-Palvelimet-2022  
  
Palvelut:   
  
#### Laita tähän tiedot kaikista palveluista ja testit, joilla olet tarkistanut niiden toimivuuden. Laita tiedostoon myös kaikki salasanat.  
  


  
#### Suojaa tiedosto niin, että ulkopuoliset käyttäjät eivät pysty lukemaan sitä.   Tiedoston nimen tulee olla oikein, eli se tulee löytyä 'ls /home/*/lab.txt'.  
  
mp@2021lab:\~$ sudo chmod go-r /home/pajunmi/lab.txt   
mp@2021lab:\~$ ls -la /home/pajunmi/lab.txt   
-rw------- 1 root root 74 14. 3. 14:22 /home/pajunmi/lab.txt  
  
### Turvallisesti etänä  
  
Aiot kuulemma siirtyä etätöihin Hawajille. Valmistaudu ylläpitämään konetta ssh:lla. (Testaa paikallisesti, että SSH toimii). 
  
Aloitin asentamalla ja kytkemällä päälle palomuurin:  
sudo apt-get install ufw  
sudo ufw enable  
sudo reboot -i  
pajunmi@2021lab:\~$ systemctl status ufw  
Active: active (exited) since Mon 2022-03-14 14:35:00 EET; 1min 14s ago  
  
Asensin ssh:n ja avataan portti ssh-yhteydelle:  
sudo apt-get install ssh  
sudo ufw allow 22/tcp  
pajunmi@2021lab:\~$ sudo ufw allow 22/tcp  
[sudo] password for pajunmi:   
Rule added  
Rule added (v6)  
  
Testasin ssh-yhteyden toimintaa paikallisesti:  
pajunmi@2021lab:~$ ssh localhost  
The authenticity of host 'localhost (::1)' can't be established.  
ECDSA key fingerprint is SHA256:yMy5sW4k4q3lViiDXJE/bWckVbHL6wMdFAWL7s1o5Yg.  
Are you sure you want to continue connecting (yes/no/\[fingerprint])? yes  
Warning: Permanently added 'localhost' (ECDSA) to the list of known hosts.  
pajunmi@localhost's password:   
Linux 2021lab 5.10.0-10-amd64 \#1 SMP Debian 5.10.84-1 (2021-12-08) x86_64  
  
The programs included with the Debian GNU/Linux system are free software;  
the exact distribution terms for each program are described in the  
individual files in /usr/share/doc/*/copyright.  

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent  
permitted by applicable law.  
Last login: Wed Mar 14 14:40:23 2022 from 10.0.2.15  
  
Toimii.  
  
#### Suojaa kone tulimuurilla.  
  
Tehty edellisesssä.    
   
### Arvostetut asiantuntijamme  
  
Työntekijämme ovat  
  
    Ossi Otsomaja  
    Arnold Sjöbrengrörez  
    Einari Vähäkäähkö  
    Erkki Esimerkki  
    Maija Mallihenkilö  

Luodaan asiantuntijaryhmä ja käyttäjätunnukset asiantuntijoille:  
sudo groupadd specialist  
sudo adduser --ingroup specialist otsomos   
sudo adduser --ingroup specialist sjobrar  
sudo adduser --ingroup specialist vahakei  
sudo adduser --ingroup specialist esimeer  
sudo adduser --ingroup specialist mallima  
  
pajunmi@2021lab:\~$ groups otsomos sjobrar vahakei esimeer mallima  
otsomos : specialist  
sjobrar : specialist  
vahakei : specialist  
esimeer : specialist  
mallima : specialist  
   
Salasana kaikille on march22. Vanhennetaan ne ja asetaan salasanoille 90 päivän vanheneminen:   
pajunmi@2021lab:\~$ sudo passwd --expire otsomos  
passwd: password expiry information changed.  
pajunmi@2021lab:\~$ sudo passwd --expire sjobrar  
passwd: password expiry information changed.  
pajunmi@2021lab:\~$ sudo passwd --expire vahakei  
passwd: password expiry information changed. 
pajunmi@2021lab:\~$ sudo passwd --expire esimeer  
passwd: password expiry information changed.  
pajunmi@2021lab:\~$ sudo passwd --expire mallima  
passwd: password expiry information changed.  
  
pajunmi@2021lab:\~$ sudo nano /etc/login.defs  
pajunmi@2021lab:\~$ sudo cat /etc/login.defs | grep PASS_MAX_DAYS  
\#	PASS_MAX_DAYS	Maximum number of days a password may be used.  
PASS_MAX_DAYS	90  

#### Listaa käyttäjätunnukset ja salasanat aiemmin tekemääsi lab.txt tiedostoon.  
Done.  
  
### Mikä verkko, mikä meininki?  
  
#### Tee meille uusi komento 'netsee', joka kertoo verkon tilasta. Haluamme nähdä ainakin reititystaulun ja oman IP-osoitteen. Voit lisätä halutessasi jonkin ekstratiedon.  
  
Komennon tulee toimia kaikilla käyttäjillä.  

### Referenssilista  
  
Laitamme asiakaslistan nettiin. Menestystarinoita virtaa kuin vettä Keravanjoesta, joten tarvitsemme taustalle tehokkaan tietokannan.  
  
Haluamme tietokannan referenssiasiakkaistamme näkyviin palvelimen etusivulle weppisivuna (osoiteeseen http://localhost). Tietokannassa tulee olla seuraavat kentät  
  
    Asiakkaan nimi  
    Liikevaihto (miljoonaa euroa)  
    Työntekijöitä  
  
#### Keksi listaan itse esimerkkiasiakkaita.    

### Kuormaa  
  
Odotamme enintään 100 yhtäaikaista (samalla sekunnilla) asiakasta. Testaa, kestääkö palvelu tämän kuorman.  
  
Testit saa tehdä ainostaan "localhost"-osoitteella ja omalla paikallisella koneella. Kuormitustestausta ei saa tehdä kenenkään toisen palvelimelle tai hostaamalle palvelimelle.  
  
Voit käyttää työkalua "ab".  
  
====== Huvitusta guruille ===========  
  
Tästä alaspäin tehtävät edellyttävät enemmän soveltamista, eli kannattaa tehdä nuo helpoimmat ensin.  
Kaksi nimeä, yksi IP  
  
Laita aiemmin tehty referenssilista asiakkaista näkyviin osoitteesta "leili.example.com" ja laita toinen weppisivu osoitteeseen "hello.leili.  example.com". Voit simuloida nimipalvelun toimintaa hosts-tiedoston avulla.  
Haasteita: Muokattava osoitekirja  
  
Tee weppiin osoitekirja, jota voi muokata. Laita se osoitteeseen "crm.leili.example.com".  

## f) Tee uusi tyhjä virtuaalikone (tai oikea kone) viimeisen kerran arvioitavaa labraa varten. Koneella ei saa olla luottamuksellisia tietoja Kannattaa tehdä koneelle tarpeeksi iso virtuaalinen levy ja laittaa riittävästi RAM:ia. Guest additions saa olla asennettuna. Koneella ei saa olla muita asetuksia ennakkoon, eikä ylimääräisiä asennettuja ohjelmia.


## g) (vapaaehtoinen) Käytä Linuxia kurssin ulkopuolella.


## h) (vapaaehtoinen) Varaa kalenteristasi viikon välein aikoja Linux-harjoitteluun kurssin jälkeen.

Vinkkejä:

* Tapaamme seuraavan kerran w11 keskiviikkona kello 15:00 tutulla Jitsi-kanavalla. Silloin on arvioitava laboratorioharjoitus, ja on tärkeää ja pakollista olla etänä mukana. Ensi viikolla w10 ei ole online-tuntia.
* Arvioitava laboratorioharjoitus on yksilötehtävä. Varaa keskeytyksetöntä ja häiriötöntä aikaa tehtävän ajaksi.
* Hyödyllisiä ja hauskoja tietoja saa esim: uname -a; date --iso=min; cat / etc/lsb-release; uptime; w; whoami; last; hostname -I; df -h /home/
* Parametrit ovat skriptissä automaattisesti muuttujissa $1, $2, $3... Tai kaikki $* (ja hienommin "$@")
* Muista ilmoittautua
  - Palvelinten hallinta. Suositeltava jatkokurssi. Tosin tänne taitaa suuri osa ollakin jo ilmoittautunut. Opit, miten tämän kurssin taidot laajenevat kymmenien, satojen tai tuhansien koneiden hallintaan. Viime toteutuksen palaute 5.0/5, eli jokainen palaute oli paras mahdollinen 5.
  - Python weppikurssi w21-w22, ilmoittautuminen 2022-03-14 w11 maanantaina 08:00. Palaute 4.9/5.
  - Tunkeutumistestaus, jos täytät ennakkovaatimukset ja hakkerointi / kyberturvallisuus kiinnostaa. Palaute 4.9/5. Tervetuloa!
