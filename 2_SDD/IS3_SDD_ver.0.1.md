# SDD — System Design Document — Progetto `IS3`

> **Scheletro 0.1 — da compilare.**
> La struttura segue il check-list del docente (51 voci in `IS3_CL_SDD.md`).
> Il concetto guida è **rationale**: per ogni decisione architetturale servono
> argomenti **a favore e contrari** e il legame con i design goal.
>
> Sostituisci `IS3` con la sigla del progetto, `TBD` con il contenuto.

| System Design Document | `IS3` | |
|---|---|---|
| **Versione** | 0.1 | |
| **Data** | _gg/mm/aaaa_ | |
| **Autori** | _Cognome1, Cognome2, Cognome3_ | |
| **Stato** | bozza | |
| **RAD di riferimento** | `IS3_RAD_ver._1.0` | data — **verificare la versione** |

> ⚠️ Il check-list verifica che il documento sia **consistente con gli altri
> deliverable** e che le versioni siano riportate in §1.5. Se il RAD è alla 2.0,
> qui deve esserci scritto 2.0.

---

## Revision History

| Data | Versione | Descrizione | Autori |
|---|---|---|---|
| _gg/mm/aaaa_ | 0.1 | Prima stesura | _tutti_ |

---

# 1. Introduzione

## 1.1 Scopo del sistema

_2 paragrafi. Cosa fa il sistema a livello architetturale, in una frase._ _TBD_

## 1.2 Obiettivi di Design (Design Goals)

> **VINCOLO: da 6 a 12 design goal** (2–4 per membro × 3).
>
> ⚠️ **Regola d'oro: ogni design goal discende da un requisito non funzionale.**
> Il check-list chiede la corrispondenza in **entrambe** le direzioni:
> - ogni design goal è ricondotto a un RNF o a un'esigenza di management;
> - ogni RNF è stato considerato ai fini dei design goal.
>
> Un design goal senza RNF che lo giustifichi è un design goal inventato.

**Vincoli sui design goal:** vanno **descritti**, **prioritizzati** e devono essere
**realistici**.

| ID | Design goal | Deriva da (RNF) | Priorità | Membro | Trade-off analizzato |
|---|---|---|---|---|---|
| DG-01 | _es. Massima indipendenza dei moduli di dominio_ | _RNF-01_ | Alta | _Cognome1_ | _con DG-03_ |
| DG-02 | _…_ | _RNF-02_ | Alta | _Cognome1_ | _—_ |
| DG-03 | _es. Semplificità del deploy in ambiente didattico_ | _RNF-05_ | Media | _Cognome2_ | _con DG-01_ |
| DG-04 | _…_ | _RNF-03_ | Media | _Cognome2_ | _—_ |
| DG-05 | _…_ | | Media | _Cognome3_ | _…_ |
| DG-06 | _…_ | | Bassa | _Cognome3_ | _…_ |

**Totale: _6-12_ (2-4 per membro).**

## 1.3 Analisi dei trade-off

> **VINCOLO: almeno 2 COPPIE di design goal** con analisi del trade-off.
> Una coppia = due design goal che sono in tensione reciproca: ottimizzare l'uno
> peggiora l'altro.

### Trade-off 1: _DG-01_ vs _DG-03_

| | |
|---|---|
| **Design goal in tensione** | _es. modularità massima_ ↔ _es. deployment semplice_ |
| **Perché sono in conflitto** | _es. più moduli = più configurazione_ |
| **Cosa si guadagna scegliendo il primo** | _es. testabilità, riuso_ |
| **Cosa si perde** | _es. setup complesso_ |
| **Cosa perde l'altro** | _es. accoppiamento ridotto_ |
| **Decisione presa** | _…_ |
| **Perché** | _la scelta è coerente con DG-01 prioritario_ |

### Trade-off 2: _DG-0?_ vs _DG-0?_

_(stessa struttura)_

---

## 1.4 Definizioni, acronimi e abbreviazioni

| Termine | Definizione |
|---|---|
| _es. Pattern Observer_ | _…_ |
| _es. Layer_ | _…_ |

## 1.5 Riferimenti

| Documento | Versione | Data |
|---|---|---|
| `IS3_RAD_ver._1.0` | _1.0_ | _gg/mm_ |
| `IS3_SOW_ver._1.0` | _1.0_ | _gg/mm_ |
| _Lezione 08 — System Design 1_ | — | A.A. 2026/2027 |

## 1.6 Organizzazione del documento

| Capitolo | Contenuto |
|---|---|
| 1 | Introduzione: scopo, design goal e trade-off |
| 2 | Architettura del sistema corrente |
| 3 | Architettura del sistema proposto |
| 4 | Servizi dei sottosistemi |
| 5 | Glossario |

---

# 2. Architettura del sistema corrente

<!-- Se il progetto è greenfield: "nessuna architettura, il processo è manuale".
     Non saltare il capitolo. -->

_TBD_ — come funziona oggi, senza software.

---

# 3. Architettura del sistema proposto

## 3.1 Panoramica della sezione

_4-8 righe: l'architettura in una frase e la sua motivazione in tre righe._ _TBD_

---

## 3.2 Decomposizione in sottosistemi

> **VINCOLO: 1 diagramma per team.** → `diagrammi/decomposizione_sottosistemi/`
>
> ⚠️ **"Sottosistema" ≠ "classe".** Un sottosistema è un insieme di classi con una
> **responsabilità autonoma** e un'interfaccia definita. Se lo chiami "sottosistema"
> ma è una classe, il concetto non è dimostrato.

| ID | Sottosistema | Responsabilità | Interfaccia offerta | Dipende da |
|---|---|---|---|---|
| SS-01 | _es. GestioneUtenti_ | _registrazione, autenticazione_ | _servizi REST_ | _SS-02_ |
| SS-02 | _es. GestioneCatalogo_ | _..._ | _..._ | _—_ |

**Rationale (OBBLIGATORIO — pro/contra + design goal):**

| | |
|---|---|
| **Decisione** | _es. suddivisione in 3 sottosistemi_ |
| **Argomenti a favore** | 1. _es. accoppiamento ridotto_ 2. _es. testabilità indipendente_ 3. _..._ |
| **Argomenti contrari** | 1. _es. costo di integrazione_ 2. _es. complessità del deploy_ 3. _..._ |
| **Design goal di riferimento** | _DG-01, DG-03_ |
| **Coerenza verificata** | la scelta ottiene DG-01 accettando di perdere qualcosa su DG-03 |

---

## 3.3 Mapping hardware / software

> Il check-list chiede rationale anche per questa scelta.

| Componente | HW | SW | Note |
|---|---|---|---|
| _Client_ | _portatile_ | _browser_ | _..._ |
| _Server_ | _macchina virtuale_ | _JVM 17_ | _..._ |
| _Persistenza_ | _disco locale_ | _DB relazionale_ | _..._ |

**Rationale (pro/contra + design goal):** _TBD_

---

## 3.4 Gestione dei dati persistenti

<!-- Obbligatorio: TUTTO il modello dati sta qui. Quale storage, come si mappa
     sul modello oggetti, come si garantisce consistenza, concorrenza, backup. -->

**Storage scelto:** _es. database relazionale SQLite / PostgreSQL / file JSON_ _TBD_

| Entità (dal class diagram) | Tabella / struttura | Chiave primaria | Relazioni |
|---|---|---|---|
| _CL-01_ | _..._ | _id_ | _..._ |

**Persistenza:** _ORM usato / JDBC / file_ _TBD_

**Consistenza e concorrenza:** _come si gestiscono le transazioni, le race condition_ _TBD_

**Rationale (pro/contra + design goal):** _TBD_

---

## 3.5 Controllo degli accessi e sicurezza

<!-- Obbligatorio. Ruoli, permessi, autenticazione, autorizzazione. -->

| Ruolo | Permessi | Ruoli ammessi |
|---|---|---|
| _es. Amministratore_ | _pieno_ | _tutti_ |
| _es. Utente_ | _lettura + propri dati_ | _..._ |

**Meccanismo di autenticazione:** _es. sessione con cookie HttpOnly + password hash (BCrypt)_ _TBD_

**Meccanismo di autorizzazione:** _es. controllo a ogni endpoint_ _TBD_

**Rationale (pro/contra + design goal):** _TBD_

---

## 3.6 Controllo globale del software

<!-- Obbligatorio: come il sistema "sta insieme". Pattern architetturali,
     ciclo di richiesta, propagazione errori, logging, configurazione. -->

**Stile architetturale:** _es. Three-tier / MVC / Clean Architecture_ _TBD_

**Ciclo di una richiesta:**

```
Client → [Boundary] → [Control] → [Entity] → [Persistenza]
                  ↑                                    ↓
                  └──────────── risposta ─────────────┘
```

**Gestione errori:** _es. eccezioni tipizzate, mapping a codici HTTP_ _TBD_
**Logging:** _es. SLF4J + Logback, livelli per ambiente_ _TBD_
**Configurazione:** _es. file properties esterno, variabili d'ambiente_ _TBD_

**Rationale (pro/contra + design goal):** _TBD_

---

## 3.7 Condizioni limite

<!-- Obbligatorio. Cosa succede ai bordi del sistema: cosa fa quando
     NON funziona. È quello che i docenti valutano di più in assoluto. -->

| # | Condizione limite | Comportamento atteso | Dove gestita |
|---|---|---|---|
| 1 | _es. database non raggiungibile_ | _il sistema non crasha, mostra errore recuperabile_ | _handler_ |
| 2 | _es. input troppo grande / malformato_ | _validazione con messaggio utile_ | _boundary_ |
| 3 | _es. due utenti registrano lo stesso email_ | _vincolo di unicità, errore 409_ | _entity_ |
| 4 | _es. sessione scaduta_ | _redirect a login con messaggio_ | _filtro_ |
| 5 | _es. rete assente_ | _..._ | |
| 6 | _es. spazio disco esaurito_ | _..._ | |

---

# 4. Servizi dei sottosistemi

<!-- Se i sottosistemi sono servizi: metodo, firma, input, output, errori.
     È la "lettera d'intenti" che il client userà davvero. -->

| Sottosistema | Servizio | Firma | Errori possibili |
|---|---|---|---|
| _SS-01_ | _registraUtente_ | `_registra(email, password, nome): Result<Utente, Errore>` | _emailDuplicato, datiNonValidi_ |
| _SS-02_ | _..._ | | |

---

# 5. Glossario

| Termine | Definizione |
|---|---|
| _TBD_ | _..._ |

---

# Appendice A — Object Design (cenni)

> Il SOW richiede i **cenni su ODD** come deliverable separato. In pratica:
> in questa sezione dell'SDD si fa il **riferimento** al documento
> `3_ODD/IS3_ODD_ver._1.0`, che contiene i **2 design pattern** del team.
>
> In alternativa, se preferisci un documento unico per la consegna, sposta
> l'intero contenuto dell'ODD qui e aggiungi la sottosezione corrispondente.
> **Decidi ora** e mantieni la decisione coerente in tutti i documenti.

---

# Appendice B — Check-list di conformità (autocontrollo)

- [ ] 6-12 design goal, 2-4 per membro
- [ ] Ogni design goal è collegato a un RNF del RAD
- [ ] Ogni RNF del RAD è considerato nei design goal
- [ ] Almeno **2 coppie** di trade-off analizzate (pro e contro espliciti)
- [ ] Diagram: **1** decomposizione sottosistemi
- [ ] Diagram: **1** deployment
- [ ] Rationale con pro/contra per: architettura, mapping HW/SW, persistenza, accessi, flusso di controllo (5 punti)
- [ ] §3.7 Condizioni limite: almeno 4-6 casi concreti
- [ ] Nessun termine usato senza definizione nel glossario
- [ ] Coerente con il RAD e con la versione dichiarata in §1.5
- [ ] `2_SDD/IS3_CL_SDD.md` compilato con risposte SI/NO/NA