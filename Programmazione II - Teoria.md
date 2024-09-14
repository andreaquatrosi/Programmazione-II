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
- **sotto-lineare** 
	- $O(n^c)$ con $c<1$, ossia la complessità per cicli annidati in base al numero di volte in cui vengono eseguite le istruzioni
	- **logaritmica**
		- $O(\log n)$, ossia la complessità di un ciclo quando le sue variabili sono incrementate o decrementate moltiplicandole o dividendole per una costante
		- ![[Pasted image 20240523110216.png|350]]
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
- ![[Pasted image 20240905163514.png|350]]

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

*Complessità*:
- caso migliore: $O(1)$
- caso medio: $O(n)$
- caso peggiore: $O(n)$

Un tipo di ricerca più efficiente è la *ricerca dicotomica* o **ricerca binaria**
spiegata in seguito:

##### Ricerca Dicotomica o Binaria
Si effettua una ricerca su un **array già ordinato**. Questa è un informazione importante dato che permette di:
- *suddividere l'array a metà* e controllare se la key è $>,=,<$ dell'elemento presente nel mezzo
- *ripetere le suddivisioni* fino a che non si avranno due elementi per il quale scegliere quello richiesto

**Algoritmo**:
```c++
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
```

*Complessità*:
- caso migliore: $O(1)$
- caso medio: $O(\log n)$
- caso peggiore: $O(\log n)$

#### Algoritmi Iterativi o di Ordinamento
L'algoritmo di ordinamento classico che si utilizza computa eseguendo un confronto tra due elementi in cui: se l'elemento `j`, successivo all'elemento `i`, è più piccolo allora si effettua lo scambio tra i due

**Algoritmo**:
```c++
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
```

##### Selection Sort
Quest'algoritmo prevede l'utilizzo di una variabile il cui contenuto è l'indice dell'elemento più piccolo, il quale verrà confrontato e aggiornato ad ogni occorrenza di un elemento ancora più piccolo

Finiti i confronti si effettua uno swap tra l'elemento fissato dal ciclo e l'elemento di indice minore

Si ripete il procedimento per la lunghezza dell'array

*Complessità:
- caso migliore: $O(n)$
- caso medio: $O(n^2)$
- caso peggiore: $O(n^2)$
*Vantaggio*: meno chiamate alla funzione swap e maggiore vantaggio in termini di efficienza

**Algoritmo**:
```c++
template <typename T>
void swap(T& a, T& b) {

    T t = a;
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
```

##### Insertion Sort
Quest'algoritmo prevede l'utilizzo di una variabile temporanea che immagazina un elemento dello array per confrontarlo con tutti quelli che lo precedono: se uno degli elementi che lo precede è più grande dell'elemento nella variabile temporanea, si effettua uno scambio

Si ripete questa logica e queste operazioni finché l'array non è ordinato

```c++
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
```

*Complessità*:
- caso migliore: $O(n)$
- caso medio: $O(n^2)$
- caso peggiore: $O(n^2)$

#### Algoritmi Ricorsivi di Ordinamento
Rispetto agli *algoritmi di ordinamento iterativi* sono più efficienti, in termini di complessità. Si basano sulla ricorsione e sulla logica *dividi et impera*

I passi del paradigma **dividi et impera** sono tre:
1. **Dividere**: *suddividere il problema in sottoproblemi*
2. **Conquistare**: *risolvere i sottoproblemi*
3. **Combinare**: *combinare le soluzioni dei sottoproblemi*

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
// Merge function to combine two sorted halves
template <typename T>
void merge(T arr[], int left, int mid, int right) {
    int n1 = mid - left + 1;
    int n2 = right - mid;

    // Create temporary arrays
    T *L = new T[n1];
    T *R = new T[n2];

    // Copy data to temporary arrays
    for (int i = 0; i < n1; ++i)
        L[i] = arr[left + i];
    for (int j = 0; j < n2; ++j)
        R[j] = arr[mid + 1 + j];

    // Merge the temporary arrays back into arr
    int i = 0; // Initial index of first subarray
    int j = 0; // Initial index of second subarray
    int k = left; // Initial index of merged subarray
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) {
            arr[k++] = L[i++];
        } else {
            arr[k++] = R[j++];
        }
    }

    // Copy the remaining elements of L[], if any
    while (i < n1) {
        arr[k++] = L[i++];
    }

    // Copy the remaining elements of R[], if any
    while (j < n2) {
        arr[k++] = R[j++];
    }

    // Free dynamically allocated memory
    delete[] L;
    delete[] R;
}

// Merge sort function
template <typename T>
void mergeSort(T arr[], int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;

        // Recursively sort first and second halves
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);

        // Merge the sorted halves
        merge(arr, left, mid, right);
    }
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

*Complessità*: nel **caso medio** $O(n\log n)$ mentre nel **caso peggiore** $O(n^2)$
*Vantaggio*: l'algoritmo è meno efficiente con $n$ molto grandi dato che prendere un elemento che sia il minimo o il massimo è molto meno probabile

**Algoritmo**:
```c++
// Function to swap two elements
template <typename T>
void swap(T &a, T &b) {
    T temp = a;
    a = b;
    b = temp;
}

// Partition function for quick sort
template <typename T>
int partition(T arr[], int low, int high) {
    T pivot = arr[high]; // Choose the rightmost element as pivot
    int i = low - 1; // Index of smaller element

    for (int j = low; j < high; ++j) {
        // If current element is smaller than or equal to pivot
        if (arr[j] <= pivot) {
            ++i; // Increment index of smaller element
            swap(arr[i], arr[j]);
        }
    }

    // Swap the pivot element with the element at (i + 1)
    swap(arr[i + 1], arr[high]);
    return (i + 1);
}

// Quick sort function
template <typename T>
void quickSort(T arr[], int low, int high) {
    if (low < high) {
        // Partition the array
        int pi = partition(arr, low, high);

        // Recursively sort elements before and after partition
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}
```

## OOP (Object Oriented Programming)
I principi di base di questo paradigma di programmazione sono:
- **astrazione**
- **information hiding** e **incapsulamento**
- **ereditarietà**
- **polimorfismo**

### 1. Astrazione
>E' un procedimento che consente di semplificare la realtà che si vuole modellare. La semplificazione avviene concentrando l'attenzione solo sugli elementi importanti del sistema complesso preso in considerazione

Terminologia:
- **Astrarre** significa semplificare delle entità complesse in *oggetti caratterizzati dalle caratteristiche e dalle funzionalità essenziali* per gli scopi preposti

### 2. Information Hiding
> E' la capacità di una classe di nascondere all'esterno i dettagli implementativi dei metodi di un oggetto

Limita di molto gli errori rispetto alla programmazione strutturata

#### 2.1 Incapsulamento
>E' la proprietà degli oggetti di incorporare al loro interno sia gli attributi (caratteristiche) che i metodi (comportamenti)

### Classe
>Una classe è un insieme di oggetti che condividono struttura e comportamento

Essa contiene:
- **attributi**, specifica dei dati che descrivono ogni oggetto che ne fa parte
- **metodi**, descrizione delle azioni che l'oggetto stesso è capace di eseguire

Gli attributi (o membri dato) non possono essere inizializzati all'atto della loro definizione ma si devono inizializzare ogni volta che si crea un'*istanza specifica* della classe mediante il **Costruttore** della classe

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

>L'**oggetto** è un'entità che ha un proprio stato e che può eseguire certe operazioni. Nello specifico, è un'*istanza* della classe che viene allocata in memoria

**N.B.**: i metodi **non** occupano spazio nell'istanza di un oggetto mentre gli attributi sì

#### Costruttore
>E' il metodo responsabile dell'istanziazione di un oggetto

**Caratteristiche**:
- ha lo stesso nome della classe
- non ha tipo di ritorno
- inizializza i valori degli attributi

**N.B.**: E' bene che un oggetto si possa auto-inizializzare a seguito della sua creazione, senza dovere effettuare una successiva chiamata ad una sua qualche funzione membro
**N.B.**$_{2}$: C++ crea automaticamente un *costruttore di default* quando non vi sono altri costruttori, tuttavia esso non inizializza i membri della classe a valori predefiniti

Ne esistono di tre tipi:
1. *Default*
	- serve per inizializzare gli attributi con dei valori di default
2. *Parametrizzato*
	- serve per inizializzare gli attributi con dei valori presi dai parametri
3. *Copia*
	- serve per inizializzare glli attributi con dei valori presi da un oggetto della stessa classe

#### Distruttore
>E' un metodo speciale che viene chiamato automaticamente quando si distrugge un oggetto; serve per liberare la memoria assegnata dal costruttore

**Caratteristiche**:
- stesso nome della classe preceduta dal simbolo ~
- non ha tipo di ritorno
- non accetta parametri
- non può essercene più di uno
- se non si dichiara, C++ ne crea uno in automatico

**N.B.**: il metodo Distruttore viene invocato alla chiusura del main automaticamente

##### Header File
>Separare in files diversi il codice "cliente" della classe dal codice della classe

##### Intestazione di classe
>Separare il codice sorgente di una classe in due files con lo stesso nome della classe
- uno con la definizione della classe (solo prototipi dei metodi) ed estensione **.h**
- un altro con le implementazioni dei metodi della classe ed estensione **.cpp**

#### Specificatori di Accesso
>Gli **specificatori di accesso** permettono di controllare la visibilità all'esterno di attributi e metodi

Si fa utilizzo delle parole chiavi:
- `private:`
	- possono essere acceduti solo dall'interno della classe
- `protected:`
	- possono essere acceduti anche da metodi di classi derivate
- `public:`
	- possono essere acceduti dall'esterno della classe

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
>E' lo strumento che permette di costruire nuove classi utilizzando quelle già sviluppate: una classe derivata **eredita** attributi e metodi dalla classe base già esistente

E' un ulteriore livello di astrazione che permette di avere un livello più alto rispetto a un interfaccia comune (*classe base*), grazie al al quale tutte le proprietà di questa classe vengono estese alle *classi derivate* (in quest'ultime si possono aggiungere nuove specifiche e funzionalità)

### 4. Polimorfismo
>Il **polimorfismo** indica la possibilità per i metodi di assumere forme, cioè implementazioni, diverse all'interno della gerarchia delle classi. 

E' la caratteristica grazie al quale oggetti di classi diverse rispondono in maniera diversa a uno stesso metodo

Due concetti fondamentali del polimorfismo nella OOP sono:
- l'*overloading* degli operatori
	- più funzioni con lo stesso nome ma con firme diverse (diverso numero o tipo di parametri)
- l'*overriding* delle funzioni
	- quando una classe derivata fornisce una specifica implementazione di un metodo che è già definito nella sua classe base: la versione del metodo nella classe derivata sostituisce quella della classe base quando viene chiamato su un oggetto della classe derivata


**N.B.**: ogni oggetto risponde alle chiamate ai metodi come specificato dal suo vero tipo

E' fondamentale associare il concetto di **binding**

#### Binding
>Si riferisce all'associazione tra una funzione chiamata e la funzione che viene effettivamente eseguita

Può essere:
- **statico** (default), se l'associazione avviene a *tempo di compilazione*
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

Per abilitarlo si antepone la clausola `virtual` alla dichiarazione di una funzione per indicare al compilatore che essa può essere definita in una classe derivata

*Vantaggio*: offre un alto grado di flessibilità e praticità nella gestione delle gerarchie di classi

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

>Permettono a una classe base di definire funzioni che possono essere **sovrascritte** (**overriding**) nelle classi derivate, con il comportamento corretto determinato a tempo di esecuzione

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

#### Classi Astratte
>Una **classe astratta** è una classe che contiene almeno un metodo puramente virtuale: come conseguenza, non si possono istanziare oggetti di una classe astratta

**Esempio**:
```c++
// Definizione di una classe puramente virtuale
class MyClass {
	private:
		int value;
		string a_string;

	public:
		virtual void myAbstractFunction() = 0;
};

class MyDerivedClass : public MyClass {
	private:
		// Ulteriori attributi

	public:
		void myAbstractFunction() {
			// Implementazione
		}
};

int main() {

	MyClass myObj; // NO
	MyDerivedClass myDerivedObj; // SI

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
>Così come una classe è un modello per istanziare oggetti a tempo di esecuzione, un **template** è un modello per istanziare classi o funzioni a tempo di compilazione

Permetto di implementare strutture (classi) e algoritmi (funzioni) indipendentemente dal tipo di oggetti su cui operano 

Il template implementa il concetto di *tipo parametrizzato*: il tipo viene specificato come se fosse un parametro

##### Template di Funzioni
>Sono funzioni in grado di operare su tipi generici

Il compilatore genererà più copie della stessa funzione per eseguire le chiamate con tipi di dato differenti

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
>Sono classi che hanno membri che usano i parametri del template come tipi

Il compilatore genera una classe diversa per ogni tipo per cui è richiesta la specializzazione

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
Vengono chiamati **insiemi dinamici**, insiemi manipolati dagli algoritmi che possono crescere, ridursi o cambiare nel tempo

>E' un insieme dinamico in cui una sequenza di elementi sono collegati l'uno all'altro da un puntatore

La differenza con l'array è che la lista *non viene preallocata* ma viene popolata a tempo di esecuzione poiché non ha una dimensione prefissata

*Vantaggio*: le liste si prestano bene a implementare sequenze dinamiche

La lista ha come elementi costitutivi dei **nodi** che contengono:
- un **valore**
- uno o più **puntatori**

##### 1. Liste Linkate Semplici
>E' una sequenza di nodi in cui ogni nodo ha un valore e un collegamento all'elemento successivo

Consentono di collegare fra loro nodi generati dinamicamente per costruire *liste semplici*

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
        Node<T>* get_next() { return next; }

        // Setter
        void set_value(const T value) { this->value = value; }
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

            delete nextNode;
        }

        // Operazioni
        bool is_empty() { return head == nullptr; }

        void push_head(const T value) {
            Node<T>* newNode = new Node<T>(value);

            if(this->is_empty()) {
                head = newNode;
                return;
            }

            newNode->set_next(head);
            head = newNode;
        }

        void push_tail(const T value) {

            Node<T>* newNode = new Node<T>(value);
  
            if(this->is_empty()) {
                head = newNode;
                return;
            }

            Node<T>* current = head;

            while(current->get_next() != nullptr)
                current = current->get_next();

            current->set_next(newNode);
        }

        void push_sorted(const T value) {

            Node<T>* newNode = new Node<T>(value);  

            if(this->is_empty() || value < head->get_value()) {
                newNode->set_next(head);
                head = newNode;
                return;
            }

            Node<T>* current = head;
            Node<T>* prev = nullptr;

            while(current != nullptr && value > current->get_value()) {
                prev = current;
                current = current->get_next();
            }

            newNode->set_next(current);

            if(prev != nullptr)
                prev->set_next(newNode);
        }

        T extract_head() {
        
            if(this->is_empty())
                exit(EXIT_FAILURE);

            Node<T>* temp = head;

            T value = head->get_value();
            head = head->get_next();

            delete temp;
  
            return value;
        }

        T extract_tail() {

            if(this->is_empty())
                exit(EXIT_FAILURE);

            Node<T>* temp = head;
            Node<T>* prev = nullptr;
            
            while(temp->get_next() != nullptr) {
                prev = temp;
                temp = temp->get_next();
            }

            T value = temp->get_value();

            if(prev != nullptr)
                prev->set_next(nullptr);

            delete temp;  

            return value;
        }

        bool extract_element(T value) {

            if(this->is_empty())
                exit(EXIT_FAILURE);

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

            if(temp == nullptr) // not found
                return false;

            // found
            if(prev != nullptr)
                prev->set_next(temp->get_next());
            else
                head = head->get_next();

            delete temp;  

            return true;
        }

        void print_list() const {  

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

    list.push_head(5);
    list.push_head(7);
    list.push_head(1);
    list.push_head(4);
    list.push_head(9);

    list.print_list();
  
    list.extract_head();
    list.print_list();
  
    list.extract_tail();
    list.print_list();

    list.extract_element(1);
    list.print_list();

    list.push_sorted(5);
    list.push_sorted(1);
    list.push_sorted(9);

    list.print_list();

    return 0;
}
```

##### 2. Liste Doppiamente  Linkate
>Sono liste che hanno un collegamento sia al nodo successivo che al nodo precedente

Consentono di collegare fra loro nodi generati dinamicamente per costruire *liste doppiamente concatenate* 

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
        Node() : value(T()), next(nullptr) {}
        Node(T value) : value(value), next(nullptr) {}

        // Getter
        T get_value() const { return value; }
        Node<T>* get_next() { return next; }
        Node<T>* get_prev() { return prev; }

        // Setter
        void set_value(const T value) { this->value = value; }
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
  
            while(current != nullptr) {
                nextNode = current->get_next();
                delete current;
                current = nextNode;
            }

            delete nextNode;
        }

        // Operazioni
        bool is_empty() { return head == nullptr; }

        void push_head(const T value) {
            
            Node<T>* newNode = new Node<T>(value);
            
            if(this->is_empty()) {
                head = tail = newNode;
                return;
            }

            newNode->set_next(head);
            head->set_prev(newNode);
            head = newNode;
        }

        void push_tail(const T value) {

            Node<T>* newNode = new Node<T>(value);

            if(this->is_empty()) {
                head = tail = newNode;
                return;
            }

            tail->set_next(newNode);
            newNode->set_prev(tail);
            tail = newNode;
        }

        void push_sorted(const T value) {

            Node<T>* newNode = new Node<T>(value);

            if(this->is_empty() || value < head->get_value()) {
                newNode->set_next(head);
                
                if(head != nullptr)
                    head->set_prev(newNode);

                head = newNode;

                if(tail == nullptr)
                    tail = newNode;
            }

            else if(value > tail->get_value()) {
                tail->set_next(newNode);
                newNode->set_prev(tail);
                tail = newNode;
            }

            else {
                Node<T>* current = head;

                while(current->get_next() != nullptr && value > current->get_next()->get_value()) {
                    current = current->get_next();
                }

                newNode->set_next(current->get_next());

                if(current->get_next() != nullptr) {
                    current->get_next()->set_prev(newNode);
                }
                current->set_next(newNode);
                newNode->set_prev(current);
            }
        }

        T extract_head() {

            if(this->is_empty())
                exit(EXIT_FAILURE);

            Node<T>* temp = head;

            T value = head->get_value();
            head = head->get_next();

            if(head != nullptr)
                head->set_prev(nullptr);
            else
                tail = nullptr;

            delete temp;  

            return value;
        }

        T extract_tail() {

            if(this->is_empty())
                exit(EXIT_FAILURE);

            Node<T>* temp = tail;

            T value = tail->get_value();
            tail = tail->get_prev();

            if(tail != nullptr)
                tail->set_next(nullptr);
            else
                head = nullptr;

            delete temp;  

            return value;
        }

        bool extract_element(T value) {

            if(this->is_empty())
                exit(EXIT_FAILURE);
                
            Node<T>* temp = head;

            while(temp != nullptr && value != temp->get_value())
                temp = temp->get_next();
                
            if(temp == nullptr) // not found
                return false;

            // found
            if(temp->get_prev() != nullptr)
                temp->get_prev()->set_next(temp->get_next());
            else
                head = temp->get_next();    // element is in the head

            if(temp->get_next() != nullptr)
                temp->get_next()->set_prev(temp->get_prev());
            else
                tail = temp->get_prev();    // element is in the tail

            delete temp;

            return true;
        }

        void print_list() const {

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

    list.push_sorted(50);
    list.push_sorted(20);
    list.push_sorted(60);
    list.push_sorted(30);
    list.push_sorted(40);

    list.print_list();

    list.extract_head();
    list.extract_tail();
    list.extract_element(30);

    list.print_list();

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
// Methods to use:
	// ~List() { if(!is_empty) pop(); }
	// push_head()
	// extract_head()

template <typename T>

class Stack {
    private:
        List<T> list; // Usa la lista per implementare la pila

    public:
        // Aggiunge un elemento in cima alla pila
        void push(T value) {
            list.push(value); // list.push_head()
        }
        
        // Rimuove e restituisce l'elemento in cima alla pila
        T pop() {
            return list.pop(); // list.extract_head()
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
// Methods to use:
	// ~List() { if(!is_empty) dequeue(); }
	// push_tail()
	// extract_head()

template <typename T>
class Queue {
    private:
        List<T> list; // Usa la lista per implementare la coda

    public:
        // Aggiunge un elemento in fondo alla coda
        void enqueue(T value) {
            list.enqueue(value); // list.push_tail()
        }

        // Rimuove e restituisce l'elemento all'inizio della coda
        T dequeue() {
            return list.dequeue(); // list.extract_head()
        }

        // Controlla se la coda è vuota
        bool is_empty() const {
            return list.is_Empty();
        }
  
        // Stampa gli elementi nella coda
        void print_queue() const {
            list.display();
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

**N.B.**: un grafo diretto è un insieme di nodi collegati mediante archi direzionati

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

Un albero si dice **bilanciato** quando la differenza tra l'altezza tra i due sottoalberi della radice è al più uno

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

*Tipologia* di albero:
- **albero binario degenere**, se ogni nodo diverso da una foglia ha un solo figlio (si assume che l'albero vuoto sia degenere)

E' importante capire cos'è la **chiave di un nodo**:
>La **chiave di un nodo** in un albero binario, e in particolare in un albero binario di ricerca (BST), è il valore associato al nodo stesso 

-  Questi valori, o chiavi, determinano la posizione del nodo all'interno dell'albero secondo regole specifiche

**Implementazione**:
```c++
// class NodeBST
template <typename T>
class Node {
    private:
        T key;
        Node<T>* left;
        Node<T>* right;

    public:
        Node() : key(T()), left(nullptr), right(nullptr) {}
        Node(T key) : key(key), left(nullptr), right(nullptr) {}

        // Getter
        T get_key() const { return key; }
        Node<T>*& get_left() { return left; }
        Node<T>*& get_right() { return right; }

        // Setter
        void set_key(const T key) { this->key = key; }
        void set_left(Node<T>* left) { this->left = left; }
        void set_right(Node<T>* right) { this->right = right; }
};
```

```c++
// class BST
template <typename T>
class BST {
    private:
        Node<T>* root;

        void add_node(Node<T>*& root, const T& key) {

            if(!root) {
                Node<T>* newNode = new Node<T>(key);
                root = newNode;

                return;
            }

            if(key < root->get_key())
                add_node(root->get_left(), key);
            else if(key > root->get_key())
                add_node(root->get_right(), key);
        }

        void delete_node(Node<T>*& root, const T& key) {

            if (!root)
                return;

            if (key < root->get_key())
                delete_node(root->get_left(), key);
            else if (key > root->get_key())
                delete_node(root->get_right(), key);
            else {
                Node<T>* toDelete = nullptr;

                if (!root->get_right() && !root->get_left()) {     // node has no children (leaf)
                    delete root;
                    root = nullptr;
                }

                else if (!root->get_left()) {                      // node has only right children
                    toDelete = root;
                    root = root->get_right();

                    delete toDelete;
                }

                else if (!root->get_right()) {                    // node has only left children
                    toDelete = root;
                    root = root->get_left();

                    delete toDelete;
                }

                else {                                            // node has both left and right children
                    Node<T>* smallestRight = get_minNode(root->get_right());

                    root->set_key(smallestRight->get_key());
                    delete_node(root->get_right(), smallestRight->get_key());
                }
            }
        }

        Node<T>* get_maxNode(Node<T>* root) {

            Node<T>* current = root;
            
            /* since it's a BST, all (key > root) will be the right node*/
            while(current->get_right())
                current = current->get_right();

            return current;
        }

        Node<T>* get_minNode(Node<T>* root) {

            Node<T>* current = root;  

            /* since it's a BST, all (key < root) will be the left node*/
            while(current->get_left())
                current = current->get_left();

            return current;
        }

        void inOrder(Node<T>* root) const {

            if(!root)
                return;

            inOrder(root->get_left());
            cout << root->get_key() << " ";
            inOrder(root->get_right());
        }

        void preOrder(Node<T>* root) const {

            if(!root)
                return;

            cout << root->get_key() << " ";
            preOrder(root->get_left());
            preOrder(root->get_right());
        }

        void postOrder(Node<T>* root) const {  

            if(!root)
                return;

            postOrder(root->get_left());
            postOrder(root->get_right());
            cout << root->get_key() << " ";
        }

        Node<T>* search_node(Node<T>*& root, const T& key) {  

            if(!root)
                return nullptr;

            if(key < root->get_key())
                return search_node(root->get_left(), key);
            else if(key > root->get_key())
                return search_node(root->get_right(), key);
            else
                return root;
        }

    public:
        BST() : root(nullptr) {}

        // Methods
        void add_node(const T& key) {
            add_node(root, key);
        }

        void delete_node(const T& key) {
            delete_node(root, key);
        }

        void inOrder() const {
            inOrder(root);
        }

        void preOrder() const {
            preOrder(root);
        }

        void postOrder() const {
            postOrder(root);
        }
};
```

La **ricerca di un elemento** di un BST ha *complessità* $O(h)$, dove $h$ è l'indice di profondità dell'albero (ossia il livello)

#### Visita dell'Albero
L'albero può essere visitato in tre modi diversi:
- visita **preorder**
- visita **postorder**
- visita **inorder**

Queste tre visite hanno in comune il fatto di essere procedure ricorsive, che si applicano ad ogni nodo

*Complessità*: $\Theta(n)$

##### Visita PreOrder
Prevede i seguenti passi:
- visitare la *radice*
- visitare il *sottoalbero sinistro*
- visitare il *sottoalbero destro*

**Esempio**:
- ![[Pasted image 20240901122514.png|350]]
- $10-4-2-1-3-6-5-7-16-12-14-18$

##### Visita PostOrder
Prevede i seguenti passi:
- visitare il *sottoalbero sinistro*
- visitare il *sottoalbero destro*
- visitare la *radice*

**Esempio**:
- ![[Pasted image 20240901122902.png|350]]
- $1-3-2-5-7-6-4-14-12-18-16-10$

##### Visita InOrder
Prevede i seguenti passi:
- visitare il *sottoalbero sinistro*
- visitare la *radice*
- visitare il *sottoalbero destro*

**Esempio**:
- ![[Pasted image 20240901123105.png|350]]
- $1-2-3-4-5-6-7-10-12-14-16-18$

## Grafi
>Si dice **grafo** un insieme di vertici legati "a due a due" da archi direzionati o non

**Terminologia**:
- $G=(V,E)$ dove:
	- $G$ è il grafo
	- $V$ è l'insieme dei *vertici* 
	- $E$ è l'insieme degli *archi* $(u,v)$
	- **Sottografo** $G^\prime=(V^\prime,E^\prime)$ di $G=(V,E)$ 
- **Cammino** (di lunghezza $k$) da $u$ a $v$ è la sequenza $v_{0},\dots,v_{k} :u=v_{o} \text{ e }v=v_{k}$, contentente anche gli archi $(v_{0},v_{1}),\dots,(v_{k-1},v_{k})$
	- **Cammino Semplice** è un cammino in cui tutti i vertici in esso contenuti sono distinti
- **Sottocammino** è la sequenza di vertici $v_{i},\dots,v_{j}$ di un cammino $v_{0},\dots v_{k}$ per cui $0\leq i\leq j\leq k$
- **Ciclo** è un cammino $v_{0},\dots,v_{k}$ per cui $v_{0} = v_{k}$
	- **Ciclo Semplice** è un ciclo in cui tutti i suoi nodi sono distinti
	- **Aciclico** è un grafo che non contiene cicli

### Grafo Non Direzionato
>Si dice **grafo non direzionato**, un grafo in cui ciascun arco collega i vertici da entrambe le direzioni

**Esempio**:
- ![[Pasted image 20240907131744.png|350]]

**Caratteristiche**:
- $E$ consiste di *coppie non ordinate* di vertici
- *Self-loops* non sono ammessi
- $(u,v)$, $u$ e $v$ sono sia entranti che uscenti (non hanno la freccia)
- l'adiacenza è *simmetrica*

#### Grado
>E' dato dal numero di archi entranti

#### Grafo Non Direzionato Connesso
>Un grafo non direzionato si dice **connesso** se ogni coppia di vertici è unita da un cammino

**N.B.**: un grafo direzionato è connesso se ha $1$ componente connessa

#### Grafo Non Direzionato Completo
>Un grafo non direzionato si dice **completo** se ogni coppia di vertici è adiacente

### Grafo Direzionato
>Si dice **grafo direzionato** un grafo in cui ciascun arco collega i vertici da una o più direzioni

**Esempio**:
- ![[Pasted image 20240907132325.png|350]]

**Caratteristiche**:
- $E$ consiste di *coppie ordinate* di vertici
- *Self-loops* sono ammessi
- $(u,v)$, $u$ e $v$ sono o entranti o uscenti (hanno la freccia)
- Se $(u,v)\in E$, $v$ è adiacente a $u$

#### Grado
> E' dato dal **numero di archi entranti** $+$ il **numero di archi uscenti**

#### Grafo Direzionato Fortemente Connesso
>Un grafo direzionato si dice **fortemente connesso** se per ogni coppia di vertici $(u,v)$ esiste un cammino che unisce $u$ a $v$ e $v$ a $u$

### Rappresentare un grafo
Esistono due modi principali per rappresentare un grafo:
1. **Liste di adiacenza**, utilizzate per rappresentare grafi con pochi archi
	- $O(\text{max}(|V|,|E|))=O(|V|+|E|)$ spazio
	- ![[Pasted image 20240907152738.png|250]]
1. **Matrici di adiacenza**, utilizzate per rappresentare grafi con molti archi
	- $O(|V|^2)$ spazio
	- ![[Pasted image 20240907152816.png|250]]

**N.B.**: $|V|$ la cardinalità di $V$, ossia un $n\in\mathbb N$ definito come il *numero di elementi che costituiscono l'insieme*

#### Liste di adiacenza
Per i **grafi non direzionati**:
- si definisce un array di $|V|$ liste, una per ogni vertice
- si definisce `adj[u]` contenente puntatori a tutti i vertici $v$ per i quali $(u,v)\in E$
- la somma delle lunghezze di tutte le liste è $2|E|$

**Esempio**:
- ![[Pasted image 20240907152646.png|350]]

Per i **grafi direzionati**:
- si definisce un array di $|V|$ liste, una per ogni vertice
- si definisce `adj[u]` contenente puntatori a tutti i vertici $v$ per i quali $(u,v)\in E$
- la somma delle lunghezze di tutte le liste è $|E|$

**Esempio**:
- ![[Pasted image 20240907152912.png|350]]

#### Matrici di adiacenza
Si ha che:
- $a=[a_{ij}]$
- $a_{ij}=1$ sse $(i,j)\in E$ ($0$ altrimenti)

**Esempio**:
- ![[Pasted image 20240907153105.png|350]]

### Ricerca
#### Ricerca In Ampiezza (Breadth - First - Search)
>L'algoritmo di **ricerca in ampiezza** (o **BFS**, **B**readth-**F**irst-**S**earch) è un metodo per attraversare o cercare i nodi di un grafo che si basa sull'esplorare tutti i nodi adiacenti al nodo corrente prima di muoversi verso i nodi successivi

**N.B.**: viene anche utilizzato per trovare la distanza minima tra due nodi in un grafo non pesato o per trovare i percorsi più brevi

**Esempio**: dato un vertice $s$, si esplora il grafo per scoprire ogni vertice $v$ raggiungibile da $s$

*Complessità*: $O(n+m)$ dove $n =$ numero di nodi e $m =$ numero di archi 

Per implementare questo tipo di ricerca si procede a step:

###### 1. Inizializzazione
- Si sceglie un nodo di partenza e lo si inserisce in una coda di nodi da visitare, tenendo traccia dei nodi già visitati

###### 2. Iterazione Principale
- Finché la coda non è vuota, si estrae un nodo dalla coda: il nodo estratto rappresenta il nodo corrente da esaminare
- Si visitano i nodi adiacenti a questo nodo corrente che non sono stati visitati e li si aggiungono alla coda

###### 3. Segnare i Nodi Visitati
- Ogni volta che si visita un nodo, lo si marca come visitato
- Questo può essere fatto mantenendo una lista di nodi visitati o segnando i nodi stessi

###### 4. Ripetere per l'Intero Grafo
Si continua il passo **2.** finché ci sono nodi nella coda o finché non sono stati visitati tutti i nodi accessibili dal nodo di partenza

###### 5. Risultato
Si ottiene un **albero di visita** (o **albero di copertura in ampiezza**) che copre tutti i nodi raggiungibili dal nodo di partenza

##### Breadth-First-Tree
>La procedura $BFS(G,s)$ serve a costruire un albero rappresentante i predecessori di ciascun nodo

**Caratteristiche** $G_{p}=(V_{p},E_{p})$:
- $V_{p}=\{ v\in V :p[v]\neq \\text{NULL}\}$
- $E_{p}=\{ (p[v],v)\in E:v\in V_{p},v\neq s \}$

$G_{p}$ è un albero in cui:
- c'è un unico cammino da $s$ a $v\in V_{p}$ che è anche il cammino più breve
- gli archi in $E_p$ sono chiamati *tree-edges*

#### Ricerca in Profondità (Depth - First - Search)
>L'algoritmo di **ricerca in profondità** (o **DFS**, **D**epth-**F**irst-**S**earch) è un metodo per attraversa o cercare i nodi di un grafo che si basa sull'esplorare più in profondità possibile lungo un ramo del grafo prima di tornare indetro e esplorare gli altri rami

Gli archi sono esplorati a partire dal nodo $v$ che:
- è stato scoperto più di recente
- abbia ancora archi (uscenti) non esplorati

Quando gli archi di $v$ terminano, si fa *backtracking*:
- si esplorano eventuali altri archi (uscenti) dal nodo precedente a $v$

Si ripete il processo fin quando vi sono nodi da esplorare

*Complessità*: $\Theta(V+E)$

Per implementare questo tipo di ricerca si procede a step:

###### 1. Inizializzazione
- Si sceglie un nodo di partenza e lo si marca come visitato, tenendo traccia dei nodi già visitati

###### 2. Iterazione Principale
- Si visitano un nodo adiacente non visitato dal nodo corrente
- Si continua finché non si raggiunge un nodo senza nodi adiacenti non visitati
- Si fa backtracking fino a trovare un nodo con nodi adiacenti non visitati
###### 3. Segnare i Nodi Visitati
- Ogni volta che si visita un nodo, lo si marca come visitato
- Questo può essere fatto mantenendo una lista di nodi visitati o segnando i nodi stessi

###### 4. Ripetere per l'Intero Grafo
Si continua il passo **2.** finché non sono stati visitati tutti i nodi

###### 5. Risultato
Si ottiene un **albero di visita** (o **albero di copertura in profondità) che copre tutti i nodi raggiungibili dal nodo di partenza

##### Depth-First-Forest
>La procedura $BFS(G,s)$ serve a costruire un albero rappresentante i predecessori di ciascun nodo

$G_{p}$ è una foresta in cui:
- $V_{p}=V$
- $E_{p}=\{ (p[v],v)\in E:v\in V,p[v]\neq \text{NULL} \}$

## Costrutti del C++
### Puntatori e Riferimenti
#### Riferimenti
> Il **riferimento** ad una variabile è un ulteriore nome per essa, un "alias"

Essa dev'essere inizializzata contestualmente alla sua definizione con il nome di una variabile già definita dello stesso tipo

#### Puntatori
>Il **puntatore** è una variabile di *tipo puntatore al tipo $x$* che contiene l'indirizzo di memoria di una variabile di *tipo $x$*

##### Aritmetica dei Puntatori
Se si incrementa un puntatore a un tipo $x$ di $n$, il suo valore aumenta di $n\times \text{sizeof}(T)$

##### Puntatori a Funzioni
E' possibile creare dei puntatori che puntino alle funzioni

**N.B.**: questi particolari puntatori puntano alla prima istruzione del blocco istruzioni della funzione