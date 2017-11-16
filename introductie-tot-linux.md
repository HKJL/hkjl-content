Title: Introductie tot Linux
Date: 2015-10-25 18:00
Category: Basis
Tags: basis, linux, ubuntu
Slug: introductie-tot-linux
Authors: Sling
Summary: Het eerste deel uit een drie-delige serie die je de basis van het werken met de Linux commandline uitlegt, zodat je over voldoende basiskennis beschikt om de andere tutorials te kunnen volgen.

![XKCD Server Problem](images/xkcd-server-problem.png)

In deze uitgebreide tutorial zal ik je bekend maken met de beginselen van het gebruiken en beheren van een Linux-systeem. Dit zijn vaardigheden die nodig zijn om veel andere tutorials te kunnen volgen, aangezien daar op de kennis gebouwd wordt die je in deze tutorial zal vergaren.

Als je de goede volgorde van de basis tutorials aanhoudt heb je net de [vorige tutorial](je-eigen-linux-systeem.html) over Linux afgerond, waar we een virtuele machine hebben opgezet met hierop Ubuntu Server. Zo niet, dan adviseer ik je om deze eerst te volgen. We gaan in de onderstaande tutorial namelijk direct met dit systeem aan de slag! Zorg ervoor dat je virtuele machine gestart is en je in de console `ubuntu login:` ziet staan.

![Login scherm Linux](images/introlinux1.png)

Het zwarte rechthoekige venster wat je nu ziet met links bovenin wat tekst, heet de terminal. Vrijwel alles wat we met Linux zullen gaan doen, zullen we in deze omgeving uitvoeren. Je kent dit soort interfaces misschien van vroeger, zoals MS-DOS of hele oude spelcomputers. De terminal die je nu ziet is echter allesbehalve ouderwets. Het is trouwens wel mogelijk om Linux via een grafische omgeving met icoontjes en knopjes te beheren, maar dat gaan we niet doen! Hiervoor zijn een heleboel redenen te bedenken, waaronder de volgende:

- Door in een terminal te werken sta je veel dichter bij de echte werking van de computer, een grafische beheerinterface verbergt wat er eigenlijk onder de motorkap gebeurt. Door bekend te raken met de terminal leren we dus veel beter hoe Linux echt werkt.
- Als we later scripts gaan maken die taken voor ons gaan automatiseren, dan willen we daar kunnen opschrijven wat de computer moet doen. Deze opdrachten zullen identiek zijn aan wat we in de terminal intypen, of hier sterk op lijken.
- Op Linux servers draait bijna nooit een grafische interface. Als je jezelf aanleert om Linux via een grafische interface te beheren, zul je dus voor een heleboel verrassingen komen te staan als je je vaardigheden in de praktijk wil brengen.
- In het begin zal het even wennen zijn en zul je geregeld denken “Maar in een grafische omgeving kan ik dit veel makkelijker!”, maar uiteindelijk zul je je realiseren dat je via een terminal juist veel meer mogelijkheden hebt dan in een grafische omgeving, en dat je veel sneller en efficiënter kan werken.

# 0. In- en uitloggen, opstarten en afsluiten.

Wat je op dit moment in de terminal ziet is het zogenaamde login prompt, wat verschijnt zodra Linux klaar is met opstarten. Je kan hier een gebruikersnaam invoeren, op enter drukken, je wachtwoord invoeren, en weer op enter drukken. Als dit goed gaat, ben je ingelogd. Let op dat je bij het invoeren van het wachtwoord geen tekens te zien krijgt op het scherm, om zo te voorkomen dat mensen die mee kijken op je scherm kunnen zien hoeveel tekens je wachtwoord heeft.

<div class="opdracht">
  <p>Opdracht 1</p>
  <div class="subopdracht">Wat gebeurt er als je een gebruikersnaam invult die niet bestaat?</div>
  <div class="subopdracht">Wat gebeurt er als je wel je eigen gebruikersnaam invult, maar een verkeerd wachtwoord invult?</div>
  <div class="subopdracht">Log ten slotte in met je goede gebruikersnaam en wachtwoord om door te gaan met de volgende stappen.</div>
</div>

Als het goed is zie je nu een scherm zoals dit:

![Post-login scherm Linux](images/introlinux2.png)

We zijn nu ingelogd, wat betekent dat we commando‘s kunnen gaan uitvoeren. Dit zijn korte instructies die we intypen en afsluiten met de enter-toets. Linux leest vervolgens wat we hebben getypt en volgt deze instructies nauwkeurig op.

De eerste commando’s die we zullen gaan bekijken hebben te maken met het stoppen en herstarten van de computer, en het uitloggen van de gebruiker. Dat geeft ons meteen een heleboel controle over ons nieuwe Linux systeem. Hier volgt een aantal commando’s die we hiervoor kunnen gebruiken:

Commando                   | Uitleg
-------------------------- | --------------------------
`logout`                   | Log de huidige gebruiker uit en keer terug naar het login prompt.
`sudo reboot`              | Start de computer opnieuw op
`sudo halt`                | Stop meteen de computer
`sudo shutdown -h now`     | Stop meteen de computer (-h staat voor ‘halt’)
`sudo shutdown -h 5`       | Stop over 5 minuten de computer
`sudo shutdown -r now`     | Start de computer opnieuw op (-r staat voor ‘reboot’)

Het `sudo` commando is hier nodig, maar mag je voor nu even negeren. We zullen later in deze tutorial bekijken wat dit precies doet. Als je dit commando gebruikt wordt er om je wachtwoord gevraagd.

De laatste drie commando’s bestaan, zelfs zonder `sudo`, nog steeds uit meerdere gedeeltes. Het commando `shutdown` heeft namelijk extra _opties_ en _argumenten_ nodig, om te weten wat er precies moet gebeuren. Voorbeelden van opties bij `shutdown` zijn `-r` en `-h`. Opties worden gebruikt om de actie die een commando uitvoert wat specifieker te maken, in dit geval om aan te geven dat het shutdown commando de computer moet herstarten of uitschakelen. Deze opties hebben in dit geval ook nog een argument nodig, die aangeeft wanneer het `shutdown` commando de computer moet herstarten of uitschakelen. Er bestaan ook commando’s die je argumenten mee _kan_ geven, maar waar het niet verplicht is. Hoe je erachter kan komen wat een commando allemaal aan extra argumenten accepteert, zullen we later zien.

Nog iets wat je misschien opgevallen is, is dat er meerdere commando’s zijn die je kunt gebruiken om de computer meteen uit te zetten of te herstarten. Dit is iets wat in Linux veel voorkomt; er zijn meerdere manieren om hetzelfde doel te bereiken. Hou dat in je achterhoofd als je deze tutorial volgt, de voorbeelden die hier gegeven worden zijn in de meeste gevallen niet de enige manier om je doel te bereiken. Wel proberen we je de meest gebruikte manier aan te leren.

<div class="opdracht">
  <p>Opdracht 2</p>
  <div class="subopdracht">Probeer bovenstaande commando’s eens uit en observeer wat er gebeurt.</div>
  <div class="subopdracht">Wat gebeurt er als je `sudo` weglaat en alleen maar `halt` intypt?</div>
  <div class="subopdracht">Wat gebeurt er als je `sudo shutdown` zonder opties intypt?</div>
  <div class="subopdracht">Wat gebeurt er als je bij `sudo shutdown` wel de optie `-h` opgeeft maar hier geen argument achter zet?</div>
</div>

**Let op**: Voordat we doorgaan naar het volgende hoofdstuk is het belangrijk om te vermelden dat je een Linux systeem nooit zomaar uit mag zetten zonder de goede afsluitprocedure te volgen. Als je de VM geforceerd afsluit in VirtualBox dan gebeurt er hetzelfde als wanneer je bij een echte computer de stekker er zomaar uit trekt. Linux krijgt dan namelijk niet de kans om ‘netjes’ alle processen die lopen te beeindigen, wat kan betekenen dat je bestanden kwijtraakt die recentelijk zijn bewerkt en/of dat je schijf corrupt raakt!

# 1. Mappen en bestanden

Laten we voordat we onze eerste mappen en bestanden gaan aanmaken eerst bekijken hoe Linux deze mappen indeelt, ofwel hoe de structuur van het bestandssysteem in elkaar steekt. Je zult op Windows waarschijnlijk al eens namen gezien hebben zoals:
`C:\Program Files\Microsoft Office\OFFICE15\EXCEL.EXE`
met vooraan de naam van de schijf, vervolgens een serie mappen en op het einde de bestandsnaam. Op Linux is dit niet veel anders, behalve dat je als basis niet een ‘schijf’ hebt, maar een `/`. Zo ziet op Linux een volledig pad er als volgt uit: `/etc/programma/configuratie.txt`. Dit betekent een bestand `configuratie.txt` in de map `programma`, die weer in de map `etc` zit.

Een voorbeeld van een mappenstructuur op Linux is als volgt:

![Linux bestandssysteem](images/linux-bestandssysteem.png)

Helemaal bovenaan staat een `/`-teken, wat het startpunt is voor alle bestanden en mappen op het systeem. Het is zelf eigenlijk ook een soort map, waarin bestanden (in dit geval het bestand `document`) en submappen (in dit geval de mappen `etc`, `var`, `tmp`, `usr`, `home`) staan. In het voorbeeld hebben we nog een paar mappen uitgeklapt om het idee verder te illustreren. Ook staan er op diverse plekken bestanden.

<div class="opdracht">
  <p>Opdracht 3</p>
  <div class="subopdracht">Er staan 4 bestanden in de bovenstaande afbeelding, wat zijn de volledige paden naar deze bestanden?</div>
</div>

De bovenstaande afbeelding geeft natuurlijk maar een heel kleine greep uit de mappen die je kunt vinden op je Ubuntu server. Gelukkig heeft elke distributie, ook Ubuntu, voor het grootste gedeelte dezelfde mappenstructuur. Dus als je je straks comfortabel voelt met de Ubuntu structuur dan zul je je al snel thuis voelen op andere distributies. Door te werken met je Ubuntu systeem zul je vanzelf te weten komen waar veel van de mappen voor gebruikt worden, we zullen de belangrijkste mappen nu alvast doornemen:

Locatie        | Uitleg
-------------- | --------------
`/`            | Het startpunt van alle bestanden en mappen op je systeem, ook wel de ‘root’ (Engels woord voor de wortel van een plant of boom) map genoemd.
`/bin`         | Programma’s worden in deze map opgeslagen. Veel commando’s die we gaan gebruiken in deze tutorial zul je als een bestand in deze map vinden.
`/boot`        | In de boot map vind je alle bestanden die te maken hebben met het opstarten van Linux.
`/dev`         | Dit is een speciale map, waarin geen bestanden staan maar waarin alle hardware onderdelen van de computer een soort snelkoppeling hebben. Andere onderdelen van Linux en diverse programma’s kunnen deze koppelingen gebruiken om met de hardware van je systeem te praten.
`/etc`         | In windows staan alle instellingen van programma’s verspreid over het hele systeem, maar in Linux vind je alle configuratiebestanden in deze map. Hier zul je als beheerder van een systeem vaak mee te maken hebben.
`/home`        | Zoals de naam al aangeeft is dit de map waarin alle thuis-directories van de gebruikers te vinden zijn. Er zal op dit moment maar 1 map in staan, namelijk die van je eigen aangemaakte gebruiker.
`/lib`         | In deze map staan systeem libraries, dit zijn bestanden die nodig zijn voor de werking van diverse services en programma’s. We zullen hier in deze tutorial niets mee doen.
`/media`       | Verwisselbare apparaten zoals USB-sticks zijn in deze map te benaderen.
`/mnt`         | In deze map kunnen extra opslagapparaten gemount worden. Meer hierover in deel 2 van deze tutorial.
`/root`        | In de map /home staan de gebruikersmappen van de normale gebruikers, maar het beheersaccount van Linux (met de gebruikersnaam ‘root’) heeft een eigen plek in het bestandssysteem, namelijk deze map; /root. Let op, de ‘root’ van het bestandssysteem ‘/’ is wat anders dan deze map /root !
`/tmp`         | Hier staan tijdelijke bestanden die door diverse programma’s en gebruikers kunnen worden aangemaakt. Deze map kan bij een reboot worden leeggemaakt, dus sla hier niets belangrijks op!
`/var`         | Tenslotte staat in deze map een grote verscheidenheid aan bestanden, eigenlijk alles wat in de overige mappen niet thuishoort. Belangrijk om te weten: de meeste logbestanden worden in deze map opgeslagen.

Ga deze lijst nu niet uit je hoofd leren, maar probeer als je in deze en volgende tutorials mappen in Linux tegenkomt, te bedenken of je snapt waarom er juist voor die map gekozen is.

In de terminal bevindt je je op elk moment in een map op het systeem, net zoals je in bijvoorbeeld Windows Verkenner (of DOS) gewend bent. De commando’s die je uitvoert en die met mappen of bestanden te maken hebben worden dan in die locatie uitgevoerd. Maak je bijvoorbeeld een nieuw bestand aan zonder daarbij te vertellen in welke map dat moet gebeuren, dan maakt Linux het bestand aan in de map waar je op dat moment bent.

Tijd om zelf aan de slag te gaan! Hieronder volgt een lijst van commando’s die je zal gaan gebruiken om met bestanden en mappen te werken. Lees de lijst om te beginnen eerst door, zonder ze in je terminal te typen. Direct hierna volgt een opdracht waarmee je al deze commando’s kan oefenen.

Commando                           | Uitleg
---------------------------------- | ----------------------------------
`ls`                               | Bekijk de inhoud van de huidige map. Probeer ook eens de optie `-l` hierachter te zetten.
`ls /tmp`                          | Bekijk de inhoud van map `/tmp`
`pwd`                              | Bekijk in welke map we op dit moment zitten, de ‘working directory’.
`cd /tmp`                          | Navigeer naar `/tmp`
`touch mijnbestand`                | Maak een nieuw, leeg bestand aan met de naam `mijnbestand`
`cp mijnbestand /tmp`              | Kopieer het bestand `mijnbestand` in de huidige map naar de map `/tmp`
`cp mijnbestand /tmp/mijnbestand2` | Kopieer het bestand `mijnbestand` in de huidige map naar de map `/tmp` en geef het als nieuwe naam `mijnbestand2`
`mv /tmp/mijnbestand2 /home/user/` | Verplaats het bestand `/tmp/mijnbestand2` naar de map `/home/user/` (dit kun je ook gebruiken om mappen en bestanden een nieuwe naam te geven)
`mkdir /home/user/mijnmap`         | Maak een nieuwe map in `/home/user/` met de naam `mijnmap`
`rm /home/user/mijnbestand2`       | Verwijder het bestand `mijnbestand2` in de map `/home/user/`
`rmdir /home/user/mijnmap`         | Verwijder de map `/home/user/mijnmap` (de map `/home/user/` blijft bestaan)

<div class="opdracht">
  <p>Opdracht 4</p>
  <div class="subopdracht">Zoek op in welke map je op dit moment bent en bekijk de inhoud van de huidige map. Dit is onze eigen thuis (home) map waarin we alles mogen doen wat we willen, zonder dat andere gebruikers op het systeem daar last van hebben.</div>
  <div class="subopdracht">Maak hier een nieuwe map aan, met de naam ‘notities’, en bekijk daarna opnieuw de inhoud van de huidige map.</div>
  <div class="subopdracht">Navigeer van de huidige map naar de map ‘notities’ die je zojuist hebt aangemaakt en maak daarin een bestand met de naam ‘notitie1’</div>
  <div class="subopdracht">Ga terug naar de map waar je begon (je home map).</div>
  <div class="subopdracht">Geef de map ‘notities’ een nieuwe naam: ‘notes’.</div>
  <div class="subopdracht">Kopieer het bestand ‘notitie1’ uit de map ‘notes’ naar de map waar je begon.</div>
  <div class="subopdracht">Probeer de map ‘notes’ te verwijderen. Waarom lukt dit niet? Verwijder het bestand wat er voor zorgt dat je de map niet kan verwijderen en probeer het opnieuw.</div>
  <div class="subopdracht">Bekijk de inhoud van de root map (`/`) en probeer wat door de mappen hierin te navigeren. Zijn er mappen waar je niet in kunt komen? In welke map staan de meeste bestanden denk je?</div>
</div>

Tip: Gebruik het commando `clear` om het scherm leeg te maken zodat je wat meer overzicht krijgt! Als je er echt niet meer uit komt kun je altijd uitloggen met `logout` en weer opnieuw inloggen.

Stel nu dat je de volgende map zou willen aanmaken: `~/a/b/c/d/e/f/g/h/i/j/k/l/test/foo/1/` (gewoon, omdat het kan). Als we dat met de commando’s die we net hebben geleerd zouden moeten doen, dan moeten we best veel commando’s uitvoeren: `cd ~`, `mkdir a`, `cd a`, `mkdir b`, `cd b`, etcetera. Niet erg effectief dus. Hetzelfde geldt voor het verwijderen, als we in onze home map staan en we typen `rmdir ~/a/b/c/d/e/f/g/h/i/j/k/l/test/foo/1/` dan krijgen we de melding dat de map `a` niet leeg is. Als we map `a` in gaan krijgen we de melding dat `b` niet leeg is, etcetera. Daar zijn gelukkig handigere commando’s voor:

Commando               | Uitleg
---------------------- | ----------------------
`mkdir -p werkmap/b/c` | Maak in de huidige map de mappenstructuur `werkmap/b/c` aan. Dit betekent dus een map `werkmap`, met daarin een map `b`, en daarin ten slotte een map `c`.
`rm -r werkmap`        | Verwijder de map `werkmap` en alle mappen en bestanden die daar in zitten. Dit kan een gevaarlijk commando zijn, kijk dus goed of je geen typefouten hebt gemaakt voordat je dit uitvoert!

Probeer beide commando’s eens uit en gebruik tussen het aanmaken en verwijderen eens `cd` en `pwd` om te zien hoe je door je mappenstructuur heen kan navigeren.

## Zoeken op je systeem: find en locate

Je hebt net al rondgekeken in het systeem en een heleboel mappen en bestanden gezien. Best een wirwar van namen, het kan dus best eens gebeuren dat je niet meer precies weet waar je ook alweer dat ene bestand een paar weken geleden had opgeslagen. Gelukkig kun je in Linux ook zoeken naar een bepaalde bestandsnaam in je systeem, en zelfs zoeken _in_ een groep bestanden naar een stukje tekst.

![Zoeken](images/detective.png)

Linux houdt hiervoor een speciaal lijstje bij van alle bestanden en mappen in het systeem waar je heel snel doorheen kan zoeken. Dit lijstje wordt elke 24 uur automatisch geupdate, als de computer aan staat. Het zoeken in deze lijst kan met het commando `locate` gevolgd door de naam van het bestand of map waar je naar op zoek bent. Probeer het eens uit met bijvoorbeeld `locate test` en je zult zien dat je heel snel een lange lijst bestanden met ‘test’ in de naam te zien krijgt. Als je niet wilt wachten totdat het systeem deze lijst automatisch update, dan kun je dit ook met de hand doen, met het commando `sudo updatedb`. Het uitvoeren hiervan kan eventjes duren, maar daarna zul je weer heel snel kunnen zoeken, inclusief de meest recent aangemaakte mappen en bestanden.

Als je iets specifieker wil zoeken dan zul je gebruik moeten maken van het commando `find`. Dit commando heeft geen speciale lijst die hij snel kan doorzoeken, maar het zoekt echt de harde schijf door. Hierdoor is het trager dan `locate`.

Je kan met dit commando allerlei speciale condities opgeven, waar ik hier een paar voorbeelden van zal geven. Het kan best gebeuren dat je meldingen krijgt met ‘Permission denied’, want find probeert elke map die hij tegenkomt in te gaan, ook al heeft jouw gebruikersaccount hier misschien helemaal geen toegang toe. Hoe we deze foutmeldingen kunnen weg laten leren we in deel twee van deze tutorial.

Commando                       | Uitleg
------------------------------ | ------------------------------
`find /var -name test`         | Zoek alle bestanden en mappen met de naam `test` in de map `/var`
`find /etc -name *.conf`       | Zoek alle bestanden en mappen die eindigen op `.conf` in de map `/etc`
`find / -type d -name ba*`     | Zoek alle mappen in het hele systeem die beginnen met `ba`
`find /etc -type f -name test` | Zoek alle bestanden met de naam `test` in de map `/etc`
`find /var -mmin -10`          | Zoek alle bestanden en mappen op het hele systeem die in de laatste 10 minuten zijn gewijzigd.

Je krijgt ongetwijfeld meer tekst te zien bij sommige van bovenstaande commando’s dan er in je terminal past. Daardoor zie je alleen maar het onderste gedeelte van de uitvoer. Hoe je toch alle uitvoer kan zien en hier doorheen kan scrollen leren we in de volgende tutorial.

## Tab-completion, zoeken in bestanden en handige tekens.

Het komt nog wel eens voor dat je moet werken met hele lange bestands- of mapnamen. Neem bijvoorbeeld de map `/usr/src/Linux-headers-3.19.0-25/drivers/`, de eerste twee mappen uittypen in je terminal lukt nog wel maar de rest zou je liever niet helemaal willen uitschrijven omdat dit veel moeite kost en je kan ook nog eens makkelijk een typefoutje maken. Gelukkig is er een hele handige manier om Linux voor jou te laten werken in dit soort gevallen: tab-completion.

<div class="opdracht">
  <p>Opdracht 5</p>
  <div class="subopdracht">Ga de map `/usr/src/` in en bekijk welke bestanden en mappen hier in staan. Realiseer je dat je deze lange namen niet wil intypen en voer alleen het commando `cd` gevolgd door de eerste paar letters van de namen in. Druk nu op de &lt;tab&gt; toets op je toetsenbord en kijk wat er gebeurt. Wat gebeurt er als je nog een paar keer op tab drukt?</div>
  <div class="subopdracht">Probeer eens de eerste letter van een commando in te typen, en druk twee keer op de &lt;tab&gt; toets. Je krijgt alle mogelijke commando’s die met deze letter beginnen te zien! Ga zo enkele letters af om te zien hoeveel commando’s Linux wel niet heeft.</div>
</div>

We hebben enkele alinea’s terug gezocht naar bestanden en mappen op basis van de bestandsnaam. Maar het zou natuurlijk ook wel erg handig zijn als we _in_ de bestanden op ons systeem kunnen zoeken naar stukken tekst. Gelukkig heeft Linux hier een hele geavanceerde tool voor, namelijk `grep`. Je kan een heleboel dingen met dit commando, maar voor deze tutorial zullen we ons tot enkele eenvoudige oefeningen beperken. Het enige wat je bij hier goed moet onthouden is de volgorde van de argumenten die je meegeeft. Het eerste argument na grep is de zoekterm die je wil gebruiken, en het tweede argument is het bestand waar je in wil zoeken. Ook is het met een extra optie mogelijk om in mappen (en submappen) te zoeken, ik zal dit laten zien in enkele voorbeelden:

Commando                        | Uitleg
------------------------------- | -------------------------------
`grep 'root' /etc/passwd`       | Zoek naar alle regels in `/etc/passwd` waar het woord `root` in voorkomt.
`grep -r 'root' /etc`           | Zoek naar alle regels in alle bestanden en mappen in `/etc` waar het woord `root` in voorkomt.
`grep -r -i 'root' /etc`        | Hetzelfde als hierboven, maar zoek nu naast `root` ook naar `Root`, `ROOT`, etc; kortom: niet hoofdlettergevoelig.
`grep -r -i -n 'root' /etc`     | Weer hetzelfde, maar laat nu ook bij elk zoekresultaat het regelnummer zien waarop het woord `root` is gevonden.
`grep -v 'nologin' /etc/passwd` | Zoek naar alle regels in `/etc/passwd` waar het woord `nologin` **niet** in voorkomt.

Tip: Je kan bij de meeste commando’s meerdere losse opties zoals `-r -i` ook schrijven als `-ri`

<div class="opdracht">
  <p>Opdracht 6</p>
  <div class="subopdracht">Zoek naar alle regels in het bestand `/etc/group` waarin je gebruikersnaam voorkomt.</div>
  <div class="subopdracht">Op welk regelnummer komt ‘battery’ het eerst voor in het bestand `/etc/hdparm.conf` ?</div>
  <div class="subopdracht">Welke bestanden in de map `/etc/pam.d/` bevatten het woord `password` ?</div>
  <div class="subopdracht">In het bestand `/etc/hdparm.conf` staat een hoop commentaar, wat dient als documentatie. Elke commentaar-regel begint met een `#`. Gebruik 1 `grep` commando om te achterhalen wat er behalve dit commentaar in het bestand staat.</div>
</div>

We sluiten dit hoofdstuk af met enkele tekens die je in alle commando’s kunt gebruiken die we net geleerd hebben. Als je deze tekens slim gebruikt hoef je een stuk minder te typen en kun je op veel systemen dezelfde commando’s gebruiken, ook al verschillen de mappen misschien van naam. Het gaat om drie tekens / tekencombinaties:

Tekens | Uitleg | Voorbeeld
------ | ------ | ------
`.`    | De huidige map. Handig als je bijvoorbeeld iets van of naar de huidige map wil kopieren of verplaatsen. | `cd /tmp`<br />`cp /boot/grub/grub.cfg. `
`..`   | De bovenliggende (in Engels: parent) map. Dit kun je meerdere keren gebruiken in een pad. | `cd /boot/grub/`<br />`cp grub.cfg ../../tmp`
`~`    | De home map van de huidige gebruiker, dus een map in `/home/` of bij de root gebruiker de map `/root` | `cd ~`

Tip: Als je net met cd naar een andere map bent genavigeerd, onthoudt Linux in welke map je hiervoor zat. Gebruik daarvoor cd -. Je kan op die manier heel eenvoudig tussen twee locaties wisselen.

# Tekstbestanden

TODO