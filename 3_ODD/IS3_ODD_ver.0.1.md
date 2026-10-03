# ODD — Object Design Document — Progetto `IS3`

> **Scheletro 0.1 — da compilare.**
> Il deliverable del SOW si chiama "**cenni su ODD**": non serve un documento
> enorme. Serve dimostrare che sapete **progettare a oggetti in dettaglio**.
>
> **VINCOLO: 2 design pattern per team**, scelti **tra quelli presentati a lezione**.
> È ammesso **solo progettazione**: non è obbligatorio implementarli.
>
> ⚠️ **Verifica la lista dei pattern visti a lezione** (modulo M4, `05.01-…` e
> `06.02-Riuso e Design pattern….md` nella cartella madre) e usa solo quelli.
> Un pattern mai trattato è un rischio inutile.

| Object Design Document | `IS3` | |
|---|---|---|
| **Versione** | 0.1 | |
| **Data** | _gg/mm/aaaa_ | |
| **Autori** | _tutti_ | |
| **Stato** | bozza | |
| **RAD** | `IS3_RAD_ver._1.0` | |
| **SDD** | `IS3_SDD_ver._1.0` | |

---

## Revision History

| Data | Versione | Descrizione | Autori |
|---|---|---|---|
| _gg/mm_ | 0.1 | Prima stesura | _tutti_ |

---

## 1. Scopo del documento

_2 paragrafi. Questo documento passa dal design architetturale (SDD, "che struttura
ha il sistema") al design a oggetti ("quali classi esattamente, con quali
responsabilità, come collaborano, e con quali pattern"). _

---

## 2. Pattern implementato 1 — _Nome Pattern_

### 2.1 Definizione e pattern problem

_2 paragrafi. Qual è il problema, nella forma canonica del pattern, a cui il pattern
risponde? Non serve riscoprire il pattern: serve mostrare che avete riconosciuto il
problema nel VOSTRO dominio._

**Problema nel nostro sistema:** _..._

### 2.2 Obiettivo

> Il SOW chiede esplicitamente l'**obiettivo**: *a cosa serve questo pattern qui*.
> Una riga, netta.

_Il pattern serve a … perché in questo punto del sistema …_

### 2.3 Come sarebbe implementato

**Classi e ruoli:**

| Ruolo nel pattern | Classe | File | Responsabilità |
|---|---|---|---|
| _Subject_ | `_..._` | `_..._` | _..._ |
| _ConcreteSubject_ | `_..._` | `_..._` | _..._ |
| _Observer_ | `_..._` | `_..._` | _..._ |
| _ConcreteObserver_ | `_..._` | `_..._` | _..._ |

**Collaborazioni:** _quali classi istanziano quali, chi notifica cosa, in quale ordine._

**Diagramma:** _inserisci il diagramma UML delle classi del pattern, in
`design_pattern/` — sorgente modificabile + PNG._

**Codice (sketch, non obbligatorio):**

```java
// _es. sketch delle firme, non implementazione completa_
public interface _Notificatore_ {
    void _notifica_(String _messaggio_);
}

public class _Cliente implements _Notificatore_ {
    private final List<_Observer_> _osservatori_ = new ArrayList<>();

    public void _notifica_(String _messaggio_) {
        for (_Observer_ o : _osservatori_) { o._aggiorna_(_messaggio_); }
    }
}
```

### 2.4 Trade-off dell'uso del pattern

| | |
|---|---|
| **Vantaggio ottenuto** | _es. disaccoppiamento tra X e Y_ |
| **Costo pagato** | _es. complessità, curva di apprendimento, indirezione_ |
| **Design goal servito** | _DG-0?_ |
| **Alternativa scartata** | _es. callback diretto / if-else_ |

---

## 3. Pattern implementato 2 — _Nome Pattern_

<!-- STESSA STRUTTURA DEL PATTERN 1. Copia le sezioni 2.1-2.4. -->

### 3.1 Definizione e pattern problem
### 3.2 Obiettivo
### 3.3 Come sarebbe implementato
### 3.4 Trade-off dell'uso del pattern

---

## 4. Scelte di design a oggetti oltre ai pattern

<!-- Facoltativo ma utile: mostra maturità. Rivelazione di informazione,
     incapsulamento, responsabilità unica, composizione vs ereditarietà,
     interfacce e polimorfismo. 1-2 paragrafi. -->

_TBD_

---

## 5. Mappa oggetti → use case

> Collega questo documento al RAD: ogni classe qui deve essere tracciata a un
> requisito. È la stessa verifica che farà la matrice di tracciabilità.

| Classe | Use case | Requisito (RF/RNF) | Sottosistema (SDD) |
|---|---|---|---|
| _..._ | _UC-0?_ | _RF-0?_ | _SS-0?_ |

---

## 6. Glossario

| Termine | Definizione |
|---|---|
| _..._ | _..._ |

---

## Appendice — Catalogo dei pattern visti a lezione

<!-- Solo consultazione. NON è un deliverable: eliminalo prima di consegnare. -->

| Pattern | Tipo | Presentato in |
|---|---|---|
| _es. Strategy_ | _comportamentale_ | `06.02-Riuso e Design pattern….md` |
| _es. Observer_ | _comportamentale_ | `06.02-…_ |
| _es. Factory Method_ | _creazionale_ | `05.01/06.02-…_ |
| _es. Adapter_ | _strutturale_ | `06.02-…_ |
| _es. Facade_ | _strutturale_ | `06.02-…_ |
| _es. Singleton_ | _creazionale_ | `06.02-…_ |

> **Consiglio:** scegli 2 pattern **diversi tra loro** (uno comportamentale + uno
> creazionale o strutturale). Due pattern della stessa famiglia sembrano una scelta
> pigra e sono più difficili da distinguere in valutazione.
>
> **Attenzione a Singleton:** è il pattern più discusso del corso. Se lo scegli,
> devi saper dire perché in questo caso è accettabile e cosa alternative
> modernissime (enum singleton, dependency injection) farebbero meglio. Se non
> hai una risposta solida, **non sceglierlo**.