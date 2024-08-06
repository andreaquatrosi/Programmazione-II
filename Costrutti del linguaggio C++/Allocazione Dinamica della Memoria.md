***
Il sistema operativo assegna al programma tre specific segmenti della memoria principale:
- **code segment**, che ospita il codice stesso
- **data segment**, che ospita costanti e variabili globali
- **stack** (cresce verso l'alto), che contenendo variabili locali e parametri delle funzioni cresce e decresce durante l'esecuzione del programma 

La parte di memoria libera nello stack viene denominata **heap** (cresce verso il basso) e cresce e decresce *dinamicamente*

###### Heap
`new`:
Per generare dinamicamente una variabile di un certo tipo assegnandole un blocco di memoria della dimensione opportuna:
- `typename* ptr = new typename;`
- `typename* ptr = new typename[dim]`

`delete`:
Per liberare la memoria allocata dinamicamente perché possa eventualmente essere riallocata mediante successive chiamate all'operatore `new`:
- `delete ptr;`
- `delete [] ptr;`