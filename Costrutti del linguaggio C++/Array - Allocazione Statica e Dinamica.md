I due tipi di allocazione sono:
- Statica
- Dinamica

### Allocazione Statica
L'allocazione Statica permette di utilizzare il segmento di memoria chiamato Stack (o Pila)

### Allocazione Dinamica
L'allocazione Dinamica permette di utilizzare il segmento di memoria Heap

Questo permette di manipolare e utilizzare l'array come un effettivo puntatore, eliminando, quando necessario o a fine programma, la porzione di memoria occupata dall'array

**Esempio**:
```c++
#include <iostream>

#define N 10

using namespace std;

void stampa(int *array) {

    for(size_t i = 0; i < N; i++) {
        cout << array[i] << "\t";
    }
}

int main(){

    //int array[N]/* = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}*/; // allocazione statica

    int *array = new int [N]; // allocazione dinamica

    //inizializza array

    for(size_t i = 0; i < N; i++) {
        array[i] = i;
    }

    //print array
    stampa(array);

    // deallocazione array
    delete [] array;
    array = nullptr;

    if(array != nullptr)
        cout << array[1];
    else
        cout << "\n array = nullptr\n";
}
```

**N.B.**: l'operatore `delete` se non è affiancato da `[]` deallocherà il primo elemento dell'array, perdendo così il riferimento al primo elemento
**N.B.**$_{2}$: a seguito di una `delete` si potrà accedere agli elementi dell'array ma il comportamento sarà indefinito. Viene eseguito dunque l'istruzione `array = nullptr`
