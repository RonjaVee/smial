### Tiivistelmä

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

### Virtuaalipalvelimen vuokraus

Virtuaalipalvelimen vuokraamisen tilanne on tällä hetkellä tämä: 

![image](https://github.com/RonjaVee/smial/assets/148786247/f447cace-1059-4160-8304-c36df981deaf)

![Screenshot_20240212_210414_Outlook](https://github.com/RonjaVee/smial/assets/148786247/74f1d83e-1673-484f-b6b2-c89a48a09fb9)

Pääsy on evätty taikka odottaa vastausta kaikkiin palveluihin joita kokeilin käyttää.
