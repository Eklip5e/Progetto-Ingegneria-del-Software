# Statement of Work (SoW) — Progetto `IS3`

> **Scheletro 0.1 — da compilare.** La struttura e i vincoli sono già corretti:
> sono quelli del template TirocinioSmart adattato dal docente per l'A.A. 2026/2027.
> Il tuo compito è riempirlo con **il progetto tuo**.
>
> ⚠️ Sostituisci ovunque `IS3` con la sigla del vostro progetto e `TBD` con il contenuto.
> ⚠️ Non copiare il testo del template TirocinioSmart: il *numero* dei vincoli è
> uguale, la *descrizione* del progetto deve essere la vostra.

| Statement of Work — Progetto `IS3` | |
|---|---|
| **Progetto** | `IS3` — _da definire_ |
| **Versione** | 0.1 |
| **Data** | _da compilare_ |
| **Autori** | _Cognome1 Nome1, Cognome2 Nome2, Cognome3 Nome3_ |
| **Stato** | bozza |
| **Doc collegati** | `1_RAD/IS3_RAD_ver.*`, `2_SDD/IS3_SDD_ver.*` |

---

## Revision History

| Data | Versione | Descrizione | Autori |
|---|---|---|---|
| _gg/mm/aaaa_ | 0.1 | Prima stesura | _tutti_ |
| | | | |
| | | | |

> **La revision history non è decorativa.** Il check-list verifica che il documento
> sia versionato. Ogni volta che integrate i commenti del docente dopo il 20 dicembre,
> aggiungete una riga.

---

## Team

| Ruolo | Nome | Responsabilità principali |
|---|---|---|
| _ruolo_ | _Cognome Nome_ | _use case n.1, sequence diagram, statechart, unit test 1_ |
| _ruolo_ | _Cognome Nome_ | _use case n.2, sequence diagram, unit test 2_ |
| _ruolo_ | _Cognome Nome_ | _use case n.3, statechart, unit test 3, pattern 1_ |

> I **3 use case** (1 per membro), i **2 sequence diagram** (1 ogni 2 membri), i
> **2 statechart** (1 ogni 2 membri) e i **3 unit test** (1 per membro) sono
> assegnati **per membro**: questo è ciò che rende la ripartizione verificabile dal
> docente. Decidetela ora e scrivetela qui.

---

## 1. Scopo del Sistema

<!-- 3-6 paragrafi. Chi vi chiede il sistema, il problema reale che risolve,
     perché non potete farne a meno, cosa deve supportare esplicitamente. -->

_Con testo: il Consiglio Didattico / l'ente / il reparto / il committente
desidera incrementare [X] evitando allo stesso tempo [problema tipico],
senza necessità di ulteriore personale. L'obiettivo è fornire [strumento/sistema]
assicurando che tutti gli stakeholder coinvolti possano interagire in modo agevole
ed efficiente. Deve supportare: [elenco delle 4-6 capacità principali]._

**Elenco delle capacità che il sistema deve supportare:**

1. _
2. _
3. _
4. _
5. _

> Le frasi soprra sono la **forma** del template, non il contenuto. Il docente
> valuta che lo scopo sia concreto e circoscritto, non la forma.

### 1.1 Cosa è fuori scope

<!-- NON obbligatorio ma fondamentale: previene il runaway di requisiti
     e dimostra maturità di progetto. -->

- _Non gestiamo…_
- _Non prevediamo…_
- _L'integrazione con X è out of scope e sarà valutata come evoluzione futura._

---

## 2. Data di Inizio e di Fine

| Milestone | Data | Note |
|---|---|---|
| Inizio progetto | ottobre 2026 | formazione gruppo, setup tool |
| **Consegna SoW** | **10 ottobre 2026** | questo documento — **obbligatoria** |
| **Consegna intermedia (opzionale)** | **20 dicembre 2026** | un solo file: RAD + SDD + testing funzionale |
| Fine progetto | **6 gennaio 2027** (consegna) / **7 gennaio 2027** (discussione) | pre-appello |

> Le date vengono dalla piattaforma Moodle. **Verifica con il docente** la data della
> discussione: la piattaforma mostra scadenza di consegna 6 gennaio 2027 ma il titolo
> dell'assignment dice "pre-appello 7 Gennaio" — consegna il 6, si discute il 7.

---

## 3. Deliverables

| # | Deliverable | Acronimo | Quando |
|---|---|---|---|
| 1 | Statement of Work | SOW | 10 ott 2026 |
| 2 | Requirements Analysis Document | RAD | 20 dic 2026 (intermedia) + 6 gen 2027 (finale) |
| 3 | System Design Document | SDD | 20 dic 2026 (intermedia) + 6 gen 2027 (finale) |
| 4 | Cenni su Object Design Document | ODD | 6 gen 2027 |
| 5 | Matrice di Tracciabilità | MTR | 6 gen 2027 |
| 6 | Test Plan | TP | 6 gen 2027 |
| 7 | Test Case Specification | TCS | 6 gen 2027 |
| 8 | Test Incident Report | TIR | 6 gen 2027 |
| 9 | Test Incident Report Tracker | TIRT | 6 gen 2027 |
| 10 | Test Summary Report | TSR | 6 gen 2027 |
| 11 | Codice sorgente | — | 6 gen 2027 |
| 12 | Documentazione | — | 6 gen 2027 |

> I deliverable 2-12 sono **un'unica consegna, un unico file**, con eventuali link a
> cartelle Drive e/o GitHub. Una sola consegna per team.
> Il RAD include RAD + SDD + cenni ODD + matrice di tracciabilità come *allegati*
> o come parti di un unico documento, a scelta vostra — ma deve essere **un file**.

---

## 4. Vincoli / Constraints

### 4.1 Vincoli collaborativi e comunicativi

1. **Rispetto delle scadenze** intermedie e finali definite in questo documento.
2. **Sistema di versioning — GitHub in particolare**, al quale **tutti i membri del
   team** contribuiscono. Nessun membro può essere spettatore: ognuno deve avere
   commit e pull request proprie.
3. **Tool per la suddivisione di task e attività** — Trello o similare.
4. **Tool di comunicazione tracciabile** — Slack.

> Questi quattro non sono suggerimenti: sono **criteri di accettazione**.
> Se non sono usati secondo le linee guida dei lab, **il progetto fallisce**.

### 4.2 Vincoli tecnici — Analisi e specifica dei requisiti

Per un team di **3 membri**:

- Specifica di **minimo 2 e massimo 4 requisiti funzionali** per ogni membro del
  team → **da 6 a 12 requisiti funzionali**.
- Specifica di **minimo 2 e massimo 4 requisiti non funzionali** per ogni membro
  → **da 6 a 12 requisiti non funzionali**.
- Specifica di **minimo 2 e massimo 4 scenari** per ogni membro del team
  → **da 6 a 12 scenari**.
- **Esattamente 1 use case per ogni membro del team** → **3 use case**.
  *I casi d'uso aggiuntivi non saranno valutati.*
- **Esattamente 1 sequence diagram ogni due membri del team** → **2 sequence diagram**.
  *I sequence diagram aggiuntivi non saranno valutati.*
- **Esattamente 1 statechart ogni due membri del team** → **2 statechart diagram**.
  *Ulteriori diagrammi non verranno valutati.*
- **Esattamente 1 activity diagram per team** → **1**.
  *Ulteriori diagrammi non verranno valutati.*
- **1 class diagram per team** → **1**.
  *Eventuali object diagram non verranno valutati.*
- Specifica degli oggetti **boundary, control, entity** per gli use case specificati.

### 4.3 Vincoli tecnici — System Design

- Specifica di **minimo 2 e massimo 4 design goal per ogni membro** del team
  → **da 6 a 12 design goal**.
- **Analisi dei trade-off** relativi ad **almeno due coppie di design goal**.
- Definizione di un **diagramma di decomposizione dei sottosistemi** per team,
  con annessa descrizione e **motivazione** all'uso.
- Definizione di un **deployment diagram** per team, con annessa descrizione e
  **motivazione** all'uso.
- Definizione di: architettura del sistema, gestione dei dati persistenti,
  flusso di controllo globale, politiche di controllo degli accessi —
  ciascuna con **rationale pro/contra**.

### 4.4 Vincoli tecnici — Object Design

- Uso di **due design pattern per team**, selezionati **tra quelli presentati a lezione**
  — **anche solo progettazione** (non è obbligatorio implementarli).

### 4.5 Vincoli tecnici — Notazione

- **Uso di UML** in tutti gli artefatti.

### 4.6 Vincoli tecnici — Testing

**Ogni studente** dovrà effettuare:

1. **testing di unità**, tramite **category partition**, di **esattamente un metodo**
   di **una classe sviluppata** → **3 unit test** (1 per membro).
2. **testing di sistema**, tramite **category partition**, di **esattamente una
   funzionalità** del sistema sviluppato → **3 system test** (1 per membro).

> ⚠️ **"Esattamente".** Non un metodo in più. Il docente conta.

### 4.7 Vincoli tecnologici

<!-- Da compilare: cosa vi limita tecnicamente? -->

- Linguaggio: **Java 17**
- Build: **Maven**
- Test: **JUnit 5** + Mockito
- Persistenza: _
- CI: **GitHub Actions**

---

## 5. Criteri di Accettazione / Acceptance Criteria

> **Criteri che, se non rispettati, portano al FALLIMENTO del progetto.**
> Non sono obiettivi, sono condizioni.

1. Utilizzo appropriato di **GitHub**, che preveda il rispetto delle linee guida
   definite nel contesto delle attività di laboratorio.
2. Adeguato utilizzo del **pull-based development**, che preveda il rispetto delle
   linee guida definite nel contesto delle attività di laboratorio.
3. Adeguato utilizzo di **Slack**, che preveda il rispetto delle linee guida
   definite nel contesto delle attività di laboratorio.
4. Adeguato utilizzo di **Trello**, che preveda il rispetto delle linee guida
   definite nel contesto delle attività di laboratorio.
5. **Documentazione adeguata.** Verranno usati **tool di plagiarism detection**
   per identificare casi in cui gli studenti hanno copiato da progetti di anni
   precedenti e/o da altre fonti.
6. Appropriato **test di unità** di un metodo sviluppato, che preveda il rispetto
   dei vincoli.
7. Appropriato **test di sistema** di una funzionalità del sistema sviluppato,
   che preveda il rispetto dei vincoli.

---

## 6. Criteri di premialità

Punti aggiuntivi, non obbligatori:

1. Uso adeguato di **sistemi di build**.
2. Uso adeguato di un processo di **continuous integration** tramite **Travis**
   o **GitHub Actions**.
3. Adozione di processi di **code review**.
4. Uso adeguato di **tool avanzati di testing** (es. Mockito, Cobertura, ecc.).

> Il CI e il code review sono le premialità **più facili** da ottenere e le uniche
> che non richiedono tempo di sviluppo: sono già configurati in `6_codice/`.

---

## 7. Rischi del progetto

<!-- Facoltativo ma molto apprezzato: dimostra maturità.
     Un rischio = probabilità (B/M/A) × impatto (B/M/A) × mitigazione. -->

| # | Rischio | Prob. | Impatto | Mitigazione |
|---|---|---|---|---|
| 1 | _es. scope creep sui requisiti_ | A | M | _SoW come perimetro; nuove feature → backlog Trello, non RAD_ |
| 2 | _es. integrazione con servizio esterno non disponibile_ | M | A | _mock/adapter in fase 2_ |
| 3 | _es. membro con poco tempo_ | M | A | _pair programming, commit giornalieri_ |

---

## 8. Glossario

| Termine | Definizione |
|---|---|
| _TBD_ | _da definire_ |

---

## 9. Riferimenti

| Documento | Versione | Data |
|---|---|---|
| Lezione 00 — Introduzione al corso (vincoli di progetto) | — | A.A. 2026/2027 |
| Template SoW TirocinioSmart (C. Gravino) | 0.8 | 23/09/2026 |
| `GUIDA_COMPLETA_ESAME_E_PROGETTO.md` | — | — |

> I riferimenti si citano per **versione e data**, non per nome generico.
> È così che il check-list verifica la coerenza fra deliverable.

---

## 10. Firme / Approvazione

| Ruolo | Nome | Data | Firma |
|---|---|---|---|
| Referente progetto | | | |
| Membro 2 | | | |
| Membro 3 | | | |
| Docente (ricevuta) | | | |