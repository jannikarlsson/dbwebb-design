---
---
Utvärdering av webbplatsers laddningstid
=======================

I den här uppgiften jämför jag tre webbplatsers laddningstid och undersöker vad de hade kunnat göra för att snabba upp webbplatsen.

Urval
-----------------------

I den här uppgiften har jag valt att jämföra tre webbplatser som säljer resor, eftersom jag föreställer mig att man måste använda mycket bilder och kanske även rörlig bild när man säljer den sortens upplevelse och att detta lätt kan bli tungt. För att jämförelsen ska bli så rättvis som möjligt har jag använt startsidan, en destinationssida och sista minuten-sidan hos alla tre. Bolagen jag har valt är Tui, Ving och Apollo.

Metod
-----------------------

Jag har mätt laddningstid med hjälp av DevTools i Google Chrome och använt mig av [Google PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights) i analysen.

[Här finns mina mätresultat i Google Kalkylark](https://docs.google.com/spreadsheets/d/16u8p9d_c4taY4MP6dmjFUOkVG-vxmO07ngVL6W-s2ZQ/edit?usp=sharing)

Resultat
-----------------------

#### Tui

[FIGURE src="image/tui.jpg"]

Undersökta sidor:

[Startsidan](https://www.tui.se/): Sidans laddningstid var 3,2 sekunder, 104 resurser om totalt 4 MB hämtades.

[Destinationssidan för Madeira](https://www.tui.se/resa/portugal/madeira/): Sidans laddningstid var 2,7 sekunder, 111 resurser om totalt 4,6 MB hämtades.

[Sista minuten-sidan](https://www.tui.se/erbjudanden/sista-minuten/): Sidans laddningstid var 2,2 sekunder, 96 resurser om totalt 3,3 MB hämtades.

Tuis startsida får betyget 92 för desktop och 57 för mobil i Google PageSpeed Insights. För desktop klarar den de flesta testen, och den åtgärd som ytterligare föreslås för att snabba upp laddningstiden är att minska storleken på JS-resurserna som skickas eftersom det är den laddningstiden som förlänger tiden till att användaren kan interagera med webbplatsen. Även i mobilläge klarar sidan många tester, men här är problemet med JS-resurserna ännu större. Rådet är att minska resursernas storlek för att minska tiden det tar att tolka, kompilera och köra koden.

Resultatet ser likvärdigt ut för startsidan och destinationssidan. Sista minuten-sidan sticker ur lite i resultatet, eftersom den för desktop klarar de flesta granskningarna och får totalbetyget 96. För mobil får den lägre, 68, men ändå högre än de andra testade sidorna hos Tui. Men även här är det storleken på JS-resurserna som de rekommenderas att se över.

#### Ving

[FIGURE src="image/ving.jpg"]

Undersökta sidor:

[Startsidan](https://www.ving.se/): Sidans laddningstid var 2,6 sekunder, 67 resurser om totalt 5,2 MB hämtades.

[Destinationssidan för Madeira](https://www.ving.se/portugal/madeira): Sidans laddningstid var 2,8 sekunder, 64 resurser om totalt 5,6 MB hämtades.

[Sista minuten-sidan](https://www.ving.se/sista-minuten): Sidans laddningstid var 2,9 sekunder, 49 resurser om totalt 4,5 MB hämtades.

Vings startsida får betyget 78 på desktop och bara 30 på mobil. Det som drar ner betyget är dels att JS-resurserna är stora och dels att sidan innehåller nästan 3000 DOM-element mot det rekommenderade taket på 1500, vilket kan öka minnesförbrukningen. För mobilversionen är ett annat problem tredjepartskod från bland andra Hotjar och Google Tag Manager som ökar laddningstiden. Detta är alltså skript som används för att analysera användarbeteenden.

Destinationssidan får ett liknande resultat, medan sista minuten-sidan även här sticker ut med betyget 93 för desktop. Den enda möjlighet som nämns som kan snabba upp sidan är att ta bort resurser som blockerar renderingen.

#### Apollo

[FIGURE src="image/apollo.jpg"]

Undersökta sidor:

[Startsidan](https://www.apollo.se/): Sidans laddningstid var 5,1 sekunder, 109 resurser om totalt 5,5 MB hämtades.

[Destinationssidan för Madeira](https://www.apollo.se/resor/europa/portugal/madeira): Sidans laddningstid var 4,7 sekunder, 99 resurser om totalt 6,5 MB hämtades.

[Sista minuten-sidan](https://www.apollo.se/sista-minuten): Sidans laddningstid var 2,6 sekunder, 70 resurser om totalt 4 MB hämtades.

Apollos startsida får betyget 93 för desktop, och här har alla problem med bilderna att göra. Rekommendationen är att använda rätt format och minska storleken, och även cachelagra en del bilder. För mobil är betyget bara 34, vilket även här främst har med bilderna att göra. Förslaget är att skjuta upp inläsningen av bilder som inte visas på skärmen, använda modernare bildformat och byta till rätt storlek. En annan rekommendation är att skicka textresurser komprimerade, vilket skulle spara mycket laddningstid. Även här tar inläsningen längre tid på grund av tredjepartskod.

För destinationssidan blir betyget bara 75 i desktop, vilket beror på tredjepartskod och att JS-koden tar lång tid att tolka, kompilera och köra. För sista minuten-sidan i desktopläge finns nästan inga förbättringsmöjligheter, resultatet 94 är ett av de bästa i testet, medan mobilversionen har samma problem som övriga sidor med tredjepartskod som blockerar och för stor arbetsbelastning på grund av JS-kod.

Analys
-----------------------

Mitt test visar att det allra största problemet för samtliga webbplatser i testet är att JS-resurserna är stora och tar tid att ladda, vilket gör att sidan är blockerad för interaktion i flera sekunder. Särskilt i mobilläget verkar detta ta onödigt lång tid.

Ett annat återkommande problem är tredjepartskod, där flera av de undersökta sidorna har en lång lista av analysverktyg och andra skript som ökar laddningstiden. Förhoppningsvis använder de analysverktygen tillräckligt för att göra användarupplevelsen bättre så att det väger upp för den ökade laddningstiden.

Till skillnad från vad jag trodde när jag gjorde mitt urval var bilder och video generellt inte ett stort problem på de analyserade sidorna. Det var bara en som fick förslaget att jobba mer med bildstorlekar för att minska laddningstiden, och övriga fick grönt ljus för sin bildhantering. Värt att nämna är dessutom att Apollo, som fick rekommendationer om bildhanteringen och har längst laddningstider, är den webbplats som vid en första anblick tycks ha minst bilder, medan de övriga i testet har jättebilder över hela sidan. Så det verkar absolut spela större roll hur man hanterar bilderna än mängden man har på sidan.

Testvinnare
-----------------------

Tui har marginellt längre laddningstider än Ving, men betydligt bättre testresultat i PageSpeed Insights, så jag utser dem till vinnare i testet. Apollo har riktigt dåligt resultat i mobiltestet, och dessutom längre laddningstider, så de tar hem jumbon.

Vad är en bra laddningstid?
-----------------------

För mig personligen tror jag att det beror lite på vad det är för en sida. Om jag känner till den och vet att det jag letar efter finns där kan jag tolerera lite längre laddningstid, till exempel min internetbank eller någon annan tjänst som jag vill använda. Men om jag googlar efter något och klickar in på en sida som jag aldrig har besökt vill jag att den ska ladda snabbare, annars kommer jag att lämna och gå till en annan innan den har laddat. Jag skulle säga att en sida som laddar på en eller två sekunder, alltså inte nödvändigtvis fullt ut men så pass att man kan börja läsa, är snabb. Uppåt fyra-fem sekunder börjar bli för långsamt, särskilt om det beror på reklam eller popupprutor.

Jag tycker att dessa webbplatser var mitt emellan snabba och långsamma, men om man går dit för att hitta inspiration till en resa så kanske man har mer tålamod med att bilder och effekter tar lite tid att ladda.

Referenser
-----------------------

[Google PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights)

Övrigt
-----------------------

Jag som har gjort analysen heter Janni Karlsson.
