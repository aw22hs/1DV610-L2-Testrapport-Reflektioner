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
| Metodnamn på en metod som sorterar alla ord efter hur ofta de förekommer i texten | Det är inte helt tydligt om metoden endast sorterar orden efter hur ofta de förekommer i texten eller om de även returneras, vilket de gör i detta fall. |
| | **Use Searchable Names** |
| | Metoden har ett långt namn, men det gör den mer sökbar istället för att t ex döpa den till ```countWrdFreqAlphOrder()```. |
| | **Pick One Word per Concept** |
| | Jag använder både ```count``` och ```get``` i olika metodnamn där metoden returnerar ett uträknat värde. Jag borde använda ```get``` istället om metoden returnerar ett värde. Denna metod borde heta ```getWordCountAlphabeticalOrder()```. |
| **getLetterCountDifferenceBetweenOriginalAndUpdatedText()** | **Avoid Disinformation** |
| Metodnamn på en metod som returnerar en sträng som förklarar skillnaden mellan original texten och den eventuella texten som har blivit ändrad | På metodnamnet låter det som att det kommer att returneras en siffra, men det returneras en sträng. Det blir otydligt för användaren av modulen. |
| | **Use Pronounceable Names** |
| | Metodnamnet går att enkelt att uttala till skillnad t ex ```getLtrCntDiffBtwnOrigAndUpdText()```. |
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
| **getLetterCountDifferenceBetweenOriginalAndUpdatedText()** | 21 | **Small!** |
| | | En funktion ska vara liten och en if-sats borde bara ha en rad med kod i sig, förslagsvis bestående av ett funktionsanrop. I denna funktion finns en if-sats som har ytterligare en if-sats inuti sig. Den inre if-satsen behöver inte ligger inuti den ytter if-satsen. |
| | | **Do One Thing** |
| | | Denna funktion har många retursatser och göra många saker. Den kan göras om till tre funktioner. En funktion som heter ```isOriginalTextAndUpdatedTextSame()``` som returnerar en boolean. En funktion som heter ```isUpdatedText()``` som kontrollerar om något ord har blivit utbytt (this.#updatedTextWithReplacedWords existerar) och returnerar en boolean. Sen går det att ha behålla namnet på denna funktion och göra så att den returnerar den faktiska längdskillnaden som ett nummer och då t ex alltid säga hur många tecken längre eller kortare originaltexten är jämfört med den uppdaterade texten. |
| countNotEmptyLines 11 | | |
| countNonEmptyLinesWithoutJSComments 11 | | |
| replaceWordsWithTwoDifferentFormattings | | |
| replaceWordsWithExactFormatting | | |
| #countAndSortInAlphabeticalOrder 19 | | |