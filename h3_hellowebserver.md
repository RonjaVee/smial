 
 
 
 ### Localhost vastaa

 Olin luennolla saanut tehtyä jo esimerkkisivun palvelimelle, ja se näkyi kuten pitää.
 
 ![image](https://github.com/RonjaVee/smial/assets/148786247/74755942-4100-4da7-9ec8-771772bebd0d)
 ![image](https://github.com/RonjaVee/smial/assets/148786247/73358757-35e0-418f-974d-5a1ad1ab27b7)
 
### Lokirivien tulkintaa

Kun lähdin tutkimaan lokitietoja, ei uusia merkintöjä lokeista (sekä error.log että access.log). Kokeilin vielä päivittää sivua, mutta uusia merkintöjä en saanut näkyviin.


![image](https://github.com/RonjaVee/smial/assets/148786247/ae464e72-57b9-4a4f-ae30-25696a2770a0)
![image](https://github.com/RonjaVee/smial/assets/148786247/2565e0d3-fa46-42e6-9094-3577d925950a)

Tältä loki näytti, eikä muutoksia tullut tehtävien jälkeenkään näkyviin:

![image](https://github.com/RonjaVee/smial/assets/148786247/a4a986be-1cad-4e28-a5d4-d7825a9b71a7)

Lähdin sitten vanhasta lokimerkinnästä tutkimaan, mitä kaikkea se kertoo. Kopioin merkinnän ja siirsin sen tekstieditoriin ja otin siitä kuvakaappauksen, sillä en saanut lokimerkintöjä järkevästi näkyviin
komentokehotteessa.

![image](https://github.com/RonjaVee/smial/assets/148786247/2bcea386-d422-43c7-893d-044018a704a2)


- 127.0.0.1: IP-osoite, josta pyyntö tulee. Tässä local hostin IP eli minun.
- ensimmäinen - : tunnistautuneen käyttäjän nimi (nyt tyhjä)
- toinen - : käyttäjän tunnus (nyt tyhjä)
- Seuraavaksi on aikaleima, jolloin pyyntö on tehty. Tässä kohti näkyy eri päivä kuin tehtävää tehdessäni oli.
- GET-kohdassa kerrotaan pyynnön tyyppi: tässä kohteena index.html ja pyynnön protokolla ja versio http/1.1
- Luku 304 on statuskoodi ja 247 kertoo, kuinka paljon dataa tavuina siirtyi palvelimelta kyselyn esittäjälle. Statuskoodi 304 tarkoittaa, ettei sivua olla muokattu sitten viime pyynnön, 
- joten tiedonsiirtoa ei tehdä uudestaan, vaan sivusto näyttää välimuistiversion.
- -	:Tässä kohtaa tarkoittaa, ettei viittausta (refer) ole saatavilla, eli  tietoa siitä, mistä osoitteesta pyyntö tuli.
Mozilla-kohdasta eteenpäin näkee käytetyn selaimen ja sen version.

### Uusi name based virtual host

Lähdin luomaan uutta sivua edellisen tapaan ohjeen(linkki) mukaan. Aloitin luomalla konfiguraatiotiedoston. Tämä konfiguraatiotiedosto asettaa sivuston "hattu.example.com" toimittamaan tiedostoja hakemistosta
"/home/xubuntu/publicsites/pyora.example.com" ja vastaamaan pyyntöihin, jotka kohdistuvat sekä pyora.example.com -sivustoon. 

![image](https://github.com/RonjaVee/smial/assets/148786247/c4157557-90d6-41de-b024-5180eaa2ef50)


![image](https://github.com/RonjaVee/smial/assets/148786247/b7ababaf-0194-4feb-b2f6-e3473a38d62d)

Sitten kirjoitin sivustolle vähän tekstiä testatakseni, että se näkyy kuten pitää.

![image](https://github.com/RonjaVee/smial/assets/148786247/032d54cb-5f9f-4620-802d-5fe7e2617b96)

![image](https://github.com/RonjaVee/smial/assets/148786247/ac8c62a6-fc6a-4f8a-9dda-3314e08e6af8)

Poistin vanhan sivun sites-enabled -kansiosta.

![image](https://github.com/RonjaVee/smial/assets/148786247/0aff4e2a-0577-45db-bc71-3f84d33d35d0)

Käytin HTML-kieltä sivun laatimiseen. Index.html -tiedostoa voi muokata ilman sudoa, joten näitä kokeiluja voi tehdä ilman pääkäyttäjän oikeuksia.

![image](https://github.com/RonjaVee/smial/assets/148786247/c36b34f7-0ad0-4c41-9859-9e8065d13639)
![image](https://github.com/RonjaVee/smial/assets/148786247/dc41c37a-dbf3-4ea2-9e93-bb06b42598db)
![image](https://github.com/RonjaVee/smial/assets/148786247/2980f10a-6257-46e9-bdcd-3f7a8db55388)

### Curl-komennot





Lähteet:
https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/#h3-hello-web-server
https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited
https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/
https://www.sumologic.com/blog/apache-access-log/
https://betterstack.com/community/guides/logging/how-to-view-and-configure-apache-access-and-error-logs/
https://ahrefs.com/seo/glossary/304-not-modified
https://gist.github.com/chrisvfritz/bc010e6ed25b802da7eb


 
 
 

 

 
 
 
 
 
 
