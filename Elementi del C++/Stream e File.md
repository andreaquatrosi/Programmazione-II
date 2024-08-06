***
#### Stream
>Il **flusso** è un'astrazione che rappresenta un flusso di dati che scorre tra un programma produttore ed un programma consumatore

Esistono diversi tipi di **standard**, tra cui:
- **standard input**:
	- corrente di bytes che fluisce dalla tastiera verso un programma in esecuzione sulla CPU
- **standard output**:
	- corrente di bytes che fluisce dalla CPU verso un dispositivo di uscita

##### Libreria `<iostream>`
E' distribuita su quattro *header file*:
- `<iostream>`
	- classi `istream`, `ostream` ed `iostream` per le operazioni di I/O con i flussi di input e output standard ossia con gli oggetti `cout`, `cin`, `cerr`, `clog`
- `<fstream>`
- `<sstream>`
- `<strstream>`

###### Oggetti
- ![[Pasted image 20240510111835.png|450]]
###### Classi
Classe `istream`: permette di definire un flusso di input e contiene metodi per accettare dati formattati e non

Indicatori di stato:
- `cin.good()`
- `cin.bad()`
- `cin.fail()`
***
#### FIle
>Un file è un flusso esterno: una sequenza di byte in memoria di massa

Due tipi di apertura dei file:
- **scrittura**
- **lettura**

###### Classi
Sono tre:
- `ifstream`, per aprire un file di testo in *lettura*
- `ofstream`, per aprire un file di testo in *scrittura*
- `fstream`, per aprire un file di testo *indistintamente*

**Esempio di apertura**:
```c++
ifstream fin ("demo"); 

ofstream fout ("demo", ios::out ... ios::app);

// oggetti associato ad un file di nome "demo"
```