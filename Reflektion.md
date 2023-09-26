# Reflektion
I detta dokument reflekterar jag kring hur jag har applicerat kunskapen från kapitel 2 och 3 i utvecklandet av min modul. Jag tar upp både saker som jag är nöjd med och saker som jag kunde ha gjort annorlunda.

## Kapitel 2 - Namngivning

| **Namn och förklaring** | **Reflektion** |
|---------------------|----------|
| **averageNumberOfSentencesPerParagraph()** | **Method Names** |
| Metodnamn på en metod som räknar ut och returnerar genomsnittligt antal meningar per paragraph. | Metodnamn ska innehålla eller vara verb som förklarar vad metoden gör, vilket detta metodnamn saknar. Borde ha hetat ```get``` eller ```count``` i början av metodnamnet. |
| | **Don't Pun** |
| | Alla mina variabelnamn och metodnamn är skapade för att vara så tydliga och enkla som möjligt, det finns ingen "humor" eller internt lingo i min namngivning. |
| **countWordsFrequencyAlphabeticalOrder()** | **Use Intention-Revealing Names** | 
| Metodnamn på en metod som sorterar alla ord efter hur ofta de förekommer i texten | Det är inte helt tydligt att metoden både sorterar orden efter hur ofta de förekommer i texten samt returnerar resultatet. |
| | **Use Searchable Names** |
| | Metoden har ett långt namn, men det gör den mer sökbar istället för att t ex döpa den till ```countWrdFreqAlphOrder()```. |
| | **Pick One Word per Concept** |
| | Jag använder både ```count``` och ```get``` i olika metodnamn där metoden returnerar ett uträknat värde. Jag borde använda ```get``` istället om metoden returnerar ett värde. Denna metod borde heta ```getWordCountAlphabeticalOrder()```. |
| **getLetterCountDifferenceBetweenOriginalAndUpdatedText()** | **Avoid Disinformation** |
| Metodnamn på en metod som returnerar en sträng som förklarar skillnaden mellan original texten och den eventuella texten som har blivit ändrad | På metodnamnet låter det som att det kommer att returneras en siffra, men det returneras en sträng. Det blir otydligt för användaren av modulen. |
| | **Use Pronounceable Names** |
| | Metodnamnet går att enkelt att uttala till skillnad från t ex ```getLtrCntDiffBtwnOrigAndUpdText()```. |
| **replaceWordsWithTwoDifferentFormattings(wordToReplace, newWord)** | **Use Intention-Revealing Names** |
| Metodnamn på en metod som ersätter alla ord som har någon av två olika formateringar | Metodnamnet är tydligt med att det ersätter ord. Däremot är det otydligt vilka formateringar som ersätts. Borde kanske ha delats upp till fler funktioner för att kunna göra namnet tydligare. |
| | **Add Meaningful Context** |
| | Parametrarna heter ```wordToReplace``` och ```newWord``` istället för att ta något mindre tydligt som ```word1``` och ```word2```. Detta återspeglar sig sen genom hur variabelnamnen fortsätter att utvecklas inuti metoden, se nedan. |
| **wordToReplaceWithAllLettersLowerCase**, **wordToReplaceWithFirstLetterUpperCase**, **newWordWithAllLettersLowerCase**, **newWordWithFirstLetterUpperCase** | **Make Meaningful Distinctions** |
| Variabelnamn i metoden replaceWordsWithTwoDifferentFormattings() | I stället för att endast döpa variablerna till ```wordToReplace1``` och ```wordToReplace2``` osv gav jag variablerna långa deskriptiva namn så att det ska bli lättare att särskilja dem. Eftersom jag applicerade samma mönster på ```wordToReplace``` och ```newWord``` lät jag ```wordToReplace``` och ```newWord``` står kvar i början av variabelnamnen. |
| | **Don’t Add Gratuitous Context** |
| | Det är långa variabelnamn och det skulle eventuellt gå att ta bort ```With``` mitt i namnen, men i övrigt tycker jag att all information i namnen är motiverade. |
| | **Avoid Mental Mapping** |
| | Mina namnval är tydliga för att det ska vara enkelt att följa med i koden, både under utvecklingen av koden och när den senare läses av någon annan. Användaren ska inte behöva komma ihåg vad en variabel betyder. |  

### Reflektioner kring kapitel 2  
Kapitel 2 var intressant och gav upphov till en del funderingar. En av avvägningarna som dök upp är vad som väger tyngst - att ha korta namn eller att ha långa, mer deskriptiva namn. Att skriva långa, mer deskriptiva namn har sina fördelar då det på vissa sätt blir lättare att dyka in i koden vid ett senare tillfälle och snabbt kunna sätta sig in i vad ett visst kodavsnitt betyder. Det blir en typ av dokumentation och gör att vi slipper skriva (lika mycket) kommentarer - koden blir självförklarande. Det finns dock en risk att många långa namn gör det svårare att snabbt få en överblick av koden, speciellt om flera långa variabel- eller metodnamn har subtila skillnader, som Robert C Martin skriver.

Att ha metodnamn som går att uttala är också en ny tanke. Under utbildningen har jag till största delen skrivit kod ensam, eller åtminstone inte delat min kod med någon annan. Därför har behovet av att uttala namnet på mina metoder och variabler inte uppstått tidigare, men när jag läste om det i boken kändes det som en självklarhet att vi även måste kunna tala om och uttala vår kod.

Jag tycker att jag själv har varit konsekvent i min namngivning i tidigare kurser, men då har vi ofta haft en boilerplate att utgå från som har satt riktlinjer för hur metoder ska döpas. I detta fall, då jag började med en tom modul, var det svårare. Det blev lite spretigt och jag märkte själv att jag inte var helt konsekvent när jag använde t ex count och get.

Tidigare har jag givetvis lagt tid på att försöka hitta ett bra namn, men kanske ändå inte tänkt på hur viktigt det är när andra ska granska och/eller använda ens kod. Boken underströk vikten av bra namn och att det inte är fel att gå tillbaka och byta namn senare för att det ska bli ännu tydligare. Bra kod är kod som andra och en själv förstår.

## Kapitel 3 - Funktioner

| Metodnamn och länk eller kod | Antal rader | Reflektion |
|------------------------------|-------------|------------|
| **replaceWordsWithTwoDifferentFormattings(wordToReplace, newWord)** | 26 | **Don’t Repeat Yourself** |
| | | I denna metod repeteras kod där både ```wordToReplace``` och ```newWord``` görs om till olika format och sen läggs in i en array. Detta hade kunnat göras via en egen metod som returnerar en array istället. |
| | | **Function Arguments** |
| | | Metoden har två argument (dyadic), vilket bör undvikas enligt boken. Jag hade kunnat skapa klassen ```Word``` och anropa två instanser av den istället, men har valt att behålla metoden på detta sätt. |
| **getLetterCountDifferenceBetweenOriginalAndUpdatedText()** | 21 | **Small!** |
| | | En funktion ska vara liten och en if-sats borde bara ha en rad med kod i sig, förslagsvis bestående av ett funktionsanrop. I denna funktion finns en if-sats som har ytterligare en if-sats inuti sig. Den inre if-satsen behöver inte ligger inuti den ytter if-satsen. Hela funktionen i sig kan även göras mindre, se nedan. |
| | | **Do One Thing** |
| | | Denna gör många saker. Den kan göras om till tre funktioner. En funktion som heter ```isOriginalTextAndUpdatedTextSame()``` som returnerar en boolean. En funktion som heter ```isUpdatedText()``` som kontrollerar om något ord har blivit utbytt (dvs ```this.#updatedTextWithReplacedWords``` existerar) och som returnerar en boolean. Sen går det att ha behålla namnet på denna funktion och göra så att den returnerar den faktiska längdskillnaden som ett nummer och då t ex alltid säga hur många tecken längre eller kortare originaltexten är jämfört med den uppdaterade texten. |
| | | **Structured Programming** |
| | | Enligt Edsger Dijkstra bör det endast finnas en väg ut ur en metod, dvs en retursats. Denna metod har fyra retursatser. |
| **countNotEmptyLines()** | 12 | **Use Descriptive Names** |
| | | Beskriver tydligt att den räknar alla rader som inte är tomma. Borde däremot ha hetat ```getNotEmptyLinesCount```. |
| | | **Reading Code from Top to Bottom: The Stepdown Rule** |
| | | Eftersom vissa av mina metoder anropar samma metod är det inte möjligt att göra koden läsbar "from top to bottom". Jag har därför valt att lägga de publika metoderna överst i bokstavsordning och därefter de privata metoderna i bokstavsordning. |
| | | **Function Arguments** |
| | | Genom att använda det privata fältet ```this.#trimmedLines``` behöver inga argument användas i metoden (niladic). |
| **countNonEmptyLinesWithoutJSComments()** | 12 | **Use Descriptive Names** |
| | | Lite otydligt vad ```JSComments``` betyder. Metoden riktar sig inte heller specifikt mot JavaScript-kommentarer, utan räknar alla rader som inte är tomma samt rader inte som börjar med tecknen * eller /. Hade behövt delas upp i flera metoder för att kunna få bättre namn, men med relativt få kodrader känns det överflödigt. |
| | | **One Level of Abstraction per Function** |
| | | Denna metod har två olika abstraktionsnivåer då if-satsen under vissa förutsättningar gör ett metodanrop ```this.#trimmedLines``` och övriga rader kod i metoden är på en lägre abstraktionsnivå. |
| **countNotEmptyLines()** | 12 | **Don’t Repeat Yourself** |
| | | Denna metod gör i stort sett samma sak som ```**countNonEmptyLinesWithoutJSComments()**``` och går därför emot DRY-principen. Dessa två metoder bör istället anropa en tredje metod som tar emot respektive logiskt uttryck (vilket är det som skiljer de två metoderna åt) som ett argument. |
| | | **Have No Side Effects** |
| | | Om arrayen ```this.#trimmedLines``` är tom anropas metoden ```this.#splitTextIntoTrimmedLines()``` som fyller arrayen med element. Det är en sidoeffekt som inte framgår av något av metodnamnen. |

### Reflektioner kring kapitel 3  
Den största behållningen från kapitel 3 är att funktionerna ska vara små. Som junior utvecklare ställer jag mig dock försiktigt skeptisk till hur bokens exempel drar detta till sin spets. Jag kan se hur det är lättare att både översätta modulen till ett annat språk samt att det gör modulen enklare att expandera, men jag anser inte att koden blir mer lättläst. Flödet i läsandet av koden bli mindre läsbar då jag upplever att det är svårt att komma ihåg hur anropet började. Större metoder, i viss utsträckning, är därför att föredra enligt mig, men jag ser absolut att det finns en poäng i att inte skriva metoder som är alldeles för stora. Efter att ha gjort denna laboration kommer jag ta för vana att försöka skriva mindre metoder som riktar sig mer mot att göra en sak, men inte till varje pris.

Att inte blanda abstraktionsnivåer var något som jag inte hade tänkt på överhuvudtaget tidigare och där ställer jag mig också lite skeptisk, men då det går i linje med att en metod ska göra en sak kan jag köpa konceptet.

Att det däremot skulle vara mindre önskvärt att ta emot argument i en metod hade jag svårt att förstå från början. Jag skapade därför först en vanlig modul, men övergick sedan till att göra om den till en klass där jag kunde spara olika privata fält som mina metoder kunde anropa utan att behöva ta emot argument varje gång. Endast fyra av mina sjutton publika metoder tar emot argument, vilket jag är nöjd med. Jag håller även med om att inte ta emot argument underlättar testningen och att det inte finns en risk att argument skickas in i fel format eller fel ordning.

## Övergripande reflektion
Jag tycker att boken är väldigt intressant och pedagogiskt skriven. Det är även uppfriskande med en bok som har lite humor. 

Koncepten fån kapitel 2 kändes enklast att ta in, troligtvis eftersom namngivning är enklare att ”ta på” än funktioner. Som jag redan har skrivit håller jag inte helt med om författarens syn på exakt hur små funktioner ska vara. Däremot kommer dessa två kapitel ha inverkan på hur jag namnger och skriver framtida funktioner.

Eftersom jag hade läst i boken innan jag gjorde laborationen märkte jag att det som hade fastnat mest var att använda deskriptiva namn för både metoder och variabler samt att försöka skriva kortare metoder. Under reflektion av kodkvalitetskraven märkte jag dock att det fortfarande finns flera delar att arbeta vidare med, exempelvis *Use Intention-Revealing Names* och *Pick One Word per Concept*. Jag tycker även att det är svårt, och behöver lära mig mer kring, när det är rimligt att göra en metod mindre och när det blir kaka på kaka. En av mina privata metoder, ```getAndTrimSentences()```, har endast som uppgift att anropa två andra metoder, men eftersom dessa två metoder ska anropas i samma ordning från fyra andra metoder tog jag beslutet att göra ```getAndTrimSentences()``` till en metod. Det känns lite kaka på kaka, men det går i linje med DRY-principen.

Då min klass blev förhållandevis stor i förhållande till kravet på antal publika metoder övervägde jag att bryta ut någon del av koden till en egen klass. Ett alternativ hade varit att göra en ```CodeAnalyzer``` som höll metoden ```countNonEmptyLinesWithoutJSComments()``` där jag även hade kunnat skapa metoder som inriktade sig mer på att analysera kod.
 
