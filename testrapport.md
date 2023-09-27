# Testrapport
I detta dokument redovisar jag för hur jag har utfört testningen av min modul. Längre ner i dokumentet reflekterar jag även kring kodkvalitet och hur jag har applicerat kunskapen från kapitel 2 och 3 vid utvecklandet av min modul. Jag tar upp både saker som jag är nöjd med och saker som jag kunde ha gjort annorlunda.

## Testspecifikation

Modulen har endast testats med automatiska tester. Testningen har utförts med Jest v29.7.0. För att kunna köra testerna har följande sträng angivits inuti ```scripts``` i package.json:
```
"test": "npx --node-options=--experimental-vm-modules jest --setupFiles"
```
För att starta testerna används således kommandot ```npm test```.  

Testerna består av en testsvit med totalt 94 deltester som är uppdelade enligt de 17 publika metoder som anropas av testerna, se nedan. Samtliga tester är godkända i v.1.0.0 av modulen.

I mappen 'testdata' finns två filer, exampleCode.js och loremIpsum.md. Innehållet i dessa filer används som argument vid skapandet av två olika instanser av modulen som används under testningen.

Bland de deltester som testar metoden ```getLetterCountDifferenceBetweenOriginalAndUpdatedText()``` måste deltestet som heter *'should return the difference between the original and updated text when using text from loremIpsum file as input'* köras före deltestet som heter *'should return a string that says "No words have been replaced." when changing the words back to the original text string'*.

### Metoder som testats med tillhörande deltester

**instantiating TextAnalyzer()**  
	✓ should throw an error when input is empty  
	✓ should throw an error when input is null  
	✓ should throw an error when input is undefined  

**averageNumberOfSentencesPerParagraph()**  
	✓ should throw an error when the input text is a dot  
	✓ should throw an error when the input text is a blank space  
	✓ should return 1 when there is one sentence  
	✓ should return 5 when using text from loremIpsum file as input  

**averageNumberOfWordsPerSentence()**  
	✓ should throw an error when the input text is a dot  
	✓ should throw an error when the input text is a blank space  
	✓ should return 1 when there is one word  
	✓ should return 5 when using text from loremIpsum file as input  

**countAllLines()**  
	✓ should return 1 when there is one word  
	✓ should return 1 when there is one sentence on one line  
	✓ should return 5 when using text from loremIpsum file as input  
	✓ should return 1 when the input text is a dot  
	✓ should return 1 when the input text is a blank space 

**countAllWords()**  
	✓ should return 1 when there is one word  
	✓ should return 224 when using text from loremIpsum file as input  
	✓ should throw an error when there are not words  
	✓ should throw an error when the input text is a blank space  
	✓ should throw an error when the input text contains only numbers  

**countLettersFrequencyAlphabeticalOrder()**  
	✓ should return letter count in alphabetical order when there is one word  
	✓ should return single letter count in lower case when there is one upper case letter  
	✓ should return letter count in alphabetical order when there is input from loremIpsum file  
	✓ should throw an error when there are only numbers  
	✓ should throw an error when there are no alpha-numeric characters  
	✓ should throw an error when the input text is a blank space  

**countNotEmptyLines()**  
	✓ should return 1 when there is one word  
	✓ should return 1 when there is one sentence on one line  
	✓ should return 5 when using text from loremIpsum file as input  
	✓ should return 1 when only one character input  
	✓ should return 0 when the input text is a blank space  

**countNonEmptyLinesWithoutJSComments()**  
	✓ should return the number of non empty lines without JS comments when using text from loremIpsum file as input  
	✓ should return the number of non empty lines without JS comments when only one character input  
	✓ should return the number of non empty lines without JS comments when the input is a blank space  
	✓ should throw an error when there are only numbers  

**countParagraphs()**  
	✓ should return 1 when there is one word  
	✓ should return 1 when there is one sentence in one paragraph  
	✓ should return 5 when using text from loremIpsum file as input  
	✓ should return 1 when only one character input  
	✓ should return 1 when the input text is a blank space  

**countSpecificWord()**  
	✓ should return 1 when there is one word  
	✓ should return 4 when using text from loremIpsum file as input and looking for word "cu"  
	✓ should return 0 when word is not found  
	✓ should return 0 when word is not found  
	✓ should return 0 when the input text is a blank space  
	✓ should throw an error when the word does not contain any letters  
	✓ should throw an error when the word contains unallowed characters  
	✓ should throw an error when the input text is null  
	✓ should throw an error when the input text is undefined  

**countWordsFrequencyAlphabeticalOrder()**  
	✓ should return single word count in lower case when there is a word that starts with an upper case letter  
	✓ should return word count in alphabetical order when there are several sentences  
	✓ should throw an error when there are only numbers  
	✓ should throw an error when there are no alpha-numeric characters  
	✓ should throw an error when the input text is a blank space  

**getCharacterCount()**  
	✓ shuld return the number of characters in a text  
	✓ should return the number of characters when using text from loremIpsum file as input  
	✓ should return 1 when only one character input  
	✓ should return 1 when the input is a blank space  

 **getFirstWordsInAlphabeticalOrder()**  
	✓ should return the first words in alphabetical order when using text from loremIpsum file as input  
	✓ should return the first word in alphabetical order when only one character input  
	✓ should return the first word in alphabetical order when the input is a blank space  
	✓ should throw an error when there are only numbers  

**getLetterCountDifferenceBetweenOriginalAndUpdatedText()**  
   ✓ should return that the updated text is longer than the original text  
    ✓ should return that the original text is longer than the updated text  
    ✓ should return that the text has not been updated if it has not been  
    ✓ should return a string that says "No words have been replaced." when changing the words back in the original text string  
    ✓ should return a string that says that the original text and the updated text are the same length  

**getSentenceCount()**  
	✓ should return the number of sentences when using text from loremIpsum file as input  
	✓ should return the number of sentences when using text from loremIpsum file as input  
	✓ should return the number of sentences when only one character input  
	✓ should return the number of sentences when the input is a blank space  
	✓ should throw an error when there are only numbers  

**replaceWordsWithExactFormatting()**  
	✓ should only replace words with exact formatting, case sensitive  
	✓ should replace words with exact formatting and not words that partially matches the word  
	✓ should throw an error when wordToReplace does not contain any characters  
	✓ should throw an error when newWord does not contain any characters  
	✓ should throw an error when wordToReplace contains unallowed characters  
	✓ should throw an error when newWord contains unallowed characters  
	✓ should throw an error when wordToReplace is null  
	✓ should throw an error when newWord is null  
	✓ should throw an error when wordToReplace is undefined  
	✓ should throw an error when newWord is undefined  

**replaceWordsWithTwoDifferentFormattings()**  
	✓ should replace words with two different formattings, case sensitive  
	✓ should replace words with two different formattings and not words that partially matches the word  
	✓ should throw error when trying to replace word with all upper case letters  
	✓ should replace words when newWord is all upper case, but keep formatting from wordToReplace  
	✓ should throw an error when wordToReplace does not contain any characters  
	✓ should throw an error when newWord does not contain any characters  
	✓ should throw an error when wordToReplace contains unallowed characters  
	✓ should throw an error when newWord contains unallowed characters  
	✓ should throw an error when wordToReplace is null  
	✓ should throw an error when newWord is null  
	✓ should throw an error when wordToReplace is undefined  

## Kodkvalitet

### Kapitel 2 - Namngivning

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

### Kapitel 3 - Funktioner

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
| | | Denna metod gör i stort sett samma sak som ```countNonEmptyLinesWithoutJSComments()``` och går därför emot DRY-principen. Dessa två metoder bör istället anropa en tredje metod som tar emot respektive logiskt uttryck (vilket är det som skiljer de två metoderna åt) som ett argument. |
| | | **Have No Side Effects** |
| | | Om arrayen ```this.#trimmedLines``` är tom anropas metoden ```this.#splitTextIntoTrimmedLines()``` som fyller arrayen med element. Det är en sidoeffekt som inte framgår av något av metodnamnen. |

### Reflektioner kring kapitel 3  
Den största behållningen från kapitel 3 är att funktionerna ska vara små. Som junior utvecklare ställer jag mig dock försiktigt skeptisk till hur bokens exempel drar detta till sin spets. Jag kan se hur det är lättare att både översätta modulen till ett annat språk samt att det gör modulen enklare att expandera, men jag anser inte att koden blir mer lättläst. Flödet i läsandet av koden bli mindre läsbar då jag upplever att det är svårt att komma ihåg hur anropet började. Större metoder, i viss utsträckning, är därför att föredra enligt mig, men jag ser absolut att det finns en poäng i att inte skriva metoder som är alldeles för stora. Efter att ha gjort denna laboration kommer jag ta för vana att försöka skriva mindre metoder som riktar sig mer mot att göra en sak, men inte till varje pris.

Att inte blanda abstraktionsnivåer var något som jag inte hade tänkt på överhuvudtaget tidigare och där ställer jag mig också lite skeptisk, men då det går i linje med att en metod ska göra en sak kan jag köpa konceptet.

Att det däremot skulle vara mindre önskvärt att ta emot argument i en metod hade jag svårt att förstå från början. Jag skapade därför först en vanlig modul, men övergick sedan till att göra om den till en klass där jag kunde spara olika privata fält som mina metoder kunde anropa utan att behöva ta emot argument varje gång. Endast fyra av mina sjutton publika metoder tar emot argument, vilket jag är nöjd med. Jag håller även med om att inte ta emot argument underlättar testningen och att det inte finns en risk att argument skickas in i fel format eller fel ordning.
