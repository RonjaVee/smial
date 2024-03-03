## Tiivistelmä

Tiivistelmä seuraavista ohjeista:
 Lehto, Susanna. Teoriasta käytäntöön pilvipalvelimen avulla (h4). 14.2.2022 [https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/](https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/)
Karvinen, Tero. First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS. 19.9.2017.[https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/?fromSearch=first%20steps%20on](https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/?fromSearch=first%20steps%20on)

- Ensin vuokrataan virtuaalipalvelin joltakin palveluntarjoajalta: valitaan halpa (tai GitHub educationin ilmainen) paketti
- Käyttöjärjestelmäksi valitaan tässä tehtävässä Debian
- Datakeskuksen sijainti kannattaa valita Euroopan sisältä tässä tehtävässä
- Vuokratun virtuaalipalvelimen salasanan on oltava ehdottomasti hyvä, sillä  palvelimelle voidaan helposti murtautua muuten
- Domainnimen saa vuokrattua esimerkiksi Namecheapiltä (eli millä nimellä verkkosivu maailmalle)
- Namecheapista vuokrattu domainnimi laitetaan osoittamaan oman palvelimen IP-osoitetta
- Vuokratun virtuaalipalvelimen päivitykset haetaan ja se suojataan palomuurilla asentamalla UFW
- Sallitaan SSH-yhteydet sekä HTTP-liikenne
- Tehdään virtuaalipalvelimelle uusi käyttäjä (sillekin vahva salasana)
- Asennetaan Apache kuten aiemmin ja Apachen testisivu korvataan omalla sivulla
- Palvelimen ohjelmat päivitetään:
  
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get dist-upgrade

## Virtuaalipalvelimen vuokraus

### Kotikoneeni tiedot:

AMD Ryzen 5 3600 6-Core Processor 3.59 GHz

RAM: 16,0 Gt

64-bittinen käyttöjärjestelmä, x64-suoritin

Windows 10 Pro, versio 22H2


Virtuaalipalvelimen vuokraamisen tilanne oli aikaisemmin tämä: 

![image](https://github.com/RonjaVee/smial/assets/148786247/f447cace-1059-4160-8304-c36df981deaf)

![image](https://github.com/RonjaVee/smial/assets/148786247/719c8fbe-c90e-48db-bf9e-0e4e98e259f7)



Pääsy oli evätty taikka odotti vastausta kaikkiin palveluihin joita kokeilin käyttää (DigitalOcean, Linode, GitHub education). Katselin muitakin vaihtoehtoja, mutta hinnat olivat aika suolaisia niissä mitkä
vaikutti muutoin luotettavilta.
12.2.2024 klo. 22:18.

Pääsin vihdoin hyödyntämään DigitalOceania GitHub educationin kautta. GitHubin kautta DigitalOceaniin sai 200 dollarin edestä krediittejä, niin dropletin ylläpitäminen on nyt jonkin aikaa ilmaista.

![image](https://github.com/RonjaVee/smial/assets/148786247/dc75cfc1-c8d4-4ba5-99c7-bcb15981ca08)

![image](https://github.com/RonjaVee/smial/assets/148786247/54867115-8fc0-4d11-9437-9c727db529d6)

![image](https://github.com/RonjaVee/smial/assets/148786247/ae2c1f65-59b4-4700-81d0-28a3d2db2259)

![image](https://github.com/RonjaVee/smial/assets/148786247/af2c9add-e84b-429b-adea-b836f044aee7)

![image](https://github.com/RonjaVee/smial/assets/148786247/155451a4-b996-4055-b3c6-11e12b7e3903)

![image](https://github.com/RonjaVee/smial/assets/148786247/f71b0f5a-52a0-4878-9181-7203e4820d75)

![image](https://github.com/RonjaVee/smial/assets/148786247/ef702445-c09d-44c5-a542-fbe6bd5a4639)











