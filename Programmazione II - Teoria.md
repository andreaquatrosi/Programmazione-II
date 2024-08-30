***
### Complessità
>La complessità di un algoritmo misura le risorse necessarie per eseguire l'algoritmo, solitamente in termini di tempo (complessità temporale) e spazio (complessità spaziale)

Il **costo**, il "prezzo da pagare" per ottenere l'output dall'algoritmo stesso, di un algoritmo è in funzione di $n$, ossia della dimensione dei dati in input

Il costo può essere associato:
- alla **guardia**
- al **corpo**

Cos'è il *costo computazionale* o **complessità**?
Si può rappresentare: $$\sum^n_{i=0}c_i$$
ovvero la **sommatoria dei costi delle istruzioni**

Si definiscono anche:
- **tempo**, come il numero di *operazioni RAM* eseguite
- **spazio**, come il numero di *celle di memoria* occupate (escluse l'input)

#### Complessità Temporale
>Il tempo impiegato per risolvere un problema dipende sia dall'algoritmo utilizzato sia dalla "dimensione" dei dati a cui si applica l'algoritmo

La complessità temporale è:
- *proporzionale al numero di istruzioni* dell'intero programma eseguite
- *indipendente dall'hardware* considerato
- *dipendente dalla dimensione dell'input*

L'obbiettivo è valutare il comportamento di un algortimo quando le dimensioni $n$ dell'input *tendono ad infinito*

**Esempio**:
```c++
for(int i = 0; i < N; i++) {
	swap(i, i + 1);
	swap(i. i + 2);
	v[i] = -4;
}
```
- l'interesse è valutare il costo dell'istruzione che dipende dalla dimensione $N$

**N.B.**: non si valuta dunque l'algoritmo in sé ma la dimensioni delle strutture dati che si utilizzano

##### Caso Migliore e Peggiore
1. il **caso migliore** (*costo minimo*) è quello che, dipendentemente dalla natura del problema, viene eseguito più velocemente
2. il **caso peggiore** (*costo massimo*) è il viceversa
3. il **caso medio** (*costo medio*)

#### Notazione Asintotica
Per valutare la complessità di un algoritmo è necessario sapere il suo **comportamento asintotico**, in modo tale da stimare in quanto il tempo aumenta al crescere dell'input

Esistono tre tipi di notazione asintotica:
- $O$
- $\Omega$
- $\theta$

##### Notazione $O$
Definisce il *limite asintotico superiore* e si applica a delle funzioni $f(n)$ con un limite asintotico superiore costituito dalla funzione di costo $g(n)$:
- si denota con $O(g(n)) = \{f(n) :\exists c, n_0\space|\space 0\leq f(n) \leq c\cdot g(n)\space\forall n\geq n_0\}$
- ![[Pasted image 20240528115417.png|350]]

**N.B.**: $O(g(n))$ è l'insieme di funzioni $f(n)$ tali che esistano le costanti $c,n_0$ tale che $f(n)$ sia sempre maggiore o uguale a $0$ e minore o uguale a $c\cdot g(n)$ per ogni $n\geq n_0$
**N.B.**$_{_{2}}$: $x_{0}$ equivale ad $n_{0}$

Si può stabilire una relazione tra $f(n)$ e $O(g(n))$:
- $f(n)=O(g(n)) \to$ "*f(n) è O(g(n))*"

Nella valutazione degli algoritmi si va a valutare la notazione $O$ dando un **limite superiore** ad uno dei tre casi

Attraverso la notazione $O()$ gli algoritmi vengono suddivisi in classi di equivalenza. Si hanno così algoritmi (funzioni) di *complessità di ordine*:
- **costante**
	- $O(1)$ ossia la complessità di una funzione o blocco istruzioni ciascuna di costo $O(1)$, che non contengono cicli, ricorsione o chiamate ad altre funzioni non costanti
- **logaritmica**
	- $O(\log n)$, ossia la complessità di un ciclo quando le sue variabili sono incrementate o decrementate moltiplicandole o dividendole per una costante
	- ![[Pasted image 20240523110216.png|350]]
- **sotto-lineare** 
	- $O(n^c)$ con $c<1$, ossia la complessità per cicli annidati in base al numero di volte in cui vengono eseguite le istruzioni
- **lineare** 
	- $O(n)$, ossia la complessità di un ciclo quando le sue variabili sono incrementate o decrementate di una quantità costante
	- ![[Pasted image 20240523110018.png|350]]
- **polinomiale** 
	- $O(n\log n)$
	- $O(n^c)$ con $c>1$
- **esponenziale** 
	- $O(c^n)$, ossia la complessità di cicli annidati che è uguale al numero di volte in cui le istruzioni del ciclo interno vengono eseguite
	- ![[Pasted image 20240523110046.png|350]]

In *ordine*:
- $O(1) < O(log n) < O(n) < O(n log n) <O(n^c) < O(c^n)$

**In definitiva**, se un algoritmo $A$ prende al massimo tempo $t(n)$, allora $O(t(n))$ è un limite superiore.
Concettualmente:
- ![[Pasted image 20240528120913.png|350]]

##### Notazione $\Omega$
Definisce il *limite asintotico inferiore* e viene così descritta:
- $\Omega(g(n))=\{ f(n): \exists c,n_{0}\space|\space 0\leq c \cdot g(n)\leq f(n) \forall n\geq n_{0}\}$
- ![[Pasted image 20240801171508.png]]

Si stabilisce anche qui una relazione tra $f(n)$ e $\Omega(g(n))$:
- $f(n)=\Omega(g(n))$

**In definitiva**, se un algoritmo $A$ prende almeno tempo $t(n)$, allora $\Omega(t(n))$ è un limite inferiore.

##### Notazione $\Theta$
Definisce il *limite asintotico stretto* e viene così descritta:
- $\Theta(g(n))=\{ f(n): \exists c_{1},c_{2},n_{0}\space|\space 0\leq c_{1} \cdot g(n)\leq f(n)\leq c_{2}\cdot g(n)\space\forall n\geq n_{0}\}$
- ![[Pasted image 20240801172524.png]]

Si stabilisce una relazione tra $f(n)$ e $\Theta(g(n))$ leggermente più complessa:
- $f(n)=\Theta(g(n))\iff f(n)=\Omega(g(n))\text{ e }f(n)=O(g(n))$

**Esercizio**:
- ![[Pasted image 20240529112146.png|500]]

### Algoritmi di Ricerca e Ordinamento
#### Ricerca
Gli algoritmi di ricerca lineare hanno una complessità di circa $O(n)$. Un esempio di algoritmo di ricerca lineare:
```c++
bool linearSearch(int array[], int n, int key) {
	for(int i = 0; i < n; i++) {
		if(array[i] == key) {
			return true;
		}
	}
	
	return false;
}
```

Un tipo di ricerca più efficiente è la *ricerca dicotomica* o **ricerca binaria**
spiegata in seguito:

##### Ricerca Dicotomica o Binaria
Si effettua una ricerca su un array già ordinato. Questa è un informazione importante dato che permette di:
- *suddividere l'array a metà* e controllare se la key è $>,=,<$ dell'elemento presente nel mezzo
- *ripetere le suddivisioni* fino a che non si avranno due elementi per il quale scegliere quello richiesto

**Algoritmo**:
```c++
#include <iostream>
#include <cstdlib>
#include <time.h>

#define N 10

using namespace std;  

int* init_Array() {

	cout << "Enter array elements:\n";
    for(size_t i = 0; i < N; i++) {
        cin >> array[i];
    }

    return array;
}

void print_Array(int* array) {

	cout << "\nArray:\n";
    for(size_t i = 0; i < N; i++) {
        cout << array[i] << "\t";
    }

    cout << endl;
}

void sort_Array(int* array) {

    int temp = 0;

    for(size_t i = 0; i < N; i++) {
        for(size_t j = i + 1; j < N; j++) {
            if(array[j] < array[i]) {
                temp = array[i];
                array[i] = array[j];
                array[j] = temp;
            }
        }
    }
}

void binary_Search(int *array, int key) {

    bool found = false;

    // array lenght
    int start = 0;
    int end = N - 1;

    while(!found && (start != end)) {
        int midpoint = (start + end)/2;
        
        if (array[midpoint] == key) {
            found = true;
        } else if (key < array[midpoint]) {
            end = midpoint;
        } else {
            start = midpoint + 1;
        }
    }

    if(found) {
        cout << key << " found.";
    } else {
        cout << key << " not found.";
    }
}

int main() {
    
    int *a = init_Array();
    cout << "Unsorted Array:\n";
    print_Array(a);
    
    cout << "Sorted Array:\n";
    sort_Array(a);
    print_Array(a);

    int key;
    cin >> key;

    binary_Search(a, key);  

    delete [] a;
    a = nullptr;

    return 0;
}
```

#### Algoritmi Iterativi o di Ordinamento
L'algoritmo di ordinamento classico che si utilizza computa eseguendo un confronto tra due elementi in cui: se l'elemento `j`, successivo all'elemento `i`, è più piccolo allora si effettua lo scambio tra i due

**Algoritmo**:
```c++
#include <iostream>
#include <random>

#define N 10

using namespace std;  

template <typename T> void my_swap(T& a, T&b) {
    
    T t = a;
    a = b;
    b = t;
}

template <typename T> void sorting(T* array, int n) {

    for(int i = 0; i < n; i++) {
        for(int j = i + 1; j < n; j++) {
            if(array[j] < array[i]) {
                my_swap(array[i], array[j]);
            }
        }
    }
}

int main(){
    
    int array[N];
    // double array[N];

    random_device rd;
    mt19937 gen(rd());
    uniform_int_distribution<> dis(1, 10);

    for(int i = 0; i < N; i++)
        array[i] = dis(gen);
    
    cout << "Unsorted array:\n";
    for(int i = 0; i < N; i++) {
        cout << array[i] << " ";
    }

    sorting(array, N);

    cout << "\nSorted array:\n";
    for(int i = 0; i < N; i++) {
        cout << array[i] << " ";
    }

    return 0;
}
```

##### Selection Sort
Quest'algoritmo prevede l'utilizzo di una variabile il cui contenuto è l'indice dell'elemento più piccolo, il quale verrà confrontato e aggiornato ad ogni occorrenza di un elemento ancora più piccolo

Finiti i confronti si effettua uno swap tra l'elemento fissato dal ciclo e l'elemento di indice minore

Si ripete il procedimento per la lunghezza dell'array

*Complessità*: $O(n^2)$
*Vantaggio*: meno chiamate alla funzione swap e maggiore vantaggio in termini di efficienza

**Algoritmo**:
```c++
#include <iostream>

#define N 5  

using namespace std;

void swap(int& a, int& b) {

    int t = a;
    a = b;
    b = t;
}

void selection_sort(int array[]) {

    for(size_t i = 0; i < N; i++) {
        size_t index_min = i;

        for(size_t j = i + 1; j < N; j++) {
            if(array[j] < array[i]) {
                index_min = j;
            }
        }

        swap(array[i], array[index_min]);
    }
}

int main() {

    int array[N];  

    cout << "Enter array elements:\n";
    for(size_t i = 0; i < N; i++) {
        cin >> array[i];
    }

    cout << "Unsorted Array:\n";
    for(size_t i = 0; i < N; i++) {
        cout << array[i] << " ";
    }

    selection_sort(array);

    cout << "\nSorted Array:\n";
    for(size_t i = 0; i < N; i++) {
        cout << array[i] << " ";
    }

    return 0;
}
```

##### Insertion Sort
Quest'algoritmo prevede l'utilizzo di una variabile temporanea che immagazina un elemento dello array per confrontarlo con tutti quelli che lo precedono: se uno degli elementi che lo precede è più grande dell'elemento nella variabile temporanea, si effettua uno scambio

Si ripete questa logica e queste operazioni finché l'array non è ordinato

```c++
#include <iostream>

#define N 5  

using namespace std;

void insertion_sort(int array[]) {

    for(size_t i = 1; i < N; i++) {
        int temp = array[i];

        size_t j = i;
        while((j > 0) && (temp < array[j - 1])) {
            array[j] = array[j - 1];
            j--;
        }
  
        array[j] = temp;
    }
}

int main() {

    int array[N];

    for(size_t i = 0; i < N; i++) {
        cin >> array[i];
    }

    cout << "Unsorted Array:\n";
    for(size_t i = 0; i < N; i++) {
        cout << array[i] << " ";
    }

    insertion_sort(array);

    cout << "\n\nSorted Array:\n";
    for(size_t i = 0; i < N; i++) {
        cout << array[i] << " ";
    }

    return 0;
}
```

*Complessità*: $O(n^2)$
*Vantaggio*: e fico

#### Algoritmi Ricorsivi di Ordinamento
Rispetto agli *algoritmi di ordinamento iterativi* sono più efficienti, in termini di complessità. Si basano sulla ricorsione e sulla logica *dividi et impera*

I passi del paradigma **dividi et impera** sono tre:
1. *suddividere il problema in sottoproblemi*
2. *risolvere i sottoproblemi*
3. *combinare le soluzioni*

##### Merge Sort
La logica su cui si basa questo algoritmo risiede principalmente nella *combinazione*

Quest'ultima è realizzata tramite una funzione **merge**:
- prende un array di dimensione $n$
- suddivide l'array in due sottoarray già ordinati
- combina gli array nell'array più grande in modo tale che mantengano l'ordine esatto

 **Esempio** della logica:
 - *sotto-array di sinistra*:
	 - ![[Pasted image 20240807153308.png|350]]
	 - ![[Pasted image 20240807153357.png|350]]
	 - ![[Pasted image 20240807153453.png|350]]
	- ![[Pasted image 20240807153605.png|350]]
- *stessa procedura per il sotto-array di destra*:
	- ...
- *combinazione finale*:
	- ![[Pasted image 20240807153707.png|350]]
	- ![[Pasted image 20240807153726.png|350]]

*Complessità*: $O(n\log n)$ e complessità spaziale maggiore rispetto ai classici algoritmi di ordinamento
*Vantaggio*: per grandi $n$, è la soluzione ottimale rispetto a **insertion sort**, **selection sort** e **bubble sort**

**Algoritmo**:
```c++
#include <iostream>

using namespace std;

void merge(int* A, size_t p, size_t q, size_t r) {

    size_t n1 = q-p+1; // Dimensione sotto-array L
    size_t n2 = r-q;   // Dimensione sotto-array R

    int* L = new int [n1+1];
    int* R = new int [n2+1];

    size_t i = 0, j = 0;
    
    // Inizializzo L con gli elementi di sinistra di A
    for(i = 0; i < n1; i++) {
        L[i] = A[p+i];
    }

    // Inizializzo R con gli elementi di destra di A
    for(j = 0; j < n2; j++) {
        R[j] = A[q+1+j];
    }

    i = j = 0;

    L[n1] = R[n2] = INT_MAX;    // Elementi sentinella  

    for(size_t k = p; k <= r; k++) {
        if(L[i] < R[j]) {
            A[k] = L[i];
            i++;
        } else {
            A[k] = R[j];
            j++;
        }
    }

    delete [] L;
    L = nullptr;

    delete [] R;
    R = nullptr;
}

void mergeSort(int* A, size_t p, size_t r) {

	// p = left
	// r = right
	// q = middle
    if(p < r) {
        size_t q = (p+r)/2; // suddivido l'array in due parti
        
        mergeSort(A, p, q); // applico il merge sort fino a quando i sotto-array hanno dimensione = 1
        mergeSort(A, q+1, r);
        merge(A, p, q, r);
    }
}

int main() {

    constexpr size_t N = 11;

    int array[N];

    cout << "Fill array:\n";
    for(size_t i = 0; i < N; i++)
        cin >> array[i];

    cout << "Unsorted Array:\n";
    for(size_t i = 0; i < N; i++)
        cout << array[i] << " ";

    cout << "\nSorted Array:\n";
    mergeSort(array, N-N, N);
    for(size_t i = 0; i < N; i++)
        cout << array[i] << " ";

    return 0;
}
```

##### Quick Sort
La logica risiede principlamente sul passo di *suddivisione dello array*, chiamato anche *partition*

Si sviluppa nel seguente modo:
- si prende un elemento a caso che sarà il **pivot**
- gli indici `p` ed `r` saranno gli indici di inizio e fine dello array
	- si inizializzano gli indici `i = p-1` e `j = p`
- si fa *scorrere* `j` da `p -> r`: se l'elemento $A[j]\leq$ **pivot** allora si fa *avanzare* `i` e si *scambia* $A[i]$ con $A[j]$
- scorso tutto lo array, si *scambia* il **pivot** con $A[i+1]$ e *restituisco* `i+1` ovvero la posizione finale del **pivot**

**N.B.**: lo scopo del pivot è di posizionarlo nella sua posizione ordinata finale, mettendo gli elementi minori a sinistra e maggiori a destra

**Algoritmo**:
```c++
#include <iostream>

using namespace std;
  
void swap(int& a, int& b) {

    int t = a;
    a = b;
    b = t;
}

int partition(int* A, size_t p, size_t r) {

    size_t i = p-1;
    size_t j = p;

    int& pivot = A[r];

    while(j < r) {
        if(A[j] <= pivot) {
            i++;
            swap(A[i], A[j]);
        }
        
        j++;
    }

    swap(pivot, A[i+1]);

    return i+1;
}

void quickSort(int* A, size_t p, size_t r) {

	// p = left
	// r = right
	// q = middle
    if(p < r) {
        int q = partition(A, p, r);
        
        quickSort(A, p, q-1);
        quickSort(A, q+1, r);
    }
}

int main() {

    constexpr size_t N = 8;

    int array[N];
  
    cout << "Fill array:\n";
    for(size_t i = 0; i < N; i++)
        cin >> array[i];

    cout << "Unsorted Array:\n";
    for(size_t i = 0; i < N; i++)
        cout << array[i] << " ";

    cout << "\nSorted Array:\n";
    quickSort(array, N-N, N);
    for(size_t i = 0; i < N; i++)
        cout << array[i] << " ";

    return 0;
}
```

*Complessità*: nel **caso medio** $O(n\log n)$ mentre nel **caso peggiore** $O(n^2)$
*Vantaggio*: l'algoritmo è più efficiente con $n$ molto grandi dato che prendere un elemento che sia il minimo o il massimo è molto meno probabile

## OOP (Object Oriented Programming)
I principi di base di questo paradigma di programmazione sono:
- **astrazione**
- **incapsulamento** (o **information hiding**)
- **ereditarietà**
- **polimorfismo**

### 1. Astrazione
>E' un procedimento che consente di semplificare la realtà che si vuole modellare. La semplificazione avviene concentrando l'attenzione solo sugli elementi importanti del sistema complesso preso in considerazione

Terminologia:
- **Astrarre** significa semplificare delle entità complesse in *oggetti caratterizzati dalle caratteristiche e dalle funzionalità essenziali* per gli scopi preposti

### 2. Information Hiding
>E' la capacità di una classe di incapsulare sia le caratteristiche (attributi) che i comportamenti (metodi) degli oggetti che rappresenta

Limita di molto gli errori rispetto alla programmazione strutturata

### Classe
>Una classe è un insieme di oggetti che condividono struttura e comportamento

Essa contiene:
- **attributi**, specifica dei dati che descrivono ogni oggetto che ne fa parte
- **metodi**, descrizione delle azioni che l'oggetto stesso è capace di eseguire

**Codice**:
```c++
#include <iostream>
using namespace std;

// Definizione della classe
class MyClass {
private:
    int data;

public:
    // Costruttore
    MyClass(int d) : data(d) {}

    // Metodo inline per ottenere il valore dei dati
    int getData() const {
        return data;
    }

    // Metodo inline per impostare il valore dei dati
    void setData(int data) {
        this->data = data;
    }

    // Metodo esterno per stampare i dati
    void display() const;
};

void MyClass::display() const {
    cout << "Data: " << data << endl;
}

int main() {
    // Creazione di un oggetto della classe
    MyClass obj(42);

    // Utilizzo dei metodi della classe
    obj.display();

    obj.setData(100);
    cout << "Updated Data: " << obj.getData() << endl;

    return 0;
}
```

>L'**oggetto** è un'*istanza* della classe che viene allocata in memoria

**N.B.**: i metodi **non** occupano spazio nell'istanza di un oggetto mentre gli attributi sì

#### Costruttore
>E' il metodo responsabile dell'istanziazione di un oggetto

Caratteristiche:
- ha lo stesso nome della classe
- non ha tipo di ritorno
- inizializza i valori degli attributi

**N.B.**: E' bene che un oggetto si possa auto-inizializzare a seguito della sua creazione, senza dovere effettuare una successiva chiamata ad una sua qualche funzione membro
**N.B.**$_{2}$: C++ crea automaticamente un *costruttore di default* quando non vi sono altri costruttori, tuttavia esso non inizializza i membri della classe a valori predefiniti

#### Distruttore
>E' un metodo speciale che viene chiamato automaticamente quando si distrugge un oggetto; serve per liberare la memoria assegnata dal costruttore

Caratteristiche:
- stesso nome della classe preceduta dal simbolo ~
- non ha tipo di ritorno
- non accetta parametri
- non può essercene più di uno
- se non si dichiara, C++ ne crea uno in automatico

##### Header File
>Separare in files diversi il codice "cliente" della classe dal codice della classe

##### Intestazione di classe
>Separare il codice sorgente di una classe in due files con lo stesso nome della classe
- uno con la definizione della classe (solo prototipi dei metodi) ed estensione **.h**
- un altro con le implementazioni dei metodi della classe ed estensione **.cpp**

#### Static, Const e Friend
##### 1. Static
Generalmente, una variabile dichiarata all'interno di una funzione ha uno *scope* limitato al corpo della stessa

Per far sì che il valore della variabile permanga in memoria e in tutte le chiamate successive alla funzione stessa bisogna aggiungere la keyword `static`, che precede la classica dichiarazione di una variabile

**Codice**:
```c++
#include <iostream>

using namespace std;

void foo() {

    static size_t a = 0;
    cout << a++ << endl;
}

int main() {

    for(size_t i = 0; i < 5; i++) {
        foo();
    }
   // cout << a << "\n";

    return 0;
}
```

**N.B.**: il valore della variabile `a` dichiarata nel corpo della funzione `foo` viene incrementato ogni volta che la funzione stessa viene chiamata
**N.B.**$_{2}$: non posso utilizzare la variabile `a` al di fuori della funzione, per cui la riga $726$ produce un *errore* a tempo di compilazione

###### OOP e `static`
Nella OOP, la variabile `static` conserva le stesse caratteristiche, ma la dichiarazione avviene al di fuori della classe stessa (non *inline*)

**Codice**:
```c++
#include <iostream>

using namespace std;

class Test {

    private:
        static size_t a;

    public:
        Test() {
            a++;
        }

        void print() const {
        
            cout << a << endl;
        }
};

size_t Test::a = 0;
  
int main() {

    Test test[3];

    for(size_t i = 0; i < 3; i++)
        test[i].print();

    return 0;
}
```

##### 2. Const
L'operatore `const` permette di rendere il valore di una variabile, o funzione immutabile, aggiungendo la keyword che precede la classica dichiarazione di una variabile

##### 3. Friend
La keyword `friend` permette di fornire ad una funzione o ad una classe esterna accesso ai membri privati e protetti della classe in cui appare

Un utilizzo della funzione friend avviene tramite l'*overloading* dell'operatore di stampa di una classe:
```c++
class MyClass {
	private:
		int var;

	public:
		A() : var(0) {}

		friend ostream& operator << (ostream& os, const MyClass& myObj) {
			os << "I'm MyClass's attribute: " << myObj.var << "\n";
			return os;
		}
};
```

### 3. Ereditarietà
>Una classe derivata **eredita** attributi e metodi dalla classe base già esistente

E' un ulteriore livello di astrazione che permette di avere un livello più alto rispetto a un interfaccia comune (*classe base*), grazie al al quale tutte le proprietà di questa classe vengono estese alle *classi derivate* (in quest'ultime si possono aggiungere nuove specifiche e funzionalità)

### 4. Polimorfismo
>Il **polimorfismo** permette di avere funzioni che hanno la stessa firma ma assumono diversi comportamenti a seconda del chiamante

E' la caratteristica grazie al quale oggetti di classi diverse rispondono in maniera diversa a uno stesso metodo

E' fondamentale associare il concetto di **binding**

#### Binding
>Si riferisce all'associazione tra una funzione chiamata e la funzione che viene effettivamente eseguita

Può essere:
- **statico**, se l'associazione avviene a *tempo di compilazione*
- **dinamico**, se l'associazione avviene a *tempo di esecuzione*

##### Binding Statico
Questo tipo di binding è utilizzato per le funzioni **non** virtuali. Le funzioni vengono risolte in base al tipo dell'oggetto al momento della compilazione

**Esempio**:
```c++
#include <iostream>
using namespace std;

class Base {
	public:
	    void show() {
	        cout << "Base::show() called" << endl;
	    }
	};

class Derived : public Base {
	public:
	    void show() {
	        cout << "Derived::show() called" << endl;
	    }
	};

int main() {
    Base b;
    Derived d;

    b.show(); // Chiama Base::show()
    d.show(); // Chiama Derived::show()

    Base* ptr;
    ptr = &d;
    ptr->show(); // Chiama Base::show() (binding statico)

    return 0;
}
```

##### Binding Dinamico
Questo tipo di binding è utilizzato per le funzioni virtuali. Le funzioni vengono risolte in base al tipo dell'oggetto al momento dell'esecuzione, non al momento della compilazione

Per abilitarlo si utilizzano le *funzioni virtual*

**Esempio**:
```c++
#include <iostream>
using namespace std;

class Base {
public:
    virtual void show() {
        cout << "Base::show() called" << endl;
    }
};

class Derived : public Base {
public:
    void show() override {
        cout << "Derived::show() called" << endl;
    }
};

int main() {
    Base b;
    Derived d;

    b.show(); // Chiama Base::show()
    d.show(); // Chiama Derived::show()

    Base* ptr;
    ptr = &d;
    ptr->show(); // Chiama Derived::show() (binding dinamico)

    return 0;
}
```

**N.B.**: elementi *public* vengono ereditati con le stesse proprietà, dunque rimangono o publici o protetti. 
Ciò non vale nel caso in cui l'ereditarietà è di tipo *protected* o *private*, poiché viene alterato lo scope degli elementi **public** nella classe madre ad uno dei due, in base alla specifica, nella classe derivata

#### Funzioni Virtual
`virtual` anteposto alla dichiarazione di una funzione indica al compilatore che:
- essa può essere definita in una classe derivata
- la funzione potrà essere invocata tramite un puntatore

>Permettono a una classe base di definire funzioni che possono essere sovrascritte nelle classi derivate, con il comportamento corretto determinato a tempo di esecuzione

**Esempio**:
```c++
// polimorfismo con funzioni virtual
#include <iostream>

using namespace std;

class Shape {
	public:
	    virtual void draw() const {
	        cout << "Drawing Shape" << endl;
	    }
	
	    virtual ~Shape() {}
};

class Circle : public Shape {
	public:
	    void draw() const override {
	        cout << "Drawing Circle" << endl;
	    }
};

class Square : public Shape {
	public:
	    void draw() const override {
	        cout << "Drawing Square" << endl;
	    }
};

void renderShape(const Shape& shape) {
    shape.draw();
}

int main() {
    Circle circle;
    Square square;

    renderShape(circle); // Chiama Circle::draw()
    renderShape(square); // Chiama Square::draw()

    return 0;
}
```

**Esercizio di Riassunto**:
```c++
#include <iostream>
#include <cstdlib>
#include <cstring>

using namespace std;

// Definizione della classe
class MyClass {

    private:
        int data;
        char* name;
        static size_t counter;

    public:
        // Default
        MyClass() : data(0), name(nullptr) {
            
            name = new char [1];
            name[0] = '\0';
        }                      
        
        // Parametrized
        MyClass(int d, const char* name) : data(d), name(new char [strlen(name) + 1]) {

            strcpy(this->name, name);
            counter++;
        }    

        // Copy
        MyClass(MyClass& obj) {  

            data = obj.get_Data();
            strcpy(name, obj.get_Name());
            counter++;
        }

        ~MyClass() {

            delete [] name;
        }

        // Getter
        int get_Data() const { return data; }

        char* get_Name() const { return name; }

        // Setter
        void set_Data(int data) { this->data = data; }

        void set_Name(const char* name) {

            delete [] this->name;

            this->name = new char [strlen(name) + 1];
            strcpy(this->name, name);
        }

        // Metodo esterno per stampare i dati
        /*virtual*/ void display() const;

        // Friend
        friend void add_data(int to_add, MyClass& obj);
};

void MyClass::display() const {

    cout << "MyClass::display()"
         << "\nData: " << data
         << "\nName: " << name
         << "\n";
}

size_t MyClass::counter = 0;

// Friend
void add_data(int to_add, MyClass& obj) {

    obj.data += to_add;
}

class MyDerivedClass : public MyClass {

    private:
        double extraData;

    public:
        // Parametrized Constructor
        // chiama il costruttore della classe base

        MyDerivedClass(int data, char* name, double extraData) : MyClass(data, name), extraData(extraData) {}

        ~MyDerivedClass() {}

        // Getter
        double get_extraData() const { return extraData; }

        // Setter
        void set_extraData(double extraData) { this->extraData = extraData; }

        // Metodo
        void display() const {
        
            MyClass::display();
            cout << "MyDerivedClass::display()"
                 << "\nExtra Data: " << extraData
                 << "\n";
        }
};

int main() {

    // Creazione di un oggetto della classe MyClass
    MyClass obj_b(42, "Andrea");

    // Utilizzo dei metodi della classe
    obj_b.display();
    obj_b.set_Data(100);
    cout << "\nUpdated Data: " << obj_b.get_Data() << endl;
    
    cout << "\nUpdated Data using add_data()\n";
    add_data(10, obj_b);  // add_data() è una funzione friend
    obj_b.display();

    // Creazione di un oggetto della classe MyDerivedClass
    char* name = new char [10];
    strcpy(name, "Andrea");
    cout << "\nCalling display() in the derived object\n";
    MyDerivedClass obj_d(69, name, 420.69);

    obj_d.display();

    // Ptr
    cout << "\nUsing pointer to MyDerivedClass\n";
    MyClass* ptr = &obj_d;
    ptr->display();         // Chiama MyClass::display() (binding statico)
                            // Aggiungere "virtual" alla riga 53 per chiamare MyDerivedClass::display() (binding dinamico)

    return 0;
}
```

#### Template di classi e funzioni
##### Template di Funzioni
>Così come una classe è un modello per istanziare oggetti a tempo di esecuzione, un **template** è un modello per istanziare classi o funzioni a tempo di compilazione

**Esempio**:
```c++
// swap function using a template
template <typename T>       // Sintassi
void swap(int& x, int& y) {
	T t = x;
	x = y;
	y = t;
}
```

##### Template di Classi
**Esempio**:
```c++
template <typename T>
class MyClass {
private:
    T data;

public:
    // Costruttore
    MyClass(T data) : data(data) {}

    // Metodo per ottenere il valore dei dati
    T getData() const {
        return data;
    }

    // Metodo per impostare il valore dei dati
    void setData(T data) {
        this->data = data;
    }

    // Metodo per stampare i dati
    void display() const {
        cout << "Data: " << data << endl;
    }
};

int main() {
    // Creazione di oggetti della classe template con tipi diversi
    MyClass<int> intObj(42);
    MyClass<double> doubleObj(3.14);
    MyClass<string> stringObj("Hello, World!");

    // Utilizzo dei metodi della classe template
    intObj.display();
    doubleObj.display();
    stringObj.display();

    return 0;
}

```

### Strutture Dati
>Sono entità astratte con comportamenti predefiniti per *organizzare dati*

#### Liste
>E' una sequenza di elementi i quali sono collegati l'uno all'altro

La differenza con l'array è che la lista *non viene preallocata* ma viene popolata a tempo di esecuzione poiché non ha una dimensione prefissata

La lista ha come elementi costitutivi dei **nodi** che contengono:
- un **valore**
- un **puntatore** al *nodo successivo*

##### 1. Liste Linkate Semplici
>E' una sequenza di nodi in cui ogni nodo ha un valore e un collegamento all'elemento successivo

**Esempio**:
- ![[Pasted image 20240824155336.png|350]]
In termini di codice, una lista è formata da una **head**, un puntatore al primo elemento della lista, e da una **tail**, un puntatore a `nullptr` ossia la fine della lista

**Implementazione**:
```c++
#include <iostream>

using namespace std;

template <typename T>
class Node {

    private:
        T value;
        Node<T>* next;
        
    public:
        Node() : value(T()), next(nullptr) {}
        Node(T value) : value(value), next(nullptr) {}
       
		// Getter
        T get_value() const { return value; }
        Node<T>* get_next() const { return this->next; }

        // Setter
        void set_next(Node<T>* next) { this->next = next; } 
};

template <typename T>
class List {

    private:
        Node<T>* head;

	public:
        List() : head(nullptr) {}

        ~List() {
  
			Node<T>* current = head;
            Node<T>* nextNode;
  
            while(current != nullptr) {
                nextNode = current->get_next();
                delete current;
                current = nextNode;
            }
        }

        // Operazioni
        bool is_Empty() { return head == nullptr; }

        void push_head(T value) {

            Node<T>* newNode = new Node<T>(value);

            if(this->is_Empty()) {
                newNode->set_next(head);
                head = newNode;
            } else {
                newNode->set_next(head);
                head = newNode;
            }
        }

        void push_tail(T value) {

            Node<T>* newNode = new Node<T>(value);

            if(this->is_Empty()) {
                newNode->set_next(head);
                head = newNode;
            } else {
                Node<T>* temp = head;
                
                while(temp->get_next() != nullptr)
                    temp = temp->get_next();

                temp->set_next(newNode);
            }
        }

        void push_sorted(T value) {
        
            Node<T>* newNode = new Node<T>(value);
  
            if(this->is_Empty() || value < head->get_value()) {
                newNode->set_next(head);
                head = newNode;
            } else {
                Node<T>* current = head;
                Node<T>* prev = nullptr;

                while(current != nullptr && current->get_value() < value) {
                    prev = current;
                    current = current->get_next();
                }

                newNode->set_next(current);
                if(prev != nullptr)
                    prev->set_next(newNode);
            }
        }

        T extract_head() {

            if(this->is_Empty()) {
                cout << "\nEmpty list!\n";
                exit(EXIT_FAILURE);
            } else {
                Node<T>* temp = head;
                
                T value = head->get_value();
                head = head->get_next();

                delete temp;
                
                return value;
            }
        }

        T extract_tail() {

            if(this->is_Empty()) {
                cout << "\nEmpty list!\n";
                exit(EXIT_FAILURE);
            } else {
                Node<T>* temp = head;
                Node<T>* prev = nullptr;
  
                while(temp->get_next() != nullptr) {
                    prev = temp;
                    temp = temp->get_next();
                }

                T value = temp->get_value();

                if(prev != nullptr)
                    prev->set_next(nullptr);
                else
                    head = nullptr; // the list has only one element

                delete temp;  

                return value;
            }
        }

        bool extract_element(T value) {

            if(this->is_Empty()) {
                cout << "\nEmpty list!\n";
                exit(EXIT_FAILURE);
            } else {
                if(value == head->get_value()) {
                    extract_head();
                    return true;
                }

                Node<T>* temp = head;
                Node<T>* prev = nullptr;

                while(temp != nullptr && value != temp->get_value()) {
                    prev = temp;
                    temp = temp->get_next();
                }

                if(temp == nullptr)
                    return false;

                prev->set_next(temp->get_next());
                
                delete temp;

                return true;
            }
        }
  
        void print_list() const {

            Node<T>* temp = head;

            while(temp != nullptr) {
                cout << temp->get_value() << " -> ";
                temp = temp->get_next();
            }
  
            cout << "nullptr\n";
        }
};

int main() {

    List<int> list;

    /*list.push_head(69);
    list.push_tail(420);
    list.push_head(90);
    list.push_tail(45);
  
    list.print_list();

    int value1 = list.extract_head();
    list.print_list();

    int value2 = list.extract_tail();
    list.print_list();

    list.push_tail(42);
    list.push_tail(100);
    list.print_list();
    
    int value3 = list.extract_element(42);*/

    list.push_sorted(50);
    list.push_sorted(20);
    list.push_sorted(60);
    list.push_sorted(30);
    list.push_sorted(40);
    list.print_list();

    return 0;d
}
```

##### 2. Liste Doppiamente  Linkate
>Sono liste che hanno un collegamento sia al nodo successivo che al nodo precedente

Il nodo sarà costituito da:
- un **valore**
- un **puntatore** all'elemento *successivo*
- un **puntatore** all'elemento *precedente*

La lista, invece, conterrà oltre al puntatore alla head, un **puntatore** alla *tail*

**Esempio**:
- ![[Pasted image 20240826123824.png|350]]

**Implementazione**:
```c++
#include <iostream>

using namespace std;  

template <typename T>
class Node {

    private:
        T value;
        Node<T>* next;
        Node<T>* prev;

    public:
        Node() : value(T()), next(nullptr), prev(nullptr) {}
        Node(T value) : value(value), next(nullptr), prev(nullptr) {}

        // Getter
        T get_value() const { return value; }
        Node<T>* get_next() const { return next; }
        Node<T>* get_prev() const { return prev; }

        // Setter
        void set_value(T value) { this->value = value; }
        void set_next(Node<T>* next) { this->next = next; }
        void set_prev(Node<T>* prev) { this->prev = prev; }
};

template <typename T>
class List {

    private:
        Node<T>* head;
        Node<T>* tail;

    public:
        List() : head(nullptr), tail(nullptr) {}

        ~List() {
        
            Node<T>* current = head;
            Node<T>* nextNode;
  
            while (current != nullptr) {
                nextNode = current->get_next();
                delete current;
                current = nextNode;
            }
        }

        // Operazioni
        bool is_Empty() const { return head == nullptr; }

        void push_head(T value) {

            Node<T>* newNode = new Node<T>(value);  
            
            if(this->is_Empty()) {
                head = newNode;
            } else {
                newNode->set_next(head);
                head->set_prev(newNode);
                head = newNode;
            }
        }

        void push_tail(T value) {

            Node<T>* newNode = new Node<T>(value);  

            if(this->is_Empty()) {
                head = newNode;
            } else {
                Node<T>* temp = head;

                while(temp->get_next() != nullptr)
                    temp = temp->get_next();
                    
                temp->set_next(newNode);
                newNode->set_prev(temp);
            }
        }

        void push_sorted(T value) {

            Node<T>* newNode = new Node<T>(value);  

            if(this->is_Empty() || value < head->get_value()) {
                newNode->set_next(head);

                if(head != nullptr)
                    head->set_prev(newNode);

                head = newNode;
            } else {
                Node<T>* current = head;

                while(current->get_next() != nullptr && value > current->get_next()->get_value())
                    current = current->get_next();

                newNode->set_next(current->get_next());  

                if(current->get_next() != nullptr)
                    current->get_next()->set_prev(newNode);

                current->set_next(newNode);
                newNode->set_prev(current);
            }      
        }

        T extract_head() {  

            if(this->is_Empty()) {
                cout << "\nThe list's empty!\n";
                exit(EXIT_FAILURE);
            } else {

                Node<T>* temp = head;
                T value = head->get_value();
                head = head->get_next();

                if(head != nullptr)
                    head->set_prev(nullptr);

                delete temp;

                return value;
            }
        }

        T extract_tail() {

            if(this->is_Empty()) {
                cout << "\nThe list's empty!\n";
                exit(EXIT_FAILURE);
            } else {

                Node<T>* temp = head;

                while(temp->get_next() != nullptr)
                    temp = temp->get_next();
                
                T value = temp->get_value();

                if(temp->get_prev() != nullptr)
                    temp->get_prev()->set_next(nullptr);
                else
                    head = nullptr;

                delete temp;

                return value;
            }
        }

        bool extract_element(T value) {

            if(this->is_Empty()) {
                cout << "\nThe list's empty\n";
                exit(EXIT_FAILURE);
            } else {

                Node<T>* temp = head;

                while(temp != nullptr && value != temp->get_value())
                    temp = temp->get_next();

                if(temp == nullptr)
                    return false;
                if(temp->get_prev() != nullptr)
                    temp->get_prev()->set_next(temp->get_next());
                else    
                    head = temp->get_next();    // element is in the head

                if(temp->get_next() != nullptr)
                    temp->get_next()->set_prev(temp->get_prev());

                delete temp;

                return true;
            }
        }

        void print() const {

            Node<T>* current = head;

            while(current != nullptr) {
                cout << current->get_value() << " -> ";
                current = current->get_next();
            }

            cout << "nullptr\n";
        }
};

int main() {

    List<int> list;
    /*
    list.push_head(69);
    list.push_tail(420);
    list.push_head(90);
    list.push_tail(45);
    */
    
    list.push_sorted(50);
    list.push_sorted(20);
    list.push_sorted(60);
    list.push_sorted(30);
    list.push_sorted(40);

    list.print();

    list.extract_head();
    list.extract_tail();
    list.extract_element(30);
    
    list.print();

    return 0;
}
```

#### Pila e Coda
##### Pila (o Stack)
>E' una struttura dati astratta nel quale le operazioni di inserimento e rimozione avvengono sempre dalla *cima della pila*

E' una struttura dati di tipo **LIFO** (**L**ast **I**n **F**irst **O**ut), ossia l'ultimo elemento inserito è il primo rimosso

Gli elementi costitutivi della pila sono:
- una **dimensione**
- un **puntatore** alla *head*

Per i metodi si ha:
- `push()`, aggiungere un elemento in cima
- `pop()`, estrarre un elemento dalla cima
- `is_empty()`, controllare se la pila è vuota

**Implementazione**:
```c++
#include <iostream>

using namespace std;

// class Node goes here...

// class List goes here...

template <typename T>
class Stack {
    private:
        List<T> list; // Usa la lista per implementare la pila

    public:
        // Aggiunge un elemento in cima alla pila
        void push(T value) {
            list.push_head(value);
        }

        // Rimuove e restituisce l'elemento in cima alla pila
        T pop() {
            return list.extract_head();
        }

        // Controlla se la pila è vuota
        bool is_empty() const {
            return list.is_Empty();
        }

        // Stampa gli elementi nella pila
        void print_stack() const {
            list.print_list();
        }
};

int main() {
    Stack<int> stack;
    
    stack.push(10);
    stack.push(20);
    stack.push(30);

    stack.print_stack();

    cout << "Elemento rimosso: " << stack.pop() << endl;
    stack.print_stack();

    return 0;
}
```

##### Coda (o Queue)
>E' una struttura dati astratta nel quale le operazioni di inserimento e rimozione avvengono da due *lati diversi della coda*

E' una struttura dati di tipo **FIFO** (**F**irst **I**n **F**irst **O**ut), ossia il primo elemento inserito è il primo rimosso

Gli elementi costitutivi della coda sono:
- una **dimensione**
- un **puntatore** alla *head*
- un **puntatore** alla *tail*

Per i metodi si ha:
- `enqueue()`, inserimento in coda
- `dequeue()`, estrazione dalla coda

**Implementazione**:
```c++
#include <iostream>

using namespace std;

// class Node goes here...
// class List goes here...

template <typename T>
class Queue {
    private:
        List<T> list; // Usa la lista per implementare la coda

    public:
        // Aggiunge un elemento in fondo alla coda
        void enqueue(T value) {
            list.push_tail(value);
        }

        // Rimuove e restituisce l'elemento all'inizio della coda
        T dequeue() {
            return list.extract_head();
        }

        // Controlla se la coda è vuota
        bool is_empty() const {
            return list.is_Empty();
        }

        // Stampa gli elementi nella coda
        void print_queue() const {
            list.print_list();
        }
};

int main() {
    Queue<int> queue;
    
    queue.enqueue(10);
    queue.enqueue(20);
    queue.enqueue(30);

    queue.print_queue();

    cout << "Elemento rimosso: " << queue.dequeue() << endl;
    queue.print_queue();

    return 0;
}
```

## Alberi Binari e di Ricerca
### Alberi Binari
>Un **albero** è un grafo diretto in cui ogni nodo può avere un solo arco entrante e un qualunque numero di archi

Un nodo si dice:
- **foglia**, se non ha archi uscenti
- **radice**, se non ha archi entranti

Un *albero* è una struttura dati costituita da:
- una radice
- dei **rami**, gli archi dei nodi
- delle foglie

**Esempio**:
- ![[Pasted image 20240829120612.png|350]]

Per ogni **nodo**, i cerchi rappresentati nell'immagine con all'interno le lettere, si può stabilire una gerarchia *genitore*-*figlio*:
- il nodo $R$ rappresenta la *radice*
- i nodi $F$ rappresentano i *figli* della radice
- i nodi $N$ rappresentano i *nipoti* della radice
	- sono le *foglie* poiché non hanno figli 

**N.B.**: dato che si tratta di alberi binari, i nodi possono avere al più due figli o due archi uscenti

#### Caratteristiche e Proprietà
1. **Altezza e Livello dell'albero**

Sono due concetti strettamente collegati:
- il *livello dell'albero* è l'indice di profondità; la radice si trova al livello $0$, i suoi figli al livello $1$, ecc...
- l'*altezza dell'albero* è il numero di livelli totali oppure la lunghezza del suo cammino più lungo aumentata di uno

Esempio:
- ![[Pasted image 20240829120552.png|350]]

2. **Numero Massimo di Nodi**

Trattandosi di alberi binari, il conto per trovare il numero massimo di nodi conoscendo l'altezza dell'albero è:
- $n\leq 2^h-1$
	- $h$ è l'altezza dell'albero
	- $n$ è il numero di nodi

Un albero che ha esattamente $2^h-1$ nodi si dice **completo**, come quello nell'immagine precedente

3. **Albero Bilanciato**

>Un **sottoalbero** è l'albero che, fissato un nodo, *ha come radice il figlio del nodo*

Un albero si dice bilanciato quando la differenza tra l'altezza tra i due sottoalberi della radice è al più uno

**Esempio**:
- ![[Pasted image 20240830123546.png|350]]

**N.B.**: il sottoalbero di sinistra ha un indice di profondità (livello) maggiore rispetto al sottoalbero di destra di uno, dunque questo albero può dirsi bilanciato

### Alberi Binari di Ricerca
Gli **Alberi Binari di Ricerca** (o **BST** $\to$ **B**inary **S**earch **T**rees) sono alberi che hanno la seguente costituzione:
- per ogni nodo dell'albero, i valori del suo sottoalbero sinistro sono *minori del valore stesso*
- per ogni nodo dell'albero, i valori del suo sottoalbero destro sono *maggiori del valore stesso*

**Esempio**:
- *BST*
	- ![[Pasted image 20240830124757.png|250]]
- *Non BST*
	- ![[Pasted image 20240830124817.png|250]]


E' importante capire cos'è la **chiave di un nodo**:
>La **chiave di un nodo** in un albero binario, e in particolare in un albero binario di ricerca (BST), è il valore associato al nodo stesso 

-  Questi valori, o chiavi, determinano la posizione del nodo all'interno dell'albero secondo regole specifiche

**Implementazione**:
```c++
// class NodeBST
```

```c++
// class BST
```

