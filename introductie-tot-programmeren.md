Title: Introductie tot programmeren
Date: 2017-11-19 18:00
Category: Basis
Tags: basis, programmeren, algoritmes
Slug: introductie-tot-programmeren
Authors: Jantje2000
Summary: Type hier een korte samenvatting in 1 zin.

Programmeren kan in veel verschillende talen, maar toch zijn de basis principes over het algemeen ongeveer gelijk. In deze tutorial wil ik jullie de basis van het programmeren uitleggen. We gaan echter nog geen echte programmeertaal leren.

Wat is een programma nu eigenlijk? Een programma is ten diepste gewoon een reeks instructies die duidelijk maken wat er moet gebeuren. Dit moet allemaal precies goed gebeuren, zodat alles correct wordt uitgevoerd. Stel bijvoorbeeld dat jij de instructies wil geven om naar de koelkast te lopen en een worst te pakken. De instructies zouden dan dus zo luiden:

- Loop naar de koelkast
- Pak de knop beet
- Doe de koelkast open
- Laat de knop los
- Pak de worst
- Pak de knop beet
- Doe de koelkast dicht
- Laat de knop los

Stel dat je één instructie zou vergeten, of dat je die niet zou doen, dan gaat het fout. Als je bijvoorbeeld de deurknop niet los zou laten gaat het ook nog wel, maar het gaat toch niet helemaal goed. Het kan echter ook dat jij zult vergeten de koelkastdeur dicht te doen. Dan zal je een foutmelding krijgen. Wat ik net heb laten zien is een programma. Zo’n programma snapt natuurlijk iedereen, behalve de computer. De menselijke taal is namelijk veel te variabel voor computers. 

Zo kun je de volgende 2 compleet verschillende zinnen noemen, terwijl er precies hetzelfde mee wordt bereikt.

- Doe de koelkast open
- Trek de klink naar je toe (de deur zal dan ook opengaan)

Aan dit voorbeeld heb je kunnen zien dat de menselijke taal niet heel erg handig zou zijn. Daarom bestaan er de programmeertalen. Die zijn zo gemaakt dat je maar op een paar manieren iets kunt zeggen, zodat de computer weet wat jij bedoelt. We gaan deze programmeertalen nu echter niet behandelen, omdat we hier vooral zullen gaan kijken naar de basis van programmeren die overal terugkomt.

Hoe maak je broncode van een idee

Als je wilt gaan programmeren moet je eerst een idee hebben. Maar als je een idee hebt, hoe maak je dit dan werkelijkheid? Wat je eerst moet gaan doen als je een idee hebt is het volgende rijtje afgaan. Je moet:

- Analyseren
- Ontwerpen
- Programmeren
- Testen
- Implementeren

Eerst ga je je idee analyseren. Dan ga je kijken wat jouw programma precies nodig heeft, of welk probleem je wilt gaan oplossen. Als je weet hoe je programma er precies uit moet gaan zien, dan kun je beginnen met het ontwerpen. Hier zijn speciale “talen” voor. Als je een programma wilt ontwerpen kun je UML gebruiken en voor databases kun je ERD’s ontwerpen. Als je eenmaal weet hóé het moet worden gebouwd kun je gaan programmeren. Je schrijft de codes, zodat de computer weet wat hij moet doen. Dan mag je het hele systeem gaan testen. Je gaat kijken of alles werkt en wanneer dit niet werkt moet je verder programmeren. Als dit allemaal gedaan is moet je het hele systeem implementeren in de bestaande omgeving, of je moet het systeem op een server implementeren, zodat iedereen het kan benaderen en gebruiken.

# Compileren

Ik heb net verteld dat gewone menselijke taal te onduidelijk is voor een computer en dat je daarom in speciale programmeertalen moet werken. Deze programmeertalen zijn over het algemeen nog steeds te lastig voor de computers. Nu vraag je je misschien af waarom we dan programmeren in een programmeertaal als de computer daar toch niets van snapt. Er is één geruststelling. De computer gaat die code uiteindelijk we uitvoeren. Er zijn namelijk speciale programma’s, zogenaamde compilers, die de programmeercode omzetten in enen en nullen. Hierdoor kan de computer de programmeertaal toch uitvoeren. Bij de menselijke taal zou dit niet mogelijk zijn, omdat de compiler niet zou weten hoe hij die taal zou moeten vertalen naar enen en nullen.

# Datatypen en variabelen

Dan gaat nu het echte werk beginnen. We gaan er nu naar kijken welke soorten types data we hebben. Er zijn de volgende soorten data types:

- Boolean
- String
- Char
- Int
- Float

Een boolean kan maar twéé waardes bevatten, namelijk “Waar” of “Niet waar”. In een programmeertaal is dit meestal “True” of “False”. Een string daarentegen kan alles bevatten. Een string is een heleboel tekens achter elkaar, dus bijvoorbeeld “Hallo, wij zijn van HKJL”, of “Wat vind jij van deze tutorial?”. Een char komt van Character en kan dus één karakter bevatten, zoals de “1”, de “a”, of een “g”. De int is een getal evenals de float. Het verschil tussen deze beiden is dat de float decimale getallen kan bevatten, zoals 1,345 of 4,5 terwijl een int alleen hele getalen kan bevatten, zoals 1, 4, 10.

Je wilt natuurlijk ook iets met deze waarden kunnen doen. Daarom sla je deze op in een variabele. Een variabele is een kleine opslagplaats waar je zo’n stukje data kan bewaren. Een voorbeeld is bijvoorbeeld: `Leeftijd = 16` De variabele leeftijd bevat hier dan een int met een waarde van 16.

<div class="opdracht">
  <p>Opdracht 1</p>
  <div class="subopdracht">Uit welke soorten datatypes bestaan de volgende variabelen?<br />
    <ul>
      <li>Leeftijd = 28</li>
      <li>Naam = “Piet”</li>
      <li>Programmeur = True</li>
      <li>Lengte = 1.82</li>
    </ul>
  </div>
</div>

Er bestaat nog één andere variabele soort, namelijk de array. Deze kan heel veel datatypes opslaan in één variabele. In één variabele kunnen dan dus een string, een float, een int, een boolean en een char opgeslagen worden.

# Data flow

Uiteindelijk willen we natuurlijk ook iets met die variabelen gaan doen, want waarom slaan we ze anders op? Stel bijvoorbeeld dat we een programma willen schrijven voor een festival waar je pas in mag als je 25 bent. Dan willen we die voorwaarde kunnen toetsen. Hiervoor gebruiken we de “if” functie.
Stel dat de leeftijd dan dus boven de 25 moet zijn krijg je de volgende instructies:

Je ziet dat we zeggen dat de leeftijd gelijk aan of meer dan 25 moet zijn. We zien nu echter niets wanneer je onder de 25 bent, dus als je onder de 25 bent, dan moet je ook te horen krijgen dat je niet naar binnen mag. Hiervoor gebruiken we de “else” functie. Deze zegt: “als de voorwaarde niet geldt, dan moet het volgende gebeuren. Hier zouden we dus als programma krijgen:

Als je nu dus te jong bent zal je te horen krijgen dat je nog te jong bent. Soms wil je echter twee voorwaarden testen. In ons geval heb je bijvoorbeeld ook nog een kaartje nodig. Ook zonder kaartje mag je niet worden toegelaten, ook al ben je wel ouder dan 25. Dan krijgen we dus het volgende:

Nu zul je worden toegelaten wanneer iemand een kaartje heeft terwijl hij ook nog 25 jaar of ouder is. Als iemand nu echter nog geen kaartje heeft, maar wel 25 is krijgt hij te zien dat hij te jong is. Dit klopt echter niet, dus we moeten ook de else if gebruiken. Hiermee krijgen we de volgende code:

Nu weten we hoe de “if”, “else if” en de “else” werken, maar we kunnen nog veel meer doen. Een voorbeeld is de While functie. Zolang een bepaalde voorwaarde geldt zal alles worden uitgevoerd.

Een voorbeeld bij ons festival: Er mogen maar 1000 mensen naar binnen, dus zouden we krijgen:

Dan hebben we ook nog een for functie. Deze zal voor iedere waarde de actie uitvoeren. Stel dat we een array hebben, met daarin de namen van 5 mensen:
[“Fatima”, “Simon”, “Piet”, “Rafael”, “Hassan”]
Dan willen we dat iedere naam uit deze array een keer wordt getoond. Een voorbeeld zou dan zijn.

De uitkomst zou dan zijn:

Dan kun je voor iedere waarde uit een array dus iets uitvoeren.
Functies
Een belangrijke afspraak in veel programmeertalen is dat je jezelf niet moet herhalen. Als je één stukje code meerdere keren gebruikt moet je dit niet twee of drie maal in je code plakken, maar dan maak je daar een functie van, zodat je die functie meerdere keren aanroept. Stel dat je heel vaak de naam wilt printen in een programma. Dan kun je doen:

Nu zou dat nog tamelijk overzichtelijk zijn, maar later niet meer, als je bijvoorbeeld steeds berekeningen moet uitvoeren, of andere stukken onoverzichtelijke code hebt. Dan maak je een functie, dus:

Als je hetzelfde programma zou willen maken programmeer je nu:

Het voordeel daarvan is dat je nu meer overzichtelijke code zult hebben, waardoor andere programmeurs en ook jij dit beter zullen snappen.
Programmeerstandaarden
Er zijn verschillende regels waar vrijwel alle (professionele) programmeurs zich aan houden. Een voorbeeld is het indenten. In de voorbeelden die ik net steeds gaf zijn ook geindent. Dit houdt in dat je x spaties naar voren gaat, zodat men weet wat waarbij hoort. Een voorbeeld is:
Dit is niet in één oogopslag duidelijk. Want welke “}” hoort bij welke if? Dan is het volgende stukje code duidelijker.

Je ziet dat hier na iedere if/else/else if er een tab/x spaties is gebruikt, om zo duidelijkheid te creëren. Het is nu veel duidelijker wat er gebeurt onder welke if, dan daarnet.

---

# Antwoorden op opdrachten

Hieronder zijn per opdracht de antwoorden te bekijken, door op de juiste opdracht te klikken. Probeer natuurlijk wel eerst de opdrachten te maken, anders leer je de stof niet goed en kom je bij andere tutorials kennis te kort, met valsspelen heb je alleen jezelf.

<details>
  <summary>Opdracht 1</summary>
  <ul>
    <li>Int, String, Boolean, Float</li>
  </ul>
</details>