# RAD — Requirements Analysis Document — Progetto `IS3`

> **Scheletro 0.1 — da compilare.**
> La gerarchia dei titoli è **imposta dal check-list del docente**: non riorganizzarla,
> non aggiungere o rimuovere sezioni di primo livello.
> Sostituisci `IS3` con la sigla del progetto, `TBD` con il contenuto.

| Requirements Analysis Document | `IS3` | |
|---|---|---|
| **Versione** | 0.1 | |
| **Data** | _gg/mm/aaaa_ | |
| **Autori** | _Cognome1, Cognome2, Cognome3_ | |
| **Stato** | bozza | |
| **SoW di riferimento** | `IS3_SOW_ver._1.0` | data |

---

## Revision History

| Data | Versione | Descrizione | Autori |
|---|---|---|---|
| _gg/mm/aaaa_ | 0.1 | Prima stesura | _tutti_ |
| | | | |

---

## Team

| Membro | Use case assegnato | Sequence diagram | Statechart | Unit test (metodo) | System test (funzionalità) |
|---|---|---|---|---|---|
| _Cognome1_ | _UC-01_ | _SD-01_ | _SC-01_ | _UT-01_ | _ST-01_ |
| _Cognome2_ | _UC-02_ | _SD-02_ | _SC-02_ | _UT-02_ | _ST-02_ |
| _Cognome3_ | _UC-03_ | _(si divide con il 2)_ | _(si divide con il 1)_ | _UT-03_ | _ST-03_ |

> **2 membri → 1 sequence diagram; 3 membri → 2.** I sequence diagram si dividono
> a coppie: se i membri sono A, B, C allora A+B fanno il primo e C il secondo
> (oppure A+C e B). Decidetelo e scrivetelo: è la prova che avete razionalizzato
> un vincolo dispari. Lo stesso ragionamento vale per i 2 statechart.

---

# 1. Introduzione

## 1.1 Obiettivo del Sistema

<!-- 2-4 paragrafi. Quale problema reale risolve il sistema, per chi, e perché
     la sua esistenza è giustificata. Rispondi alla domanda "che cosa sarebbe
     successo se questo sistema non esistesse". -->

_TBD_

## 1.2 Ambito del Sistema

<!-- Definizione del SYSTEM BOUNDARY: cosa è dentro, cosa è fuori.
     È la sezione più difficile del RAD e quella più valutata.
     Elenca esplicitamente gli attori, il sistema, e tutto ciò che è esterno. -->

| Dentro il boundary | Fuori dal boundary |
|---|---|
| _es. autenticazione utenti_ | _es. il servizio email di terze parti_ |
| _es. catalogo_ | _es. il sistema di pagamento_ |

**Attori (stakeholder):**

| Attore | Tipo | Descrizione |
|---|---|---|
| _es. Utente Registrato_ | primario | _..._ |
| _es. Amministratore_ | secondario | _..._ |
| _es. Sistema di terze parti_ | esterno | _..._ |

## 1.3 Obiettivi e Criteri di Successo

<!-- Obiettivi misurabili. "Il sistema deve essere usabile" NON è un obiettivo.
     "Ridurre il tempo di inserimento da 5 minuti a 30 secondi" sì. -->

| # | Obiettivo | Criterio di successo (misurabile) |
|---|---|---|
| 1 | _..._ | _..._ |
| 2 | _..._ | _..._ |

## 1.4 Definizioni, Acronimi e Abbreviazioni

<!-- NON SPECIFICATO nel documento ma presente nel glossario finale. Inserisci
     TUTTO quello che userai e che non è parola comune nel contesto informatico. -->

| Termine | Definizione |
|---|---|
| _TBD_ | _..._ |

## 1.5 Riferimenti

| Documento | Versione | Data | Ruolo |
|---|---|---|---|
| `IS3_SOW_ver._1.0` | 1.0 | _gg/mm_ | perimetro e vincoli |
| _prototipo / sito esistente analizzato_ | — | — | sistema attuale |
| _standard / regolamento_ | — | — | requisiti di legge |

## 1.6 Organizzazione del Documento

<!-- Una riga per capitolo. Serve al lettore e lo chiede il check-list. -->

| Capitolo | Contenuto |
|---|---|
| 1 | Introduzione: obiettivo, ambito, criteri di successo |
| 2 | Sistema attuale: analisi di [X] |
| 3 | Sistema proposto: requisiti e modello |
| 4 | Glossario |

---

# 2. Sistema attuale

<!-- Se il progetto è greenfield, il "sistema attuale" è il processo umano che
     oggi si usa. NON scrivere "non esiste". La sostituzione del processo manuale
     è esattamente il caso d'uso classico di un sistema nuovo. -->

**Processo attuale:** _descrivi come si fa oggi, passo dopo passo_

**Problemi identificati:**

| # | Problema | Impatto | Gravità |
|---|---|---|---|
| 1 | _es. dati duplicati tra due registri_ | _perdita di informazioni_ | Alta |
| 2 | _..._ | _..._ | _..._ |

**Chi è coinvolto e come lavora oggi:** _..._

---

# 3. Sistema proposto

## 3.1 Sintesi della sezione

<!-- 4-6 righe. Quale sistema proponiamo e in quali parti è diviso.
     Non è il sommario dei requisiti: è la mappa della sezione. -->

_TBD_

---

## 3.2 Requisiti Funzionali

> **VINCOLO: da 6 a 12** (2–4 per membro × 3 membri).
> **Non contarne meno di 6** — è il numero minimo legale, non un'indicazione.

**Regole di scrittura** (dal modulo M2):

- Sintassi: `[Condizione] [Soggetto] [Azione] [Oggetto] [Vincolo]`
- Forma **attiva**, enunciati **positivi**
- **Mai** scrivere *"il sistema deve essere in grado di…"* o *"must"*: il requisito
  è *cosa deve fare il sistema*, non cosa deve poter fare
- **Il soggetto è il sistema**, non l'utente: *"Il sistema registra l'utente"*, non
  *"L'utente registra-se stesso"*
- Un requisito = una riga = una funzione. Se la riga contiene "e", sono due requisiti.

| ID | Requisito funzionale | Fonte | Priorità | Assegnato a | Use case |
|---|---|---|---|---|---|
| RF-01 | _Il sistema …_ | _SOW/ stakeholder_ | Alta | _Cognome_ | _UC-01_ |
| RF-02 | _Il sistema …_ | | Alta | | _UC-01_ |
| RF-03 | _Il sistema …_ | | Media | _Cognome_ | _UC-02_ |
| RF-04 | _Il sistema …_ | | Media | | _UC-02_ |
| RF-05 | _Il sistema …_ | | Media | _Cognome_ | _UC-03_ |
| RF-06 | _Il sistema …_ | | Media | | _UC-03_ |
| RF-07 | _Il sistema …_ | | Bassa | _Cognome_ | _UC-03_ |
| _RF-08..RF-12_ | _fino a 4 per membro_ | | | | |

**Totale: _6-12_. Assegnati: _2-4 per membro_.**

---

## 3.3 Requisiti Non Funzionali

> **VINCOLO: da 6 a 12** (2–4 per membro × 3 membri).
>
> ⚠️ **Tutte e 9 le sottosezioni devono esistere e avere contenuto.**
> Anche "Prestazioni" e "Legali". Se un requisito non è applicabile,
> si scrive *"non applicabile — sistema didattico, nessun vincolo"* e si passa.
> Una sezione **vuota** è una check-list non soddisfatta.

### 3.3.1 Usabilità

| ID | Requisito | Criterio di verifica |
|---|---|---|
| RNF-01 | _Il sistema …_ | _come lo si misura_ |

### 3.3.2 Affidabilità

| ID | Requisito | Criterio di verifica |
|---|---|---|
| RNF-02 | _Il sistema …_ | _..._ |

### 3.3.3 Prestazioni

| ID | Requisito | Criterio di verifica |
|---|---|---|
| RNF-03 | _es. Il sistema risponde a una ricerca in meno di 2 secondi con 10.000 record_ | _test di carico_ |

> Nota: le prestazioni sono ciò che distingue un progetto serio. Scrivile qui,
> anche se poi l'implementazione non le raggiunge: **in RAD si specifica la
> desiderata, non quella che si è riusciti a fare.**

### 3.3.4 Supportability

| ID | Requisito | Criterio di verifica |
|---|---|---|
| RNF-04 | _Il codice è … / il sistema è manutenibile tramite …_ | _code coverage_ |

### 3.3.5 Implementazione

| ID | Requisito | Criterio di verifica |
|---|---|---|
| RNF-05 | _Il sistema è sviluppato in Java 17 con build Maven_ | _esistenza del pom.xml_ |

### 3.3.6 Interfacce

| ID | Requisito | Criterio di verifica |
|---|---|---|
| RNF-06 | _Il sistema espone interfaccia web su … / interagisce con …_ | _..._ |

### 3.3.7 Operation

| ID | Requisito | Criterio di verifica |
|---|---|---|
| RNF-07 | _Il sistema si installa con … / richiede …_ | _..._ |

### 3.3.8 Packaging

| ID | Requisito | Criterio di verifica |
|---|---|---|
| RNF-08 | _Il sistema è distribuito come …_ | _..._ |

### 3.3.9 Legali

<!-- Spesso sottovalutata. In un progetto didattico basta dichiarare cosa NON
     si fa e su quale base. Ma la sezione deve esistere. -->

| ID | Requisito | Criterio di verifica |
|---|---|---|
| RNF-09 | _es. Nessun dato personale è conservato oltre la sessione, ai sensi del Reg. UE 2016/679_ | _revisione del modello dati_ |

---

## 3.4 Modello del Sistema

### 3.4.1 Scenari

> **VINCOLO: da 6 a 12 scenari** (2–4 per membro).
>
> ⚠️ **Uno scenario NON è un caso d'uso.** Lo scenario è *un'istanza concreta*,
> con valori reali: *"Mario Rossi si registra il 3 ottobre con email
> mario.rossi@studenti.unisa.it e password XXXX"*.
>
> **Errore tipico da evitare:** scrivere 12 casi d'uso e 3 scenari generici.
> Il numero che il docente conta è lo **scenario**, e devono essere ≥ 2 per membro.

| ID | Scenario | Use case | Membro |
|---|---|---|---|
| SC-01 | _Nome persona: azione concreta, con valori_ | _UC-01_ | _Cognome_ |
| SC-02 | _..._ | _UC-01_ | |
| SC-03 | _..._ | _UC-02_ | _Cognome_ |
| SC-04 | _..._ | _UC-02_ | |
| SC-05 | _..._ | _UC-03_ | _Cognome_ |
| SC-06 | _..._ | _UC-03_ | |

**Struttura consigliata per ogni scenario** (traccia → precondizione → postcondizione):

```
ID          : SC-01
Use case    : UC-01
Attore      : Attore X
Trigger     : <cosa fa scattare il caso d'uso>
Precondizioni: <cosa deve essere vero prima>
Flusso principale:
   1. L'attore ...
   2. Il sistema ...
   3. ...
Postcondizioni: <cosa è vero dopo>
Alternative / eccezioni: <i flussi non nominali>
```

---

### 3.4.2 Modello dei Casi d'Uso

> **VINCOLO: ESATTAMENTE 3 use case** (1 per membro).
> I casi d'uso in più **non saranno valutati**. 3, non 5.

**Diagramma:** `diagrammi/use_case/`

| ID | Use case | Attore principale | Attori secondari | Scenuri associati | Membro |
|---|---|---|---|---|---|
| UC-01 | _Registrazione utente_ | _Attore X_ | _Attore Y_ | SC-01, SC-02 | _Cognome1_ |
| UC-02 | _…_ | | | SC-03, SC-04 | _Cognome2_ |
| UC-03 | _…_ | | | SC-05, SC-06 | _Cognome3_ |

> Nel diagramma UML i casi d'uso stanno **dentro** il boundary di sistema e gli
> attori **fuori**, collegati con associazioni. Le relazioni `<<include>>` e
> `<<extend>>` sono facoltative: usarle solo se servono davvero.

---

### 3.4.3 Modello ad Oggetti

**Diagramma delle classi:** `diagrammi/class/` — **1 per team**.

> ⚠️ Gli **object diagram non verranno valutati**. Non produrli.

| ID | Classe | Tipo | Attributi principali | Metodi principali | Use case |
|---|---|---|---|---|---|
| CL-01 | _…_ | Entity | | | _UC-0x_ |
| CL-02 | _…_ | Control | | | |
| CL-03 | _…_ | Boundary | | | |

**Criteri di qualità del diagramma:**
- [ ] Le classi **Entity** hanno attributi e metodi di dominio (`es. Utente.registra()`)
- [ ] Le classi **Control** orchestrano gli use case, non contengono logica di dominio
- [ ] Le classi **Boundary** corrispondono a elementi di interfaccia
- [ ] Le associazioni hanno **molteplicità** e **ruolo** espliciti
- [ ] Non ci sono classi con una sola parola come nome (`Manager`, `Helper`, `Util`)

**Specifica degli oggetti boundary, control, entity** (richiesta dal SOW):

| Use case | Boundary | Control | Entity coinvolte |
|---|---|---|---|
| UC-01 | | | |
| UC-02 | | | |
| UC-03 | | | |

---

### 3.4.4 Modello Dinamico

> Tre tipi di diagrammi, con vincoli **distinti e non intercambiabili**.
> Non confonderli: il docente li conta separatamente.

#### Activity Diagrams — `diagrammi/activity/`

> **ESATTAMENTE 1 per team.**

| ID | Descrizione | Attività principale modellata |
|---|---|---|
| AD-01 | _…_ | _es. il processo di registrazione dall'inizio alla fine_ |

> L'activity diagram modella un **processo/flusso di attività**, con decisioni e
> swimlane se più attori partecipano. È l'unico dei tre che ha «attività» e
> «decisione» come nodi.

#### Sequence Diagrams — `diagrammi/sequence/`

> **ESATTAMENTE 1 ogni 2 membri → 2 diagram.** Devono riferirsi agli use case specificati.

| ID | Use case di riferimento | Attori coinvolti | Membro |
|---|---|---|---|
| SD-01 | _UC-0?_ | | _Cognome1+2_ |
| SD-02 | _UC-0?_ | | _Cognome3_ |

> Il sequence diagram è **interazione nel tempo**: lifelines, messaggi con ordine
> numerato, risposte, e **activation bar** per mostrare la durata delle operazioni.
> Deve mostrare i boundary, i control e le entity che collaborano.

#### Statechart Diagrams — `diagrammi/statechart/`

> **ESATTAMENTE 1 ogni 2 membri → 2 diagrammi.**

| ID | Oggetto di cui descrive gli stati | Membro |
|---|---|---|
| SC-01 | _es. il ciclo di vita dell'ordine: creato → confermato → spedito → consegnato_ | _Cognome1+2_ |
| SC-02 | _es. il ciclo di vita dell'utente: registrato → verificato → sospeso_ | _Cognome3_ |

> Lo statechart descrive **gli stati di un singolo oggetto** e le transizioni
> con **guard** (condizioni) e **azioni**. È diverso dal sequence diagram:
> il sequence dice *chi chiama chi*, lo statechart dice *in che stato si è e come
> si transita*.

---

### 3.4.5 Interfaccia Utente — Percorsi di Navigazione e Mock-up

**Percorsi di navigazione** (testo, tabella):

| Percorso | Partenza | Azioni | Arrivo | Use case |
|---|---|---|---|---|
| P-01 | _homepage_ | _click → login → registrazione_ | _profilo creato_ | _UC-01_ |

**Mock-up:** `diagrammi/ui_mockup/`

> Non serve un design professionale. Servono schermate ** Wireframe ** che mostrino:
> - i campi di input e i pulsanti
> - i messaggi di errore di validazione
> - lo stato vuoto / caricamento / errore
>
> Il mock-up serve a collegare i casi d'uso a ciò che l'utente vede. È il ponte
> fra RAD e design.

---

# 4. Glossario

<!-- Il check-list chiede esplicitamente: "Ogni concetto introdotto è stato
     definito nel Glossario?" — quindi il glossario è valutato. -->

| Termine | Definizione |
|---|---|
| _TBD_ | _..._ |

---

# Appendice A — Tracciabilità interna al RAD

<!-- Collega RF/RNF → UC → Scenario → Test. La matrice completa, che arriva
     fino ai deliverable di design e testing, sta in 4_Matrice_Tracciabilita/. -->

| Requisito | Use case | Scenario | Caso di test previsto |
|---|---|---|---|
| RF-01 | UC-01 | SC-01 | _ST-01_ |
| RF-02 | UC-01 | SC-02 | |
| RF-03 | UC-02 | SC-03 | _ST-02_ |
| _…_ | | | |

---

# Appendice B — Check-list di conformità (autocontrollo)

<!-- NON sostituisce 1_RAD/IS3_CL_RAD.md: è il riassunto rapido.
     La check-list ufficiale va compilata per intero. -->

- [ ] Nessun requisito contiene la parola "deve poter" / "must"
- [ ] Tutti i requisiti sono in forma attiva con soggetto esplicito
- [ ] I termini usati sono definiti in §1.4 e nel Glossario
- [ ] Esistono 6-12 requisiti funzionali (2-4 per membro)
- [ ] Esistono 6-12 requisiti non funzionali (2-4 per membro)
- [ ] Esistono 6-12 scenari (2-4 per membro)
- [ ] Esistono **esattamente** 3 use case (1 per membro)
- [ ] Esistono **esattamente** 2 sequence diagram
- [ ] Esistono **esattamente** 2 statechart diagram
- [ ] Esiste **esattamente** 1 activity diagram
- [ ] Esiste **esattamente** 1 class diagram
- [ ] Nessun object diagram è stato prodotto
- [ ] Tutte e 9 le sottosezioni dei RNF hanno contenuto
- [ ] Ogni sezione ha almeno un paragrafo di testo (nessuna vuota)
- [ ] La revision history è aggiornata
- [ ] `1_RAD/IS3_CL_RAD.md` è compilato con risposte SI/NO/NA