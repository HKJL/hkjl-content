Title: Slimme vragen stellen: hoe hou je je medehackers te vriend?
Date: 2015-10-18 18:00
Category: Basis
Tags: basis, troubleshooting, vragen
Slug: slimme-vragen-stellen-hoe-hou-je-je-medehackers-te-vriend
Authors: Sling
Summary: 15 korte tips hoe je slim en effectief vragen kunt stellen over technische onderwerpen.

![XKCD - Black Hat Support](images/black_hat_support.png)

Voordat we aan de technische tutorials beginnen is het goed om even stil te staan bij de manieren waarop je hulp kan krijgen bij deze tutorials. Vaak ben je niet de enige op de wereld met dezelfde vraag, en vind je dus het antwoord al door simpelweg op het Internet te zoeken en door te klikken naar een website zoals ‘stackoverflow’ of ander blog, forum of mailinglist-archief. Als je toch geen antwoord kan vinden zul je moeten gaan overleggen met andere mensen op zo’n website of op IRC. Dit lijkt niet heel moeilijk, maar toch adviseer ik je om deze tutorial aandachtig te lezen zodat het makkelijker wordt om hulp te **krijgen** en voor anderen het makkelijker wordt om jou hulp te **geven**.

In de vorige [tutorial over IRC](introductie-tot-irc.html) hebben we al even kort stilgestaan bij hoe je het beste IRC kunt gebruiken om hulp te krijgen met een technische vraag. De tips in deze tutorial leggen dit in meer detail en iets breder uit. En voor de duidelijkheid, het stellen van vragen hoeft zich niet tot IRC te beperken, ook mailinglijsten, forums of soms zelfs persoonlijke gesprekken lenen zich hier prima voor.

De meeste van deze tips zijn gebaseerd op de sites die je onderaan de tutorial ziet, in combinatie met mijn eigen ervaring met technische ondersteuning geven via IRC en andere digitale media. Voel je vooral niet persoonlijk aangevallen als je het niet eens bent met een van de tips, discussieer dit liever onderaan de pagina!

---

# Tip 1: Stel je echte vraag

```irc
22:48:50 * INeedHelp joins #helpdesk
22:48:57 <INeedHelp> Hoi! Is er iemand?
22:49:40 <Sling> Ja, wat is er aan de hand?
22:49:50 <INeedHelp> Kun je me helpen?
22:49:58 <Sling> Ligt eraan wat de vraag is..
22:50:03 <INeedHelp> Het gaat over PHP
22:51:00 <Sling> Ok.. en wat is je vraag dan?
```

Dit klinkt misschien nogal voor de hand liggend, maar toch komt de bovenstaande situatie in technische kanalen erg veel voor. Met openingszinnen als “Hoi, kan iemand me helpen?” of “Mag ik een vraag stellen?” of “Ik heb een probleem!” kan niemand iets, je verplicht op die manier anderen om direct al moeite te gaan steken in het lospeuteren van de echte vraag die je hebt en dat kost jezelf en je helpers alleen maar tijd en moeite. Voor jou is het misschien niet zo’n probleem, maar voor helpers in zo’n kanaal is het vervelend als ze dit 100 keer per dag moeten doen.

Als je in het echt iemand aanspreekt dan is het natuurlijk netjes om even te vragen of iemand tijd voor je heeft, maar in een IRC-kanaal zitten mensen vaak al te wachten op vragen, als ze geen tijd hebben of afwezig zijn dan reageren ze niet. Dus in plaats van zo’n onhandige start, begin meteen met je echte vraag zodat de mensen die je willen en kunnen helpen je direct een antwoord kunnen geven:

```irc
22:48:50 * INeedHelp joins #helpdesk
22:48:57 <INeedHelp> Hoi! Ik ben bezig met PHP en ik krijg de hele tijd deze error http://pas.te/SDsda8s, wat moet ik doen?
22:49:40 <Sling> INeedHelp: Zo te zien ben je een ; vergeten aan het einde van regel 12
22:49:50 <INeedHelp> Ah, inderdaad, thanks!
```

---

# Tip 2: Wees precies

```irc
22:48:50 * INeedHelp joins #helpdesk
22:48:57 <INeedHelp> Hoi! Ik ben bezig met PHP en ik krijg de hele tijd deze error http://pas.te/SDsda8s, wat moet ik doen?
22:49:40 <Sling> Zo te zien ben je een ; vergeten aan het einde van regel 12
22:49:50 <INeedHelp> Nee dat had ik al geprobeerd.
22:49:58 <Sling> Ah, dat wist ik niet. Wat gebeurde er toen?
22:50:03 <INeedHelp> Toen werkte het nog steeds niet.
22:51:00 <Sling> Ok..
```

Zelfs al begin je direct met het stellen van je vraag, kan het toch mis gaan. Het is namelijk best lastig om een goede vraag te stellen. Uitdrukkingen zoals “Ik heb alles al geprobeerd” of “Het werkt niet” of “Het doet niet wat ik wil” zijn eigenlijk compleet nutteloos en vertellen de mensen die je willen helpen helemaal niets over het probleem en zullen je niet dichter bij een oplossing brengen.

Probeer in een vraag altijd de volgende zaken te vermelden:

- Wat probeer je te bereiken? Beschrijf stap voor stap wat je tot nu precies gedaan hebt.
- Wat ging er mis, wat gebeurde er in plaats van wat je verwachtte?
- Wat heb je tot nu toe geprobeerd om dat probleem op te lossen?
- Indien van toepassing: Heeft het eerder wel gewerkt en zo ja, wat is er sindsdien veranderd?

En probeer de volgende zaken ook paraat te hebben, hier zal zeer waarschijnlijk ook naar gevraagd worden:

- Specificaties van de omgeving, dus je besturingssysteem, relevante software, het liefste inclusief versienummers.
- Indien van toepassing: Complete en letterlijke foutmeldingen en logbestanden

Het leuke is dat je bij het opstellen van zo’n goede en complete vraag zelf vaak al in de gaten krijgt wat er mis gaat en je je eigen vraag kan beantwoorden. En als dit niet het geval is, wordt het in ieder geval een stuk makkelijker voor anderen om je goed te helpen.

```irc
22:48:50 * INeedHelp joins #helpdesk
22:48:57 <INeedHelp> Hoi! Ik ben bezig met PHP en ik kreeg de hele tijd deze error http://pas.te/SDsda8s, de missende ; heb ik toegevoegd, maar toen kreeg ik weer een andere foutmelding over 'missing mbcrypt module', wat is dat?
22:49:40 <Sling> INeedHelp: Dat is een PHP-module, heb je die geladen in je php.ini bestand?
22:52:50 <INeedHelp> Dat heb ik nu gedaan en het werkt, bedankt!
```

---

# Tip 3: Leg uit wat je aan het doen bent

```irc
22:48:50 * INeedHelp joins #helpdesk
22:48:57 <INeedHelp> Hoi! Ik ben bezig met PHP en ik kreeg de hele tijd deze error http://pas.te/SDsda8s, de missende ; heb ik toegevoegd, maar toen kreeg ik weer een andere foutmelding over 'missing mbcrypt module', wat is dat?
22:49:40 <Sling> INeedHelp: Dat is een PHP-module, heb je die geladen in je php.ini bestand?
22:52:50 <INeedHelp> Die heb ik geladen, maar dat werkte ook niet. Ik heb de regels 12 t/m 15 weggehaald en nu heb ik een andere foutmelding!
```

Wat er vaak gebeurt, is dat iemand met een probleem komt, enkele tips krijgt, en vervolgens alsnog iets zegt zoals “Ik heb het geprobeerd, maar het werkt nog steeds niet!” of “Ik heb het veranderd, maar dat had geen zin”. Of nog erger, de persoon die geholpen wordt verandert tussendoor nog andere zaken en probeert in het wilde weg dingen zonder dat de helper hier iets vanaf weet.

De truc zit hem in het makkelijk maken voor de helper om jou te helpen. Dat betekent dat je **precies** moet aangeven wat je hebt gedaan tijdens het opvolgen van hun tips, en absoluut niet extra dingen moet uitvoeren of veranderen zonder dit door te geven. Mensen kunnen niet met je meekijken of gedachtenlezen en zijn dus compleet afhankelijk van de informatie die jij ze geeft.

---

# Tip 4: Beantwoord alle vragen

```irc
22:49:40 <Sling> INeedHelp: Ik heb wat meer informatie nodig, welke Apache, PHP en mod_security versie gebruik je?
22:52:50 <INeedHelp> Ik heb de laatste versie van Apache, dus daar kan het echt niet aan liggen! Wat moet ik doen?
22:53:20 <Sling> Welke versies precies?
22:53:20 <INeedHelp> De laatste, 2.4.9
22:53:20 <Sling> Ok.. en van PHP en mod_security?
```

Heel zelden is een vraag, hoe compleet deze ook is, met 1 antwoord op te lossen. Vaak moeten er eerst over en weer vragen worden gesteld om duidelijk te krijgen wat je precies wil, en welke oplossing er past bij je probleem. Hou daarom je aandacht bij hetgeen er gezegd wordt en geef een antwoord op alle vragen die je krijgt. Wacht hierbij niet te lang, de persoon die je de vraag stelt zal niet eindeloos op je antwoord blijven wachten.

Soms bevat een vraag meerdere kleine vragen. Vergeet niet om elk onderdeel van de vraag te beantwoorden, de informatie wordt niet voor niets gevraagd en als je telkens maar een deel beantwoordt maak je het je helpers alleen maar moeilijker om je probleem op te lossen.

---

# Tip 5: Lees het /topic

De meeste supportkanalen op IRC hebben een topic wat ingesteld is door een van de operators in het kanaal. Hier staat nuttige informatie in dus lees dit voordat je je vraag stelt! Soms wordt er na het join’en van het kanaal ook op andere manieren informatie getoond, negeer dit niet.

Dit soort informatie kan bijvoorbeeld aangeven hoe je het beste hulp kan krijgen, en het geeft soms URL’s naar handige pagina’s of regels van het kanaal. Als je eerste vraag beantwoord had kunnen worden door het topic te lezen, maakt dit niet bepaald een goede eerste indruk.

---

# Tip 6: Blijf beleefd en respectvol

Als je je vraag stelt in een kanaal of op een mailinglist, dan wordt dit gelezen door tientallen tot soms wel honderden of duizenden mensen. De personen die je doorgaans hulp aanbieden, zullen waarschijnlijk al jaren in het betreffende kanaal zitten en hebben misschien al duizenden vragen beantwoord. Ga er vanuit dat de vragen en/of opmerkingen die je krijgt terecht zijn, en twijfel niet meteen aan de deskundigheid of goede bedoelingen van de persoon die je probeert te helpen.

---

# Tip 7: Heb geduld

```irc
22:48:50 * INeedHelp joins #helpdesk
22:48:57 <INeedHelp> Hoi! Ik ben bezig met PHP en ik krijg de hele tijd deze error http://pas.te/SDsda8s, wat moet ik doen?
22:50:04 <Sling> INeedHelp: Ik ben zo terug en dan kijk ik naar je probleem, ok?
22:50:30 <INeedHelp> Pff, het is heel dringend, help me NU!
```

Tenzij anders aangegeven, is iedereen die jou op IRC probeert te helpen een vrijwilliger. Je kan dus niet verwachten dat deze persoon alle kennis in huis heeft om je te helpen, of beschikbaar blijft totdat jouw probleem is opgelost. Net als iedereen zijn ook de helpers in een kanaal vrij om op elk moment weg te lopen van hun computer of iets anders te gaan doen dan jouw vraag beantwoorden.


```irc
22:48:50 * INeedHelp joins #helpdesk
22:48:57 <INeedHelp> Hoi! Ik ben bezig met PHP en ik krijg de hele tijd deze error http://pas.te/SDsda8s, wat moet ik doen?
22:49:59 * INeedHelp leaves the channel
22:50:04 <Sling> INeedHelp: wat voor versie- oh te laat..
```

Zelfs als je haast hebt heeft het geen zin om je vraag te stellen en een minuut later het kanaal weer te verlaten. Niet overal zitten zoveel actieve mensen dat je de tekst voorbij ziet stromen zodra je een kanaal binnentreedt. In de meeste kanalen kan het enkele minuten duren voordat er iemand op je vraag reageert, wachttijden van 10 tot 20 minuten zijn niet zeldzaam.

Het heeft ook geen zin om je vraag te blijven herhalen, tenzij er veel tussendoor gepraat wordt en er nog niemand op je gereageerd heeft. Maar ook in dat geval, herhaal je vraag niet vaker dan eens in de zoveel minuten en na enkele pogingen is het misschien beter om het een paar uur later nog eens te proberen of je antwoord op een andere manier te zoeken.

---

# Tip 8: Stuur niet zomaar privéberichten

Stel je vraag in een kanaal en niet zomaar aan iemand via een privébericht (op IRC: query). Ten eerste is het onbeleefd om zomaar ongevraagd een query te sturen, ten tweede eis je in feite iemand zijn tijd volledig op voor jouw probleem, en ten slotte is het veel nuttiger om je vraag in het kanaal te behandelen zodat er meer mensen kunnen meehelpen en misschien er wel iets van opsteken door mee te lezen.

Als je liever bepaalde zaken niet in een publiek kanaal zet, probeer het dan dusdanig te censureren zodat je alsnog goed te helpen bent. Vervang een domeinnaam bijvoorbeeld met ‘example.com’. Als dit niet mogelijk is en je toch informatie moet geven die je liever niet publiek maakt, dan zou je je moeten afvragen of je dit überhaupt wel via IRC wil troubleshooten.

---

# Tip 9: Voel je niet aangevallen

Soms lijken de antwoorden die op IRC gegeven worden erg kortaf, bijvoorbeeld “Download de apr-libs”, “Herstart Apache”, “Lees hoofdstuk 4 van de handleiding”. In een gesprek zou het inderdaad iets te kortaf zijn, maar op IRC is dit niet onbeleefd of als aanval bedoeld. De vriendelijke en sociale tussenzinnen, toevoegsels en andere beleefdheidsvormen die er in een echt gesprek vaak omheen gezegd worden, zijn weggelaten om effectiever te communiceren. Je vraag is misschien al 100 keer eerder beantwoord dus de mensen die je helpen zullen steeds minder geneigd zijn om er uitbundig over te praten. Dit scheelt tijd, moeite, voorkomt vaak ook nog eens misverstanden maar is zeker niet onbeleefd bedoeld.

---

# Tip 10: Gebruik Engels

In bijna alle grote support IRC-kanalen is Engels de voertaal. Als dit niet het geval is, dan wordt dit vaak in het topic aangegeven. Praat daarom ook Engels, ook al is je Engels niet je beste voertaal. De mensen in het kanaal zijn ook niet allemaal Engelssprekend van origine en zijn gewend om te communiceren met mensen die geen perfect Engels beheersen.

Als er mensen een andere taal gaan spreken kan de rest van het kanaal dit niet meer volgen, dit wordt als onbeleefd beschouwd. Wanneer iemand je aanbied om in het Nederlands (of een andere taal) te helpen, doe dit dan liever in een query.

---

# Tip 11: Lees documentatie

Veel hackers lezen van nature geen handleidingen en gaan vaak meteen aan de slag. Meestal gaat dit goed, maar er zijn natuurlijk uitzonderingen. Als er dus wordt aangegeven dat je een stuk documentatie moet lezen om je probleem op te lossen, wees dan niet lui door te blijven vragen om een kant-en-klare oplossing, maar lees die documentatie. Als je zulke instructies niet kan opvolgen dan zal je snel merken dat niemand je meer wil helpen.

Als je niet weet waar de documentatie te vinden is, en er staan ook geen links in het topic, dan is het natuurlijk geen enkel probleem om hiernaar te vragen, hiermee toon je in ieder geval interesse om je te verdiepen in het onderwerp of product waar je ondersteuning voor wil krijgen.

Het kan voorkomen dat je niet alles snapt wat in de documentatie staat, en hierover een vraag wilt stellen. Doe ook dit zo gedetailleerd mogelijk en beschrijf precies waar het onderdeel staat wat je niet snapt en wat de vraag is die je wilde beantwoorden met de informatie uit de handleiding. Soms zorgt jouw vraag ervoor dat de schrijvers van de documentatie aanpassingen kunnen doen waardoor toekomstige lezers er ook wijzer van worden.

---

# Tip 12: Blijf nog even hangen 

Technische support op IRC zou niet bestaan als iedereen direct na zijn vraag weer het kanaal verlaat. Probeer dus ook nadat je vraag beantwoord is te blijven rondhangen in het kanaal. Je kan op die manier leren van de vragen van anderen en op termijn zelfs nieuwe mensen helpen met hun problemen. Ook ontmoet je op die manier (virtueel) nieuwe mensen.

---

# Tip 13: Leg uit hoe je het opgelost hebt

Ook al heb je er zelf niet zoveel aan, het is wel zo netjes om de oplossing ook met de rest van het kanaal te delen. Zomaar het kanaal verlaten met de melding “Nevermind, ik heb het al opgelost” wordt je niet in dank afgenomen. Ook al is de oplossing nog zo stom, deel hem met je helpers. Ook helpt het voor mensen die meelezen en in de toekomst een zelfde soort probleem tegenkomen.

---

# Tip 14: Vertrouw niet iedereen

Net als op alle andere plekken zitten er op IRC ook mensen met slechte bedoelingen. Soms willen deze mensen je helpen door met teamviewer of iets dergelijks je desktop over te nemen, of willen ze veel meer informatie over je systeem dan nodig is voor de oplossing van je probleem. Wees bedacht op dit soort situaties en hou er rekening mee dat de mensen waarmee je praat eigenlijk complete onbekenden zijn waar je niets over weet.

---

# Tip 15: Gebruik een pastebin bij het delen van veel tekst

Soms wordt je gevraagd om een deel van een bestand te laten zien of moet je meerdere regels uit een logbestand copy-pasten. Als je dit direct in het kanaal plakt dan krijgt iedereen ineens deze lap tekst in zijn scherm en worden andere gesprekken die tegelijk met jouw gesprek liepen onderbroken.

Om dit op te lossen kun je een pastebin gebruiken. Dat zijn websites waar je een lap tekst kan invoeren die vervolgens via een unieke URL te bereiken is. Deze URL plak je dan in het kanaal zodat de mensen die je aan het helpen zijn deze link kunnen volgen en de informatie zien die ze wilden hebben. Een voorbeeld van een dergelijke pastebin site [paste2.org](https://paste2.org). De bekendste pastebin is [pastebin.com](https://pastebin.com) maar deze kun je beter niet gebruiken omdat er reclame wordt getoond, en soms captcha’s moeten worden ingevuld om de informatie te bekijken. Daarnaast is deze site ook regelmatig down of erg traag.

Hackenkunjeleren heeft ook een [eigen pastebin](https://hackenkunjeleren.nl/pastebin) die je mag gebruiken.

---

# Meer bronnen over dit onderwerp:

- [How To Ask Questions The Smart Way](http://www.catb.org/esr/faqs/smart-questions.html)
- [Mikeash.com: Getting Answers](http://www.mikeash.com/getting_answers.html)
- [Getting help on IRC](https://workaround.org/getting-help-on-irc)
- [Help Vampires: A Spotter’s Guide](http://slash7.com/2006/12/22/vampires/)
- [What have you tried?](http://mattgemmell.com/what-have-you-tried/)
- [Freenode Philosophy: Channel Guidelines](http://freenode.net/channel_guidelines.shtml)