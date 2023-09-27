# Reflektion
Jag tycker att boken är väldigt intressant och pedagogiskt skriven. Det är även uppfriskande med en bok som har lite humor. 

Koncepten fån kapitel 2 kändes enklast att ta in, troligtvis eftersom namngivning är enklare att ”ta på” än funktioner. Som jag redan har skrivit håller jag inte helt med om författarens syn på exakt hur små funktioner ska vara. Däremot kommer dessa två kapitel ha inverkan på hur jag namnger och skriver framtida funktioner.

Eftersom jag hade läst i boken innan jag gjorde laborationen märkte jag att det som hade fastnat mest var att använda deskriptiva namn för både metoder och variabler samt att försöka skriva kortare metoder. Under reflektion av kodkvalitetskraven märkte jag dock att det fortfarande finns flera delar att arbeta vidare med, exempelvis *Use Intention-Revealing Names* och *Pick One Word per Concept*. Jag tycker även att det är svårt att veta, och behöver lära mig mer kring, när det är rimligt att göra en metod mindre och när det blir kaka på kaka. En av mina privata metoder, `getAndTrimSentences()`, har endast som uppgift att anropa två andra metoder, men eftersom dessa två metoder ska anropas i samma ordning från fyra andra metoder tog jag beslutet att göra `getAndTrimSentences()` till en metod. Det känns lite kaka på kaka, men det går i linje med DRY-principen.

Då min klass blev förhållandevis stor i förhållande till kravet på antal publika metoder övervägde jag att bryta ut någon del av koden till en egen klass. Ett alternativ hade varit att göra en `CodeAnalyzer` som höll metoden `countNonEmptyLinesWithoutJSComments()` där jag även hade kunnat skapa metoder som inriktade sig mer på att analysera kod.
 
