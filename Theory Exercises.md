Consideriamo la seguente semplice implementazione di una lista concatenata cosa effettua la funzione boo()?

```c++
	class Nodo{  
	    public:  
	        Nodo* succ;  
	        int valore;  
	};

	class ListaConcatenata{  
	    public:  
	        Nodo* testa;  
	};

	void boo(Nodo* testa){  
	    if(testa==nullptr) return;  
	    boo(testa->succ);  
	    cout<<testa->valore<<endl;  
	}

```
    
-  Se testa è un puntatore nullo non fa niente altrimenti stampa il valore che contiene
- Se testa corrisponde alla testa di una lista concatenata stampa tutto il contenuto della lista dalla testa alla coda.
- Se testa corrisponde alla testa di una lista concatenata stampa tutto il contenuto della lista in ordine inverso *esatto*
- Il codice contiene un errore e non può essere compilato.

L'ultima riga della seguente funzione inverti() ha una istruzione mancante. Quale di queste istruzioni dovrebbe essere inserita alla fine della procedura per permettere alla funzione inverti() di invertire l'ordine degli elementi dalla lista concatenata la cui testa è data in input?
 
```c++
/*testa punta alla testa di una lista concatenata*/  
void inverti(Nodo* testa)  
{  
    Nodo* prev = nullptr;  
    Nodo* current = *testa;  
    Nodo* next;  
    while(current!=nullptr){  
        next = current->succ;  
        current->succ=prev;  
        prev=current;  
        current=next;  
    }  
    //AGGIUNGERE RIGA QUI  
}

```

- testa = prev; *esatta*
- testa = current;
- testa = next;
- testa = nullptr;

Supponendo che il parametro p passato alla funzione func() sia la testa di una lista concatenata la funzione func() restituisce il valore 1 se e solo se:
```c++
Nodo{  
    public:  
        int valore;  
        Nodo *=succ;  
}; 

int func(Nodo* p){  
    return (p==nullptr || p->succ==nullptr || 
           ((p->valore <= p->succ->valore && func(p->succ))));  
}

```
 
- Gli elementi della lista sono tutti diversi   
- Gli elementi della lista sono ordinati in maniera non decrescente *esatta*
- Gli elementi della lista sono ordinati in maniera non crescente
- Nessuna delle precedenti

Supponiamo di avere i puntatori al primo e all'ultimo elemento di una lista concatenata semplice. Quale di queste operazioni ha un costo che dipende dalla lunghezza della lista?
    
- Eliminare il primo elemento
- Inserire un nuovo elemento in testa
- Eliminare l'ultimo elemento della lista *esatta*
- Aggiungere un nuovo elemento alla fine della lista

Nel caso peggiore qual è il numero di confronti necessari per la ricerca di un elemento all'interno di una lista concatenata semplice?
    
- log n
- n/2
- log(n-1)
- n *esatta*

Qual è il numero minimo di campi per ciascun nodo di una lista doppiamente linkata?
- 1
- 2
- 3 *esatta* -> value, next, prev
- 4

Una lista doppiamente linkata è definita usando la classe nodo seguente dove prec e succ rappresentano i puntatori agli elementi adiacenti. Quale dei seguenti segmenti di codice deve essere eseguito per eliminare correttamente il nodo puntato da X assumendo che X non punti né all'inizio né alla fine della lista?

```c++
Nodo {  
    public:  
        int valore;  
        Nodo *succ;  
        Nodo *prec;  
};

```
 
- X->prec->succ = X->succ; X->succ->prec = X->prec *esatta*
- X->prec.succ = X->succ; X.succ->prec = X->prec;
- X.prec->succ = X.prec; X->succ.prec = X.prec;
- X->prec->succ = X->prec; X->succ->prec = X->succ;

Quale di queste strutture dati implementa una politica LIFO?

- BST
- Coda
- Stack *esatta*
- Lista

L'implementazione di una pila con un array statico

- Trasforma la pila in una coda
- Limita la dimensione massima della pila *esatta*
- Consente di effettuale tutte le operazioni in tempo costante
- Non è possibile

Qual è la complessità di questa funzione?

```c++
func(int n)  
{  
    if(n==1) return;  
    for(int i=1;i<=n; i++)   
    {  
        for(int j=1;j<=n;j++)  
        {  
            cout<<"@@@";  
            break;  
        }  
    }  
}

```

- O(N) *esatta*
- O(sqrt(N))
- O(N/2)
- O(logN)

Qual è la complessità di questa funzione?

```c++
func(int n)  
void func(int n)  
{  
    int count=0;  
    for(int i=n/2;i<=n;i++)   
        for(int j=1;j<=n;j=2*j)   
            for(int k=1;k<=n;k=k*2)   
                count++;  
}

```

- O(n^2)
- O(n log^2 n) *esatta*
- O(n log n)
- O(log n)

Come eredita i membri public e protected della classe A?

```c++
Class A {

    int a;

	protected:
	    char b:
         …

     public:
        float c;
          …
};

Class B : private A {
          …
};
```

- Risposta: li eredita con scope private, ciò significa che b e c saranno accessibili all'interno di B ma non al di fuori

Una classe astratta è una classe che:
- Risposta: contiene solamente la firma / la definizione di funzioni che devono essere implementate da classi ereditarie, promuovendo così il polimorfismo e il riutilizzo del codice

Ogni algoritmo di ordinamento basato su confronti richiede:

- nlog(n) passi *esatta*
- n^2
- log(n) passi
- Nessuna delle precedenti

Cosa fa il seguente codice?

- ![[Pasted image 20240902115317.png|350]]

- Stampa ricorsivamente tutti i figli destri a partire dalla radice.
- Stampa ricorsivamente la chiave del parent fino alla radice poi stampa tutte le chiavi del figlio.
- Questo frammento non puo essere compilato.
- Stampa le chiavi della root all’infinito. *esatta*