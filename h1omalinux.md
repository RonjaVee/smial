## Tiivistelmät Raportinkirjoitusohjeesta sekä Free Software Definitionista

[Raportin kirjoittaminen](https://terokarvinen.com/2006/raportin-kirjoittaminen-4/)
-Raportin ohjeiden on oltava toistettavia toisen henkilön toimesta samassa ympäristössä
-Raportista on nähtävä täsmällisesti mitä tehtiin, mitä tapahtui ja milloin tarkkoine vikailmoituksineen
-Raportissa on käytettävä korrektia kieltä ja aikamuotoa ja sen rakenne tulee olla helposti seurattava
-Raportissa tulee viitata käytettyihin lähteisiin
-Plagiointi, sepittäminen sekä tekijänoikeuksien rikkominen on kiellettyä

[FSF](https://www.gnu.org/licenses/gpl-3.0.html)
-Ideana on säilyttää vapaus
-Käyttäjällä on oikeus kopioida, käyttää, muokata ja kehittää ohjelmistoa
-Käyttäjällä on oikeus jakaa alkuperäistä tai muokattua ohjelmistoa kolmansille osapuolille
-Käyttäjän jakaessa ohjelmiston muokattua versiota on muokkaukset oltava julkisesti saatavilla
-Muokatuilla versioilla on oltava sama GPL-lisenssi

## Linuxin asentaminen virtuaalikoneeseen

Tavoitteenani oli asentaa virtuaalikoneeseen Linux-ytimeen perustuva Debian-käyttöjärjestelmä Linux-palvelimet -kurssin tulevia harjoitustehtäviä varten.

# Laitteen tiedot

AMD Ryzen 5 3600 6-Core Processor 3.59 GHz
RAM: 16,0 Gt
64-bittinen käyttöjärjestelmä, x64-suoritin
Windows 10 Pro, versio 22H2

Asensin Oracle Vm Virtual Box -ohjelman sekä Viimeisimmän Debian Live -levykuvan (debian-live-12.1.0-amd64-xfce.iso) PC:lle.
Pystytin virtuaalikoneen ohjeen [Tero Karvinen: Install Debian on Virtualbox - Updated 2023](https://terokarvinen.com/2021/install-debian-on-virtualbox/?fromSearch=install%20debia#the-solution---virtualbox-guest-additions) mukaan.
Sain seuraavan virheilmoituksen bootatessa: 

(kuva)

# Ongelmanratkaisua

Kokeilin ensimmäisenä asentaa VirtualBoxin toiselle asemalle, mutta tästä ei ollut apua, joten asensin sen uudelleen C: -asemalle. 

Seuraavaksi syötin virheilmoituksen OpenAI:n ChatGPT:lle (versio 3.5). Sain vastaukseksi seuraavaa: 

1.	Enable AMD-V in BIOS/UEFI:
•	Restart your computer and enter the BIOS/UEFI setup (usually by pressing a key like Del, F2, or Esc during the boot process).
•	Navigate to the "Advanced" or "CPU Configuration" section.
•	Look for an option related to "AMD Virtualization" or "AMD-V" and make sure it is enabled.
•	Save the changes and exit the BIOS/UEFI. The specific steps may vary depending on your motherboard.
2.	Verify Host OS Settings:
•	Ensure that virtualization support is enabled in your host operating system. For Windows, this can usually be checked in the Task Manager under the "Performance" tab.
Look for "Virtualization" or "Virtualization: Enabled." On Linux, you can use commands like lscpu or grep -E 'svm|vmx' /proc/cpuinfo to check if virtualization extensions are available.
4.	Update BIOS/UEFI:
•	Check if there is a BIOS/UEFI update available for your motherboard. Sometimes, newer firmware versions provide better support for virtualization technologies.
5.	Check Host OS Compatibility:
•	Ensure that your host operating system is compatible with AMD-V. Some older operating systems or specific configurations may not fully support virtualization.
6.	Verify Hyper-V Status:
•	If you are using Windows as the host OS, check the status of Hyper-V. Hyper-V and VirtualBox may conflict, so make sure Hyper-V is disabled if you are not using it.
•	Open a Command Prompt with administrative privileges.
•	Run the command: bcdedit /set hypervisorlaunchtype off
•	Reboot your computer.
7.	Reinstall VirtualBox:
•	Uninstall VirtualBox and then reinstall it. This ensures that the VirtualBox installation is using the correct settings and drivers.
After performing these steps, try running VirtualBox again. If the issue persists, there may be additional troubleshooting required, and you may want to check VirtualBox forums or community support for more specific assistance.

Tarkastin onko virtualization enabled (tehtävienhallinta -> suorituskyky -> suoritin -> virtualisointi: tila oli disabled).

Avasin BIOS:in vaihtaakseni virtualization->enabled ja käytin apuna videota: [How do I enable virtualization in BIOS AMD Ryzen: tekijä Made 4 Geek, julkaisupäivä 23.5.2021](https://www.youtube.com/watch?v=FHW3-m1sO1s)

Bios tietenkin näytti erilaiselta omalla laitteella, mutta polku oli hyvin samankaltainen:
aloitusnäyttö -> advanced mode -> advanced-kohta -> valitaan svm mode ja siitä disabled vaihdetaan enabled -> takaisin aloitussivulle -> save and exit.

Käynnistin koneen uudestaan, ja kokeilin käynnistää virtuaalikonetta Virtual Boxin kautta (en asentanut Virtual Boxia uudelleen). Tällä kertaa kone käynnistyi, joten siirryin asentamaan Debiania.

# Debianin asennus

Valitsin kieleksi ja näppäimistön kieleksi suomen ja sijainniksi Suomi. 
Määritin koneen nimen (satunnainen nimi, jota ei voi liittää laitteeseen tai sen ominaisuuksiin) ja salasanan (vahva) sekä pääkäyttäjän nimen (etunimi+sukunimi) ja salasanan (myös vahva).

Levyn osiointitavaksi valitsin Ohjattu - käytä koko levyä.
Asennettaviksi ohjelmiksi valitsin oletuksena olevat, eli Debian desktop environment + vakiot järjestelmätyökalut.

(kuva)

Levyn osiointimalliksi valitsin suositellun (vain yksi levyosio).
Asensin GRUB-alkulatausohjelman, sillä asentamani järjestelmä on virtuaalikoneen ainoa käyttöjärjestelmä. Valitsin laitteeksi ainoan valikossa näkyvän vaihtoehdon.

Käyttöjärjestelmän asentamisessa meni n. 10 minuuttia, jonka jälkeen laite käynnistyi uudelleen. Nyt pääsin kirjautumaan sisään pääkäyttäjälle, ja käyttöjärjestelmä oli käyttövalmis. 
Kokeilin vielä avata selaimen ja avata satunnaisen sivuston, ja kaikki toimi kuten pitää.

(kuva)

-------------------

Tehty 18.1.2024.

Tätä dokumenttia saa kopioida ja muokata [GNU General Public License](http://www.gnu.org/licenses/gpl.html) (versio 2 tai uudempi) mukaisesti. 
Pohjana Tero Karvinen 2024: Linux Palvelimet 2024 alkukevät, [https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/](https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/)

