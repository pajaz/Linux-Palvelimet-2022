# Luento 6 Kotitehtävät
  
Osa kurssia Linux Palvelimet ICT4TN021-3018 Haaga-Helia Ammattikorkeakoulussa  
Kurssin vetäjä: [Tero Karvinen](https://terokarvinen.com/2021/linux-palvelimet-ict4tn021-3018/)  

## a) Kaikki tehtävät arvioitavaksi. Palauta linkit kaikkiin kotitehtäväraportteihisi. Arviointi tehdään ensisijaisesti tästä linkistä. (tässä alakohdassa ei tarvitse tehdä testejä koneella)


## b) Tarkista, että olet viitannut jokaisessa tehtävässä kaikkiin lähteisiin. Esimerkiksi kurssiin, tehtävänantoihin, käyttämiisi toisten kotitehtävärapotteihin, manuaalisivuihin, kotisivuihin... (tässä alakohdassa ei tarvitse tehdä testejä koneella.


## c) Uusi komento Linuxiin. Tee uusi komento, joka tulostaa käyttäjälle hyödyllistä tietoa. Kokeile, että komento toimii kaikista hakemistoista ja muillakin käyttäjillä kuin omallasi.
  
Tein kurssin aikana aika monimutkaisen Bash -skriptin, jonka avulla voin hakea käymieni kurssien sivuilta haluamaani tiedostoon, haluamani viikon/viikkojen tehtävät, joutumatta käyttämään selainta. Skriptin toiminta selostettuna vaiheittain: 

Komento: fhwk -s h1 -e h2 -u https://terokarvinen.com/2021/linux-palvelimet-ict4tn021-3018/ -f Viikko1.md

1. w3m -dump $url > tempholder.txt  
  * Komento hakee pyydetyn verkkosivun sisällön väliaikaiseen tiedostoon.  
2. echo "Fetching site: ${url}"  
echo "Output file: ${file_location}"  
  * Tulostetaan, mitä tehdään.  
3. line1=$(grep -n $start tempholder.txt | head -1 | cut -d : -f 1)
  line2=$(grep -n $end tempholder.txt | head -1 | cut -d : -f 1)
  if [ -z $line1 ]
  then
  	echo "${start} not present in page. Exiting"
  elif [ -z $line2 ]
  then
  	echo "${end} not present in page. Exiting"
  else 
	  echo sed -n $line1','$line2'p;' tempholder.txt > file.txt
	  sed -n $line1','$line2'p;' tempholder.txt > $file_location
	  echo "Starting from line containing '${start}' to the line containing '${end}'"
  fi


## d) Parametreja. Tee skripti, joka ottaa komentoriviparametreja. Esim. 'greetuser Tero' joka tulostaa "moi" ja parametrinä olevan nimen, esim "moi Tero".


## e) Ratkaise valitsemasi vanha arvioitava laboratorioharjoitus tältä kurssilta. (Löytyy DuckDuckGolla, Googlella, linkeistä tältä sivulta tai hakemalla yläreunan hakutoiminnolla). Sovella tarvittaessa tehtäviä tähän toteutukseen sopivaksi, esimerkiksi PHP:n tilalta voi tehdä vastaavan Pythonilla; Flaskin tilalta käyttää Djangoa. Tai jättää pois jonkin epärelevantin kohdan.

Installation process is explained [Here](Homework/Lesson01/Luento1.md) in section A.  
System: Debian 11 Bullseye non-free  
RAM: 2gb  
Disk size: 15Gb  
  






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
