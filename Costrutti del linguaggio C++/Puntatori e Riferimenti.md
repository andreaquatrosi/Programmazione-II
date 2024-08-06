***
#### Puntatore
>Un puntatore è una variabile che conteine l'indirizzo di memoria di una variabile

**Esempio**:
```c++
int n;
int* p; // p è un puntatore ad intero e * è un operatore di indirezione
p = &n; // p contiene l'indirizzo della variabile n intera
```

Terminologia:
- **dereferenziare**, vuol dire andare alla variabile puntata partendo da un suo puntatore

Possono anche esistere dei *puntatori a puntatori*:
```c++
int i = 1;
int* ptr1 = &i;
int** ptr2 = &ptr1;

// **ptr2 = 4 equivale a i = 4
```

###### Puntatore come argomento di una Funzione
```c++
#include <iostream>

using namespace std;

void swap(int* a, int* b) {
	int t = *a;
	*a = *b;
	*b = t;
}

int main() {
	int x = 1, y = 2;

	swap(&x, &y);
}

```

###### Restituire un Puntatore
`return ptr
```c++
#include <iostream>

// Definizione di una funzione che restituisce un puntatore a un intero
int* creaPuntatore() {
    int* ptr = new int; // Allocazione dinamica di memoria per un intero
    *ptr = 10; // Assegnazione di un valore all'indirizzo di memoria puntato da ptr
    return ptr; // Restituisce il puntatore
}

int main() {
    // Chiamata alla funzione e assegnazione del risultato a un puntatore
    int* puntatore = creaPuntatore();

    // Stampa il valore puntato dal puntatore
    std::cout << "Valore puntato dal puntatore: " << *puntatore << std::endl;

    // Deallocazione della memoria dinamica per evitare memory leak
    delete puntatore;

    return 0;
}
```
***
#### Riferimento
>Un **riferimento** è un *puntatore costante*, il cui nome non è accessibile al programmatore, che ha per valore l'indirizzo dell'oggetto riferito: l'operazione che coinvolge l'oggetto riferito viene realizzata effettuando un'indirezione sul puntatore nascosto

`return ref
```c++
#include <iostream>

// Definizione di una funzione che restituisce un riferimento a un intero
int& incrementa(int& num) {
    num++; // Incrementa il valore dell'intero
    return num; // Restituisce un riferimento all'intero
}

int main() {
    int x = 5;

    // Chiamata alla funzione e assegnazione del risultato a un riferimento
    int& riferimento = incrementa(x);

    std::cout << "x dopo l'incremento: " << x << std::endl; // Stampa 6
    std::cout << "Valore puntato dal riferimento: " << riferimento << std::endl; // Stampa 6

    return 0;
}

```

###### Variabili riferimento
>Una variabile di tipo **riferimento** è un ulteriore nome per una variabile

```c++
int n;
int &r = n;
```