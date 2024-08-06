***
## OOP
### Astrazione
>E' un procedimento che consente di semplificare la realtà che si vuole modellare. La semplificazione avviene concentrando l'attenzione solo sugli elementi importanti del sistema complesso preso in considerazione

Terminologia:
- **Astrarre** significa semplificare delle entità complesse in *oggetti caratterizzati dalle caratteristiche e dalle funzionalità essenziali* per gli scopi preposti

### Information Hiding
>E' la capacità di una classe di incapsulare sia le caratteristiche (attributi) che i comportamenti (metodi) degli oggetti che rappresenta

Limita di molto gli errori rispetto alla programmazione strutturata

### Classe
>Una classe è un insieme di oggetti che condividono struttura e comportamento

Essa contiene:
- **attributi**, specifica dei dati che descrivono ogni oggetto che ne fa parte
- **metodi**, descrizione delle azioni che l'oggetto stesso è capace di eseguire

**Definizione**:
```c++
#include <iostream>
using namespace std;

// Definizione della classe
class MyClass {
private:
    int data;

public:
    // Costruttore
    MyClass(int data) : data(data) {}

    // Metodo per ottenere il valore dei dati
    int getData() const {
        return data;
    }

    // Metodo per impostare il valore dei dati
    void setData(int data) {
        this->data = data;
    }

    // Metodo per stampare i dati
    void display() const {
        cout << "Data: " << data << endl;
    }
};

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

#### Costruttore
>Ha lo stesso nome della classe e può avere qualunque numero di parametri. La particolarità è che non restituisce alcun tipo

E' bene che un oggetto si possa auto-inizializzare a seguito della sua creazione, senza dovere effettuare una successiva chiamata ad una sua qualche funzione membro

**N.B.**: C++ crea automaticamente un *costruttore di default* quando non vi sono altri costruttori, tuttavia esso non inizializza i membri della classe a valori predefiniti

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


#### Template di classi e funzioni
##### Template di Funzioni
>Così come una classe è un modello per istanziare oggetti a tempo di esecuzione, un **template** è un modello per istanziare classi o funzioni a tempo di compilazione

**Esempio**:
```c++
// swap function using a template

template <typename T>
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

#### Ereditarietà e Polimorfismo
>Una classe derivata eredita attributi e metodi dalla classe base già esistente

**Esempio**:
```c++
#include <iostream>
#include <string>

using namespace std;

// Super Classe
class MyClass {
protected:
    int data;
    string name;

public:
    // Costruttore con lista di inizializzazione
    MyClass(int data, string name) : data(data), name(name) {}

    // Metodo per ottenere il valore dei dati
    int getData() const {
        return data;
    }

    // Metodo per ottenere il nome
    string getName() const {
        return name;
    }

    // Metodo per impostare il valore dei dati
    void setData(int data) {
        this->data = data;
    }

    // Metodo per impostare il nome
    void setName(string name) {
        this->name = name;
    }

    // Metodo per stampare i dati
    void display() const {
        cout << "Data: " << data << ", Name: " << name << endl;
    }
};

// Sotto Classe
class DerivedClass : public MyClass {
private:
    double extraData;

public:
    // Costruttore con lista di inizializzazione che chiama il costruttore della classe base
    DerivedClass(int data, string name, double extraData) : MyClass(data, name), extraData(extraData) {}

    // Metodo per ottenere il valore di extraData
    double getExtraData() const {
        return extraData;
    }

    // Metodo per impostare il valore di extraData
    void setExtraData(double extraData) {
        this->extraData = extraData;
    }

    // Metodo per stampare i dati della classe derivata
    void display() const {
        // Chiamare il metodo display della classe base
        MyClass::display();
        cout << "Extra Data: " << extraData << endl;
    }
};

int main() {
    // Creazione di un oggetto della classe derivata
    DerivedClass obj(42, "Example", 3.14);

    // Utilizzo dei metodi della classe derivata
    obj.display();

    obj.setData(100);
    obj.setName("Updated Example");
    obj.setExtraData(6.28);
    cout << "Updated Data: " << obj.getData() << ", Updated Name: " << obj.getName() << ", Updated Extra Data: " << obj.getExtraData() << endl;

    // Utilizzo del metodo display della classe derivata
    obj.display();

    return 0;
}
```

**N.B.**: elementi *public* e *protected* vengono ereditati con le stesse proprietà, dunque rimangono o publici o protetti

#### Binding
>Si riferisce al collegamento tra una funzione chiamata e la funzione che viene effettivamente eseguita

Può essere:
- **statico**, se il collegamento avviene in fase di compilazione
- **dinamico**, se il collegamento avviene durante l'esecuzione

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
Definisce il *limite asintotico superiore* e si applica a delle funzioni $f$ con un limite asintotico superiore costituito dalla funzione di costo $g(n)$:
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

    int* array = new int [N];

    for(size_t i = 0; i < N; i++) {
        
        bool is_unique = true;
        do {
            array[i] = rand() % 20;
            
            // Check for duplicates
            for (size_t j = 0; j < i; ++j) {
            
                if (array[j] == array[i]) {
                    is_unique = false;
                    break;
                }
            }
        } while (!is_unique);
    }

    return array;
}

void print_Array(int* array) {

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

    while((found == false) && (start != end)) {
        int midpoint = (start + end)/2;
        
        if (array[midpoint] == key) {
            found = true;
        } else if (key < array[midpoint]) {
            end = midpoint - 1;
        } else {
            start = midpoint + 1;
        }
    }

    if(found) {
        cout << key << "found.";
    } else {
        cout << key << "not found.";
    }
}

int main() {

    srand(static_cast<unsigned>(time(NULL)));
    
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

        int j = i;
        while((j > 0) && (temp < array[j - 1])) {

            array[j] = array[j - 1];
            j--;

            cout << "\n\nArray:\n";
            for(size_t k = 0; k < N; k++) {
                cout << array[k] << " ";
            }
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
*Vantagggio*: e fico