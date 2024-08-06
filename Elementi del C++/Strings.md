***
>La stringa è una **sequenza di caratteri**, o **array di char**, che termina con il carattere nullo `\0`

Si può dereferenziare una stringa letterale utilizzando l'artimetica dei puntatori
- Sia "ABC" una stringa:
	- `*"ABC"` $=$ `ABC[0]`
	- `*("ABC" + n)` $=$ `ABC[n]`

**N.B.**: se $n$ supera la lunghezza effettiva della stringa, compreso il carattere terminatore, darà in output caratteri o simboli casuali

###### Definizione di Variabili Stringa
- Impostare il **bit di ordine alto** ad 1:
	- `char_array[i] |= 0x80`
- Inizializzazione:
	- `char stringa[4] = {'A','B','C'}`
	- `char stringa[4] = "ABC"`
	- `char stringa[13] = "Ciao a tutti"`
	- `char stringa[] = "Ciao a tutti, belli e brutti"`
- Assegnazione:
	- `strcpy(dest, src)`

###### Input / Output
```c++
#include <iostream>

using namespace std;

int main() {
	char nome[30];
	cin >> nome;  // input: Andrea Quatrosi  
	cout << nome; // output: Andrea
}
```

**N.B.**: i caratteri di *spaziatura* non fanno parte delle stringhe per questo la lettura dell'operatore `>>` termina quando ne incontra uno. Se vogliono anche essere letti bisogna usare la funzione `getline()`

###### Funzioni per Operazioni su Array di Char
`cin.get(car)`: restituisce $1$ se, leggendo un input dal flusso cin, legge un carattere altrimenti 0

```c++
#include <iostream>

int main() {
	char car;
	int i = 0;

	while(cin.get(car)) { // copia il carattere letto dal flusso cin in car
		if(car == 'x') {
			i++;
		} else {
			cout << i << endl;
		}
	}
}
```

`cin.getline(str, n, car)`: legge una linea di testo di lunghezza massima $n$ dal flusso di input, fino alla prima occorrenza del carattere `car`, e la memorizza in `str`

```c++
#include <iostream>
#include <string>
using namespace std;

int main(){
	// with array of char
    char stringa[20];

    cin.getline(stringa, 9, 'Q'); // input: Andrea Cacca ... Q

    cout << stringa << endl;      // output: Andrea C

	// with string
	string stringa;
	
	getline(cin, stringa);

	cout << stringa << endl;
}
```

**N.B.**: se si scrive `cin.getline(str, n)` implicitamente viene considerato come delimitatore della lettura il carattere `\0`

###### Stringhe come argomenti a funzioni
Per *argomento*:
```c++
#include <iostream>

using namespace std;

void modificaStringa(char* str) {
    strcat(str, "  Quatrosi");
}

int main() {
    const int lunghezzaMassima = 100;
    char frase[lunghezzaMassima] = "Questa è una stringa";

    modificaStringa(frase);

    cout << "Dopo la modifica: " << frase << endl;

    return 0;
}

```

Per *riferimento*:
```c++
#include <iostream>
#include <string>

using namespace std;

void mod_Stringa(string& str) {
	str += " Quatrosi"; // aggiunge " Quatrosi" alla fine di str
}

int main() {
	string stringa = "Andrea";

	mod_Stringa(stringa);

	cout << stringa << endl;
}
```

###### Libreria `<cstring>`
- ![[Pasted image 20240510110558.png|500]]
- ![[Pasted image 20240510110633.png|500]]