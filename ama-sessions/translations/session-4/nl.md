# AMA technische sessie #4
**Dag:** donderdag 21/12/2017 van 15u tot 17u  
**Mentoren:** Paul en Faiz Malkani

**Het zou leuk zijn om, naast de voorbeelden in de lessen, code-uitdagingen te krijgen om meer mogelijkheden te hebben om de concepten beter te begrijpen of zelfs om meer oefeningen of voorbeelden te hebben om ons te helpen de nieuwe concepten te onthouden. Heb je ooit gedacht om zoiets te creëren?**


Hey, Udacity gaat over het voorbereiden van je carrière in Mobile Web, en als zodanig zijn de lessen, quizzen en projecten in de cursus zelf een generieke set van problemen om je het beste op weg te helpen. Er zijn een heleboel specifiekere en meteen beschikbare problemen te vinden en de cursus geeft je de basis om die op te lossen. Uiteraard kan je deze suggestie altijd indienen mocht je het een waardevolle aanvulling vinden op de cursus.


**Waarom is de lifecycle van de service worker zo vreemd? Is het voor een service worker mogelijk om volledige controle te nemen over alle pagina's in mijn browser?**


Het is inderdaad raar. Gelukkig genoeg is dit wel het meest complexe onderdeel van het bouwen van een mobiele webapp. Eens je dit onder de knie hebt, is de rest makkelijk. Google heeft een fantastisch schema van de levenscyclus, die je gemakkelijk kan vinden door te zoeken naar *service worker lifecycle* die het hele proces op een nauwkeurige en gemakkelijk te begrijpen manier toont. Wat betreft je vraag, de service worker neemt niet de controle over alle pagina's van je browser, enkel die van je webapp.


**Ik denk dat deze vraag op de een of andere manier technisch is, dus ik zou ze je willen stellen: worden alle bezoeken aan elke les en de bijbehorende tijden geregistreerd of alleen het laatste bezoek? Gewoon om zeker te zijn.**


Hey, als je je afvraagt of Udacity al je lesbezoeken logt, dan is dat voor Udacity een weetje en bijft het voor jou een vraag.


**De cursus vereist basiskennis over node.js en relevante frameworks, maar het framework voor het gebruik van service workers wordt niet duidelijk uitgelegd in de cursus. Dat maakt dat de quizzen kunnen worden gemaakt, maar je niet weet waar te starten wanneer je echt wil ontwikkelen vanaf het begin. Is het omdat we geacht worden dit niveau al te hebben? Met welke frameworks moeten we vertrouwd zijn als we service workers willen implementeren op onze websites?**


De enige voorwaarden voor de implementatie van service workers zijn HTML, CSS en JavaScript. Je kan er voor kiezen om gebruik te maken van frameworks om bepaalde taken te vereenvoudigen, maar je hebt alleen die drie basiscomponenten nodig om te beginnen, met een zwaardere focus op JavaScript. Maar als je denkt dat de cursus tot verwarring leidt, zou ik je zeker aanbevelen om een suggestie te sturen.


**Heb je suggesties voor app-ideeën om het ontwikkelen van PWA te oefenen? En hebben jullie plannen voor evenementen zoals online hackathons of live codingsessies? Ik ben bijna klaar met het cursusmateriaal en ik wil graag meer oefensessies krijgen als dat mogelijk is.**


De repositories https://github.com/code-kotis/awesome-pwa-ideas2 en http://pwa.rocks2 hebben een fantastische set aan oefenideeën die je kan gebruiken om je vaardigheden te verbeteren. Wat hackathons en live coding betreft kan ik niet praten over toekomstplannen. Ik adviseer om Udacity in eerste instantie te gebruiken als leermiddel en vervolgens je ideeën om te zetten in echte webapps als oefening.


**De onderdelen service worker en IndexedDB and Caching zouden bijlagen met schema's en functiecalls moeten bevatten.**


Klinkt als een geweldig idee. Ik stel voor dat je het indient als suggestie bij deze cursus zodat het team bij Udacity het kan bekijken.


**Veel relevante mensen uit de webdev-wereld, zoals @jaffathecake bijvoorbeeld, berichtten gisteren over het standaard opnemen van service workers in Safari. Kan je ons meer vertellen over hoe het de gebruikerservaring verandert wanneer SW standaard wordt?**


Het standaard hebben van service workers in Safari zal de gebruikerservaring en ontwikkelingservaring aanzienlijk verbeteren. PWA's kunnen nu probleemloos op alle belangrijke platforms worden geïmplementeerd, wat minder ontwikkeling en minder bugs betekent.


**Welke updatestrategie zou je met betrekking tot service workers aanbevelen? Ik heb behoorlijk wat gelezen over dit onderwerp, maar ik ben nog steeds onzeker, het lijkt erop dat als een update eenmaal is gedetecteerd, een gebruiker zijn browser moet vernieuwen om de update te zien, kunnen we deze vernieuwing dan vermijden?**


De update van een service worker wordt geactiveerd als de nieuwe service worker een andere hash heeft (zelfs als een byte wordt gewijzigd) en negeert een browser cache van ouder dan 24 uur. Het kan vermeden worden door niet te vaak van remote service worker te veranderen en alleen incrementele updates te pushen in plaats van kleine, frequente updates.


**Voor zover ik begrijp leeft de service worker langs de clientzijde, wat maakt dat iedereen kwaadwillige code kan injecteren in elke website zonder dat de gebruiker daarvan op de hoogte is, is dit de reden waarom https vereist is. Dit betekent dat als https gecompromitteerd wordt, we gedoemd zijn te mislukken? Hoe zit het met een aanval op https, KRACK bijvoorbeeld, is er een verdedigingsmechanisme voor de service worker?**


Veiligheid is altijd belangrijk. Dit is een beetje te technisch, maar ik kan wel zeggen dat de service worker veilig is met https encryptie.


**Hoe kunnen we deze cursus het beste benutten en kunnen we één op één ondersteuning krijgen van de cursusinstructeurs, als dat zo is, hoe kunnen we dan in contact komen? Bedankt.**


De beste manier waarop je deze cursus kan gebruiken is door alle taken tijdig uit te voeren en je kennis in praktijk te brengen als je planning dat toelaat. Coderen leer je het beste door te doen. Wat de mentorhulp betreft, zijn de discussieforums de beste plaats om te kijken


**Het 2e deel van de cursus zal gaan over hoe een web app te bouwen?**


Het tweede deel heeft een app bouwproces in drie fasen en is super opwindend.


**Welke versies van node en npm zijn optimaal voor de cursussen?**


De nieuwste stabiele versies zouden goed moeten zijn. Ik zou afraden om een bèta of niet-stabiele versie te gebruiken, omdat die meestal nog een paar bugs te bevatten.


**Mijn tweede vraag is, de meeste tijd en moeite wordt gestopt in het leren over google dev tool, service workers en IndexedDB en es5&6. Hoe zal dat van pas komen?**


PWA's verspreiden snel en worden de nieuwe trend voor producten die geen volledige native app download nodig hebben. Leren hoe het hele ecosysteem van mobiele webapps in elkaar zit helpt je je basis te versterken en bereidt je voor op een carrière met een sterke basis en inzicht in het proces.


**Wanneer is het juiste moment om een sw hulpbibliotheek te gebruiken zoals een workbox?**


Eens je een goed inzicht hebt in wat een bibliotheek doet en hoe ze werkt, kan je ze gebruiken om de code van de boilerplate die je schrijft te verminderen en je te concentreren op het bouwen van de app zelf. Ik raad wel aan om bibliotheken te gebruiken om je werk te vereenvoudigen en te versnellen, en niet om de hiaten in je kennis op te vullen.


**De scholarship noemt Mobile Web Challenge, maar in hoeverre kunnen we de kennis implementeren bij het bouwen van een "mobiele app" (d.w.z. iOS en android apps)?**


Wat je in de cursus leert helpt je niet verder bij het ontwikkelen van andere pure native apps, tenzij voor basisprincipes zoals caching en update, maar het materiaal zal je leerproces van het bouwen van hybride apps, dat wil zeggen webapps in een native wrapper, aanzienlijk vereenvoudigen. Frameworks als Ionic en ReactNative zijn in opkomst en kunnen een native ervaring bieden aan de eindgebruiker.


**Ik bouw mobiele apps met behulp van Ionic framework en Angular, in hoeverre zal deze cursus voor mij nuttig zijn? Is het echt toepasbaar en gemakkelijk te gebruiken voor mobiele apps in Ionic framework?**


Angular neemt heel wat zware taken voor zijn rekening wanneer je het gebruikt om native apps met Ionic te bouwen. De cursus zal zeker helpen, door je de basis te leren waarop Angular is gebouwd, waardoor je een beter inzicht krijgt in hoe dingen werken en waardoor je problemen sneller en gemakkelijker kan oplossen.


**De cursus is in principe verdeeld in twee delen: de eerste IDB + SW en de tweede ES6. Brengt de tweede fase beide samen? of er is geen verband.**


Het tweede deel van de cursus gaat over het toepassen van je kennis van het eerste deel om in drie fasen een restaurant app te bouwen. Het is ook super spannend.


**Is er iets in het bijzonder waar ik aan moet denken bij het implementeren van een PWA met offline eerst in een isomorfe React app? Of er is geen echt verschil**


Geen echt verschil, alle technologieën zoals service worker, cache en IndexedDB werken omdat je de PWA in een container verpakt die die niet beïnvloedt.


**Waarom wordt InedexedDB geleerd om samen gebruikt te worden met service workers, terwijl de cursus zegt dat de API ervan slecht is? Is er een aanbevolen alternatief?**


Ik zou niet zeggen dat IndexedDB slecht is, alleen dat er ruimte voor verbetering is. De idb-bibliotheek die werd gelinkt (https://github.com/jakearchibald/idb) voegt promises toe, een erg gewenste feature, en is een goede optie om te gebruiken.


**Ik heb een vraag over IndexedDB is er een manier om te weten wat de opslaglimiet is of om de totale grootte van je IndexedDB te krijgen?**


Opslag is niet onbeperkt en er zijn geen API's om de grootte van IndexedDB te controleren, maar Chrome en Firefox hebben wel iets dergelijks in de pijplijn. Tot die tijd stel ik voor deze fantastische post te lezen over het handmatig berekenen van de grootte: http://www.andygup.net/calculate-size-of-indexeddb-database/


**Hi jongens, ik heb een vraag over offline eerst. Als ik een Offline First Mobile Application wil, geen PWA maar een hybride applicatie met Ionic, kan ik dan gebruik maken van service worker, cache en IndexedDB? of alleen voor PWA? En wat gebeurt er als de app native mobiele applicatie wordt? Bedankt allemaal!**


Natuurlijk kan je gebruik maken van service worker, IndexedDB en cache. Ionic is puur een wrapper voor een webapp in een native container, en het wrappen verandert niets aan de webapp zelf.


**In de industrie is een belangrijke metric de performance en opstartsnelheid, is er een audittest, zoals Lighthouse die je aanbeveelt om onze toepassingen te testen en te verbeteren?**


Lighthouse is de beste en meest uitgebreide web-app testing tool, maar je kan meer mainstream varianten proberen zoals JMeter, Capybara en Selenium.


**Promises zijn net als andere nieuwe dingen die in sommige browsers mogelijk niet worden ondersteund. Behandelt de idb-bibliotheek dit probleem of moet ik altijd een transpiler gebruiken?**


idb voegt alleen de promises functionaliteit toe aan IndexedDB en je moet dus zeker een transpiler gebruiken


**Ik heb een vraag die relevant is voor SPA. Nu is het populair om server side rendering van de pagina's te doen. Hoe werkt dat met service workers? Het lijkt erop alsof sw alle requests onder controle moet hebben. Maar in SSR kunnen we in plaats van enkele requests te doen, de content genereren op de server. En dan cachet sw deze html en geeft de volgende keer altijd verouderde gegevens terug. Dus ik ben niet echt zeker, zijn ssr en sw vrienden?**


Fantastische vraag, maar iets te technisch voor de AMA die gericht is op de problemen binnen deze cursus. Kort antwoord, ja ze zijn vrienden, goede vrienden, en ze kunnen naast elkaar worden gebruikt.


**Moeten we de integrity tag toevoegen aan de service worker scripts en andere scripts?**


Hieromtrent vindt er een buitengewoon interessante discussie plaats op dit moment. De vraag stelt zich of op beveiliging kan worden bespaard om aan prestatie te winnen. Je zou die zeker moeten volgen op https://github.com/w3c/webappsec-subresource-integrity/issues/26


**Is het gebruik van clients.claim() bij een service worker een goede praktijk?**


Als je de service worker gebruikt om pagina's anders te laden dan ze via het netwerk zouden laden, kan clients.claim() problematisch zijn, aangezien de service worker dan de controle kan krijgen over sommige clients die zonder geladen werden.


**Met een overvloed van frameworks zoals React of Angular of Vue zijn, hoe belangrijk is het om mvc of mvo te leren met vanilla js?**


MVC in vanilla js is enigszins intimiderend omdat het framework niet te scheiden valt van de design patronen. Moderne frameworks komen met hun eigen interpretatie van MVC, en ik stel voor om te proberen begrijpen hoe de patronen werken en waarop ze gericht zijn (de oplossing scheidbaar maken) en vervolgens de versie ervan te gebruiken die je framework nodig heeft.


**Ik heb gelezen dat handlebars in het template moeten worden omgeven door een script tag, maar ik zie in je templates folder dat er geen omliggende script tag is en dat vind ik verwarrend, is de script tag optioneel of wordt die behandeld op een andere plaats in het Wittr project (ik bedoel ergens behandeld in het algemeen)?**


Ik zou moeten kijken naar de broncode van Wittr om dit te kunnen beantwoorden, dus misschien valt dit buiten het bereik van de AMA. Misschien kan ik hieromtrent later nog eens bij je terecht?
