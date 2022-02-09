h4

Vinkki: muista merkitä, mikä kohta raportissasi vastaa mihinkin alakohtaan a,
b, c...

a) Vuokraa oma julkinen palvelin Internetiin. Vinkkejä: Perustele tehdyt
valinnat. Voit saada myös ilmaiseksi Github Education -paketilla. Jos sinulla
on aiempi palvelin, tee uusi alusta lähtien ja raportoi samalla. Käytä aina
hyviä salasanoja.

ax) Vaihtoehtotehtävä, korvaa kohdan a. Suosittelen mieluummin tekemään
a-kohdan, se on paljon hyödyllisempi. Kokeile virtuaalikoneiden tekoa
vagrant:lla omalla paikallisella koneellasi. Sovella muut kohdat (b, c...)
siten, että ne toimivat paikallisen koneen kanssa: esim testaa weppsivut
paikallisesti curlilla, simuloi hyökkäys syöttämällä väärä salasana omaan
ssh-palvelimeesi jne.

b) Suojaa palvelin tulimuurilla. Muista ensin reikä ssh-palvelimelle.

c) Laita koneellesi Apache-weppipalvelin. Korvaa testisivu. Laita käyttäjän
kotisivut toimimaan. Kokeile eri koneelta, esim. kännykällä, että sivut
toimivat. Vinkki: tee kotisivut normaalina käyttäjänä public_html/ alle,
opettelemme "name based virtual hosting" myöhemmin.

d) Etsi lokeistasi merkkejä murtautumisyrityksistä ja analysoi ne. Vinkki:
auth.log.

c) Vapaaehtoinen: Laita TLS-salakirjoitus (https) toimimaan Let's Encrypt
avulla. Vinkki: certbot tai lego.

e) Vapaaehtoinen: Tee weppisivuja omalla, paikallisella koneellasi ja kopioi ne
palvelimmelle scp-komennolla.

x) Vaikea, vapaaehtoinen vaihtoehtotehtävä Tämä on vain niille parille
propellihatulle, jotka halusivat vaikeamman tehtävän. Korvaa muut h4 koti- ja
tuntitehtävät. Koodaa ja julkaise uusi tietokantaa hyödyntävä weppipalvelu.
Palvelun pitää ratkaista jokin käytännön ongelma, esimerkiksi ilmoittautuminen
tapahtumaan, pisteytä tunti, äänestä suosikkia tms. Voit hyödyntää vanhoja
koodejasi, kunhan lopputulos on uusi. Voit käyttää mitä vain kehitysalustaa
(framework), esimerkiksi LAMP, Flask, Django, Postgre, Mariadb... Muista lisätä
raporttiin ruutukaappaukset keskeisestä toiminnallisuudesta.

h5
