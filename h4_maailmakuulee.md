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

##

Virtuaalipalvelimen vuokraamisen tilanne oli aikaisemmin tämä: 

![image](https://github.com/RonjaVee/smial/assets/148786247/f447cace-1059-4160-8304-c36df981deaf)



Pääsy oli evätty taikka odotti vastausta kaikkiin palveluihin joita kokeilin käyttää (DigitalOcean, Linode, GitHub education). Katselin muitakin vaihtoehtoja, mutta hinnat olivat aika suolaisia niissä mitkä
vaikutti muutoin luotettavilta.
12.2.2024 klo. 22:18.

Pääsin vihdoin hyödyntämään DigitalOceania GitHub educationin kautta. GitHubin kautta DigitalOceaniin sai 200 dollarin edestä krediittejä, niin dropletin ylläpitäminen on nyt jonkin aikaa ilmaista. Namecheapin kanssa tuli 
ongelmia, kun varmistussähköpostia ei kuulunut.

Lähdin DigitalOceanissa luomaan droplettia kohdasta deploy a virtual machine.

![image](https://github.com/RonjaVee/smial/assets/148786247/dc75cfc1-c8d4-4ba5-99c7-bcb15981ca08)

Datakeskukseksi valitsin alankomaalaisen vaihtoehdon, sillä se on maantieteellisesti lähellä.

![image](https://github.com/RonjaVee/smial/assets/148786247/54867115-8fc0-4d11-9437-9c727db529d6)

Seuraavaksi loin virtuaalikoneen, jossa käyttöjärjestelmä on Debian, ja se toimii jaetulla CPU:lla (se on halvin vaihtoehto ja tässä riittävä). Hinnaksi muodostui näillä valinnoilla 6 dollaria kuussa.
Ensimmäisen projektini ip-osoitteeksi sain 178.62.242.141.

![image](https://github.com/RonjaVee/smial/assets/148786247/af2c9add-e84b-429b-adea-b836f044aee7)

![image](https://github.com/RonjaVee/smial/assets/148786247/155451a4-b996-4055-b3c6-11e12b7e3903)

![image](https://github.com/RonjaVee/smial/assets/148786247/f71b0f5a-52a0-4878-9181-7203e4820d75)

Sitten otin virtuaalikoneellani yhteyttä DigitalOceanissa luotuun virtuaalikoneeseen, jota varten minun täytyi asentaa ensin openssh.

![image](https://github.com/RonjaVee/smial/assets/148786247/93ee6e84-793a-4726-aa16-60e30390a04a)

![image](https://github.com/RonjaVee/smial/assets/148786247/8ff1f716-812d-4005-8d3e-530ec41f3ea4)

Sitten asensin palomuurin Tero Karvisen ohjeen mukaisesti ja tein siihen reiän.

![image](https://github.com/RonjaVee/smial/assets/148786247/e2efd9d1-1e45-41ee-9619-1303008513ee)

Loin sitten koneelle käyttäjän josta tein pääkäyttäjän. Ajoin myös päivitykset.

![image](https://github.com/RonjaVee/smial/assets/148786247/041e02ae-66ca-4bcb-a2e7-aaeab6ee9c58)

![image](https://github.com/RonjaVee/smial/assets/148786247/9eb6d38a-26c4-46f1-813a-84eca666fba4)

![image](https://github.com/RonjaVee/smial/assets/148786247/29bea981-205c-41ba-bbbf-b6e7cde94329)


Lukitsin rootin ja estin rootin kautta kirjautumisen, eli koneelle pääsee nyt vain pääkäyttäjän salasanalla (joka on vahva, jottei sinne pääse ulkopuolisia pahiksia).


![image](https://github.com/RonjaVee/smial/assets/148786247/f8521b42-b02b-4f8a-9885-282b2af14df3)

![image](https://github.com/RonjaVee/smial/assets/148786247/8e2d479e-dbd5-4838-9496-e88755439dce)

Sitten asensin apache2:

![image](https://github.com/RonjaVee/smial/assets/148786247/70880d84-9c05-4660-977f-7ff14f38c871)

Ja tein reiän palomuuriin, jotta esimerkkisivu tulisi näkyviin, ja niinhän se näkyikin, kun katselin sivua kotikoneen Chromesta.

![image](https://github.com/RonjaVee/smial/assets/148786247/c2682f28-3a84-4694-a34c-d1ad6cd8f8c5)

![image](https://github.com/RonjaVee/smial/assets/148786247/6aa74659-2b05-4850-b755-6000361c59cd)






