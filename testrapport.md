# Testrapport
I detta dokument redovisar jag för hur jag har utfört testningen av min modul. En engelsk version av denna rapport finns även [här](https://github.com/aw22hs/1DV610-L2/blob/main/testing.md), i samma repositorium som modulen har laddats upp i.

## Testspecifikation

Modulen har endast testats med automatiska tester. Testningen har utförts med Jest v29.7.0. För att kunna köra testerna har följande sträng angivits inuti `scripts` i package.json:
```
"test": "npx --node-options=--experimental-vm-modules jest --setupFiles"
```
För att starta testerna används således kommandot `npm test`.  

Testerna består av en testsvit med totalt 94 deltester som är uppdelade enligt de 16 publika metoder som anropas av testerna, se nedan. Samtliga tester är godkända i v.1.0.0 av modulen.

I mappen 'testdata' finns två filer, exampleCode.js och loremIpsum.md. Innehållet i dessa filer används som argument vid skapandet av två olika instanser av modulen som används under testningen.

Bland de deltester som testar metoden `getLetterCountDifferenceBetweenOriginalAndUpdatedText()` måste deltestet som heter *'should return the difference between the original and updated text when using text from loremIpsum file as input'* köras före deltestet som heter *'should return a string that says "No words have been replaced." when changing the words back to the original text string'*.

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
