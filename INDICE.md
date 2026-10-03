# INDICE — Tasca (progetto Ingegneria del Software)

> **Questa cartella è la fonte di verità del progetto.**
> Tutto ciò che produrrai per il corso va qui dentro. Nulla va scritto altrove.
>
> **Cartella genitore:** `D:\University\3 Anno 1 Semestre\Ingegneria del Software\`
> — lì ci sono i materiali del corso (lezioni, BiblioNet d'esempio, guide).
> **Non spostare e non copiare i materiali del corso dentro `Tasca/`**: il progetto
> deve restare tuo, e il controllo anti-plagio è esplicito nei criteri di accettazione.

---

## 0. Regole d'oro prima di iniziare

1. **Non copiare.** Il progetto `BiblioNet` presente nella cartella madre è un
   *riferimento di struttura*, non un template. Il docente lo ha scritto esplicitamente:
   *"Copiare significa sbagliare nel 99.9% dei casi."* Puoi **imitare l'organizzazione**,
   mai il testo, i nomi dei casi d'uso, i diagrammi o le frasi.
2. **Tutto in GitHub.** Il repository parte ora, non alla fine. I criteri di accettazione
   richiedono esplicitamente GitHub + pull-based development + code review.
3. **Il codice non è il deliverable principale.** Il deliverable è la **documentazione**.
   Il codice serve a dimostrare che la documentazione è vera.
4. **I numeri sono vincolanti.** I vincoli quantitativi del SOW sono controllati
  (check-list). Sforarli = progetto non conforme.

---

## 1. Le due sigle da cambiare subito

Tutti i file seguono la convenzione di rinomina imposta dal docente:

```
<SiglaProgetto>_<AcronimoDocumento>_ver.<Versione>.<estensione>
   es.        IS3_RAD_ver.1.0.docx
```

| Segnaposto | Valore attuale | Cosa scriverci |
|---|---|---|
| `IS3` | sigla provvisoria | la **sigla del vostro progetto** (max 3-4 caratteri) |
| `ver.0.1` | bozza | la versione vera (`0.1` bozza, `1.0` prima consegna, `2.0` dopo i commenti) |

> BiblioNet usava `C07`. La sigla `C` + numero di gruppo è una convenzione del corso:
> se il tuo gruppo ha un numero assegnato dal docente, usa quello.

---

## 2. Vista d'insieme

```
Tasca/
├── INDICE.md                     ← SEI QUI. Leggi questo file per primo.
├── PROPOSTE_PROGETTO.md         ← 4 idee from-scratch + come adattare il tuo progetto
├── PIANO_LAVORO.md              ← milestone, ripartizione dei 3 membri, setup tool
│
├── 0_amministrazione/           ← Prove che avete lavorato "come un team"
│   ├── SoW/                     ← lo Statement of Work (PRIMA scadenza: 10 ott 2026)
│   ├── Riunioni/                ← verbali delle riunioni
│   ├── Gestione_task/           ← export di Trello
│   └── Comunicazioni/           ← export Slack (la tracciabilità dev'essere dimostrabile)
│
├── 1_RAD/                       ← Requirements Analysis Document
│   ├── IS3_RAD_ver.0.1.md       ← scheletro PRONTO, seguilo all'ordine
│   ├── IS3_CL_RAD.md            ← check-list di autocontrollo (42 voci)
│   └── diagrammi/
│       ├── use_case/            ← 3 file (1 per membro)
│       ├── sequence/            ← 2 file (1 ogni 2 membri)
│       ├── activity/            ← 1 file  (1 per team)
│       ├── statechart/          ← 2 file (1 ogni 2 membri)
│       ├── class/               ← 1 file  (1 per team)
│       ├── boundary_control_entity/  ← specifica oggetti B/C/E per i 3 use case
│       └── ui_mockup/           ← mock-up interfaccia + percorsi di navigazione
│
├── 2_SDD/                       ← System Design Document
│   ├── IS3_SDD_ver.0.1.md       ← scheletro PRONTO
│   ├── IS3_CL_SDD.md            ← check-list di autocontrollo (51 voci)
│   └── diagrammi/
│       ├── decomposizione_sottosistemi/  ← 1 diagramma per team
│       └── deployment/                   ← 1 diagramma per team
│
├── 3_ODD/                       ← Object Design Document (i "cenni su ODD")
│   ├── IS3_ODD_ver.0.1.md       ← scheletro PRONTO
│   └── design_pattern/          ← i 2 pattern del team: obiettivo + come implementarli
│
├── 4_Matrice_Tracciabilita/
│   └── IS3_MTR_ver.0.1.md       ← NON è un extra: collega requisiti↔design↔test
│
├── 5_testing/
│   ├── pianificazione/
│   │   ├── IS3_TP_ver.0.1.md    ← Test Plan
│   │   ├── IS3_TCS_ver.0.1.md   ← Test Case Specification
│   │   └── category_partition/  ← 6 file: 3 unit test (1 per membro) + 3 system test
│   └── reports/
│       ├── IS3_TIR_ver.0.1.md   ← Test Incident Report
│       ├── IS3_TIRT_ver.0.1.md  ← Test Incident Report Tracker (registro)
│       └── IS3_TSR_ver.0.1.md   ← Test Summary Report
│
├── 6_codice/                    ← il repository Git che pushate su GitHub
│   ├── pom.xml                  ← già pronto: Java 17 + JUnit 5 + Mockito + JaCoCo
│   ├── .gitignore               ← già pronto
│   ├── src/main/java/it/unisa/is3/
│   ├── src/main/resources/
│   └── src/test/java/it/unisa/is3/
│
└── .github/workflows/
    └── maven.yml                ← CI: build + test automatici a ogni push (premialità)
```

---

## 3. I numeri che devi rispettare (team = 3)

Questi derivano dal SOW TirocinioSmart, che è la versione adattata dal docente
per l'A.A. 2026/2027. Il SOW che scriverai tu **deve riportarli**: sono il contratto
con cui ti valutano.

| Artefatto | Vincolo | **Il tuo numero** | Dove |
|---|---|---|---|
| Requisiti funzionali e non funzionali | 2–4 **per membro** | **6–12** | RAD §3.2, §3.3 |
| Scenari (use case scenario) | 2–4 **per membro** | **6–12** | RAD §3.4.1 |
| Diagramma dei casi d'uso | **esattamente 1 per membro** | **3** | `1_RAD/diagrammi/use_case/` |
| Sequence diagram | **esattamente 1 ogni 2 membri** | **2** | `1_RAD/diagrammi/sequence/` |
| Statechart diagram | **esattamente 1 ogni 2 membri** | **2** | `1_RAD/diagrammi/statechart/` |
| Activity diagram | **esattamente 1 per team** | **1** | `1_RAD/diagrammi/activity/` |
| Class diagram | **1 per team** | **1** | `1_RAD/diagrammi/class/` |
| Deployment diagram | **1 per team** | **1** | `2_SDD/diagrammi/deployment/` |
| Diagramma decomposizione sottosistemi | **1 per team** | **1** | `2_SDD/diagrammi/decomposizione_sottosistemi/` |
| Design goal | 2–4 **per membro** | **6–12** | SDD §2 |
| Analisi trade-off | **almeno 2 coppie** di design goal | **2+** | SDD §2 |
| Design pattern | **2 per team** | **2** | `3_ODD/design_pattern/` |
| Unit test con category partition | **1 metodo per studente** | **3** | `5_testing/pianificazione/category_partition/` |
| System test con category partition | **1 funzionalità per studente** | **3** | `5_testing/pianificazione/category_partition/` |

> ⚠️ **Attenzione alla formulazione negativa.** Il SOW dice che *i diagrammi in eccesso
> "non saranno valutati"* e che *gli object diagram "non verranno valutati"*.
> Tradotto: **fare più di quanto chiesto è lavoro buttato**. Non fare un quarto
> sequence diagram. Non fare object diagram. Il punto è la **precisione**, non la quantità.
>
> ⚠️ C'è una variante più permissiva nella lezione 00 (sequence/statechart "almeno 1
> ogni due", activity "almeno 1"). Se il vostro SOW riporta la variante del template
> TirocinioSmart (la più restrittiva), quella vale. **Se non siete sicuri, chiedete al
> docente.** Il numero scritto nel vostro SOW è quello che conta.

---

## 4. Cosa va in ogni cartella

### `0_amministrazione/`

Il progetto **fallisce** se non si dimostra che avete lavorato in team. Questa cartella
è la prova.

| Cartella | Cosa metterci |
|---|---|
| `SoW/` | `IS3_SOW_ver.0.1.md`. È la **prima scadenza** (10 ott 2026) e l'unico documento che definisce il perimetro del progetto. Scheletro già pronto. |
| `Riunioni/` | Un verbale breve per riunione: data, presenti, decisioni, task assegnati, link al branch. 8-12 riunioni da ottobre a gennaio. |
| `Gestione_task/` | Export del board Trello alla fine di ogni sprint (JSON). Dimostra che i task sono passati da "da fare" a "fatto". |
| `Comunicazioni/` | Export dei canali Slack relevanti + screenshot delle discussioni di decisione. Il docente chiede "tool di comunicazione tracciabile": deve essere **ispezionabile**. |

> I criteri di accettazione dicono: *"Adeguato utilizzo di GitHub / pull-based
> development / Slack / Trello"*. Se non c'è una traccia esportabile, il requisito
> è considerato non soddisfatto.

### `1_RAD/` — Requirements Analysis Document

Il RAD ha una **struttura imposed dal check-list del docente**, non libera.
Lo scheletro `IS3_RAD_ver.0.1.md` la segue già:

```
1. Introduzione
   1.1 Obiettivo del Sistema
   1.2 Ambito del Sistema
   1.3 Obiettivi e Criteri di Successo
   1.4 Definizioni, Acronimi e Abbreviazioni
   1.5 Riferimenti
   1.6 Organizzazione del Documento
2. Sistema attuale
3. Sistema proposto
   3.1 Sintesi della sezione
   3.2 Requisiti Funzionali
   3.3 Requisiti Non Funzionali
       3.3.1 Usabilità        3.3.5 Implementazione
       3.3.2 Affidabilità     3.3.6 Interfacce
       3.3.3 Prestazioni      3.3.7 Operation
       3.3.4 Supportability   3.3.8 Packaging
                              3.3.9 Legali
   3.4 Modello del Sistema
       3.4.1 Scenari
       3.4.2 Modello dei Casi d'Uso
       3.4.3 Modello ad Oggetti
       3.4.4 Modello Dinamico  (activity / sequence / statechart)
       3.4.5 Interfaccia Utente — Percorsi di Navigazione e Mock-up
4. Glossario
```

> ⚠️ **Le 9 sottosezioni dei requisiti non funzionali sono obbligatorie.**
> Anche "Prestazioni" e "Legali" devono avere contenuto: anche solo 3 righe
> ("non applicabile, sistema didattico, nessun dato personale oltre la email")
> ma **non possono mancare**. Una sezione vuota = check-list non soddisfatta.

I diagrammi si producono **con un editor UML e si esportano in `.drawio` + `.png`**,
così sono ispezionabili e modificabili. I `.png` da soli non sono più modificabili:
trovate il tool che preferite (draw.io, Visual Paradigm, Enterprise Architect,
PlantUML) ma **tenete il sorgente**.

`IS3_CL_RAD.md` è la check-list del docente (42 voci). **Usatela come lista di
controllo finale**: rispondete SI / NO / NA a ogni voce e annotate le note. È anche
il metodo migliore per capire cosa vi manca prima della consegna.

### `2_SDD/` — System Design Document

Struttura anch'essa imposed dal check-list (51 voci):

```
1. Introduzione (scopo, design goal, definizioni, riferimenti, organizzazione)
2. Architettura del sistema corrente
3. Architettura del sistema proposto
   3.1 Panoramica della sezione
   3.2 Decomposizione in sottosistemi        + rationale (pro/contra)
   3.3 Mapping hardware/software           + rationale
   3.4 Gestione dei dati persistenti        + rationale
   3.5 Controllo degli accessi e sicurezza  + rationale
   3.6 Controllo globale del software       + rationale
   3.7 Condizioni limite
4. Servizi dei sottosistemi
5. Glossario
```

> **Il punto che il docente pesa di più nell'SDD è il *rationale*.**
> Per ognuna delle 5 scelte architetturali (architettura, mapping HW/SW, persistenza,
> accessi, flusso di controllo) il check-list chiede esplicitamente:
> *"Il rationale per la scelta è fornito? Sono stati indicati gli **argomenti a favore
> e contrari**? La scelta fatza è **consistente con i design goal**?"*
>
> Non scrivete "abbiamo scelto il 3-tier perché è meglio". Scrivete tre pro, tre
> contro, e il legame con i design goal. È il passaggio che distingue una risposta
> da 24 da una da 30.

I **design goal** (§1) devono essere **derivati dai requisiti non funzionali**: ogni
design goal risponde a un requisito non funzionale del RAD. Il check-list verifica
esattamente questa corrispondenza in entrambe le direzioni.

### `3_ODD/` — Object Design Document

I "cenni su ODD" del deliverable. Il SIZZATIVO:

- **2 design pattern per team**, scelti **tra quelli presentati a lezione**.
- È ammesso **solo progettazione**: non dovete per forza implementarli.
- Per ciascuno: **obiettivo** (cosa risolve) e **come sarebbe implementato**
  (classi, interfacce, ruolo nel diagramma).

> Verifica il syllabus M4 nella cartella madre per la **lista esatta** dei pattern
> visti a lezione: usare un pattern mai trattato è un rischio.
> I pattern "facili da piazzare bene" e largamente presentati sono in genere
> Strategy, Observer, Factory Method / Abstract Factory, Singleton (con cautela),
> Decorator, Adapter, Facade.

### `4_Matrice_Tracciabilita/` — Matrice di Tracciabilità

Non è un documento da scrivere "per completezza": è la prova che il progetto è
coerente. Una tabella che mappa:

```
ID Requisito funzionale  →  ID Caso d'uso  →  ID Design goal  →  ID Test  →  esito
```

Se un requisito non ha un test, o un test non copre un requisito, la matrice
fallisce. È anche il modo più rapido per capire cosa manca.

### `5_testing/`

| Documento | Cos'è | Note |
|---|---|---|
| **TP** (Test Plan) | strategia di test: ambiente, tecniche, criteri di entry/exit | include il **piano delle prove di convergenza** e i criteri di accettazione |
| **TCS** (Test Case Specification) | i casi di test con expected results | il cuore del deliverable di testing |
| **category_partition/** | le tabelle di **category partition** | **6 file**: 1 metodo di una classe + 1 funzionalità, per ciascuno dei 3 membri |
| **TIR** (Test Incident Report) | il report degli incidenti (bug trovati) | 1 documento per sessione di test |
| **TIRT** (Test Incident Report Tracker) | il **registro cumulativo** degli incidenti, in tabella | tiene traccia di ogni TIR |
| **TSR** (Test Summary Report) | il report di **sintesi finale**: quanti test, quanti passati, copertura, incidenti rimasti | si scrive **ultimo** |

> La **category partition** è l'unico tipo di test richiesto esplicitamente.
> Ogni studente deve fare: **un metodo di una classe sviluppata** (unit test) e
> **una funzionalità del sistema** (system test), entrambi con le tabelle di
> category partition. Le tabelle hanno righe di categoria per ogni **parametro**
> (es. per un metodo `registraUtente(nome, email, password)` le categorie sono
> `nome`, `email`, `password`).

### `6_codice/` + `.github/`

- **Un solo repository Git** per tutto il progetto. Le cartelle `1_RAD/`…`5_testing/`
  ci finiscono dentro (o in un repo `docs` se preferite tenere il codice separato).
- `pom.xml` è già configurato: Java 17, JUnit 5, Mockito, JaCoCo.
- `.github/workflows/maven.yml` esegue build + test a ogni push. Questo è un
  **criterio di premialità** ("processo di continuous integration").
- **Maven, non Gradle**: i lab del corso usano Maven e il docente lo verifica.
- `.gitignore` già configurato per non versionare `target/` e i `.docx` temporanei.

> ⚠️ **La CI non può fallire.** Se GitHub Actions segnala rosso, la commit è rotta.
> Commit solo con codice che compila e test verdi.

### `6_codice/src/main/java/it/unisa/is3/`

Package radice `it.unisa.is3`. **Rinominalo** in base alla sigla del progetto
(es. `it.unisa.biblionet` → `it.unisa.<sigla>`) prima di scrivere la prima classe,
e allinea `pom.xml` di conseguenza. Non lasciare package placeholder in un repo pubblico.

---

## 5. Ordine di lavorazione

Non è "tutto insieme". L'ordine è quello del ciclo di vita, e ogni deliverable
ha una data:

| Quando | Cosa | Deliverable | Cartella |
|---|---|---|---|
| **~10 ott 2026** | SoW | `IS3_SOW_ver.1.0` | `0_amministrazione/SoW/` |
| ott–dic 2026 | analisi e specifica | `IS3_RAD_ver.1.0` | `1_RAD/` |
| **~20 dic 2026** *(opzionale ma fondamentale)* | RAD + SDD + testing funzionale, **in un solo file** | `IS3_RAD_ver.2.0` | `1_RAD/`, `2_SDD/` |
| dic 2026 – gen 2027 | design + ODD | `IS3_SDD_ver.1.0`, `IS3_ODD_ver.1.0` | `2_SDD/`, `3_ODD/` |
| gen 2027 | testing completo | `IS3_TCS`, `IS3_TP`, `IS3_TIR/TIRT/TSR` | `5_testing/` |
| **6 gen 2027, 23:59** | **consegna finale** (un solo file) | tutti | tutte |
| **7 gen 2027** | discussione | — | — |

> **La consegna intermedia del 20 dicembre è opzionale ma va fatta.**
> Chi consegna in tempo riceve i commenti del docente e può migliorare la
> documentazione per la finale. È l'unico momento in cui hai un riscontro
> strutturato prima della valutazione: è una cortesia che ti costa poco e vale tantissimo.

---

## 6. Le 6 cose che fanno fallire il progetto

Dai criteri di accettazione, verbatim:

1. Uso inappropriato di **GitHub**
2. Uso inappropriato del **pull-based development**
3. Uso inappropriato di uno **strumento di comunicazione**
4. Uso inappropriato di uno **strumento di gestione task**
5. **Documentazione inadeguata** — con controllo anti-plagio attivo
6. **Test non adeguati** sui casi d'uso

Non sono "requisiti di progetto", sono condizioni di esistenza del progetto.

---

## 7. File di questo scaffolding

Tutti i `.md` con `ver.0.1` sono **scheletri**: hanno la struttura corretta e i
promemoria, ma i contenuti sono da scrivere. Nessuno contiene testo copiato
da BiblioNet o dal materiale del corso.

| File | Cos'è |
|---|---|
| `INDICE.md` | questo file |
| `PROPOSTE_PROGETTO.md` | idee di progetto + percorso per adattare il tuo progetto esistente |
| `PIANO_LAVORO.md` | milestone, ripartizione dei 3 membri, setup GitHub/Trello/Slack/CI |
| `README.md` | readme del repository GitHub (va anche in `6_codice/`) |
| `0_amministrazione/SoW/IS3_SOW_ver.0.1.md` | scheletro Statement of Work, con i vincoli già scritti |
| `1_RAD/IS3_RAD_ver.0.1.md` | scheletro RAD, struttura imposta dal check-list |
| `1_RAD/IS3_CL_RAD.md` | check-list RAD del docente, come lista di lavoro |
| `2_SDD/IS3_SDD_ver.0.1.md` | scheletro SDD, con i 5 punti di rationale obbligatori |
| `2_SDD/IS3_CL_SDD.md` | check-list SDD del docente |
| `3_ODD/IS3_ODD_ver.0.1.md` | scheletro ODD + slot per i 2 pattern |
| `4_Matrice_Tracciabilita/IS3_MTR_ver.0.1.md` | scheletro matrice di tracciabilità |
| `5_testing/pianificazione/IS3_TP_ver.0.1.md` | scheletro Test Plan |
| `5_testing/pianificazione/IS3_TCS_ver.0.1.md` | scheletro Test Case Specification |
| `5_testing/reports/IS3_TIR_ver.0.1.md` | scheletro Test Incident Report |
| `5_testing/reports/IS3_TIRT_ver.0.1.md` | scheletro tracker incidenti |
| `5_testing/reports/IS3_TSR_ver.0.1.md` | scheletro Test Summary Report |
| `6_codice/pom.xml` | progetto Maven pronto (Java 17, JUnit 5, Mockito, JaCoCo) |
| `6_codice/.gitignore` | esclusioni Git per progetto Java/Maven |
| `.github/workflows/maven.yml` | pipeline CI (build + test) |

---

## 8. Da dove viene l'informazione

| Cosa | Dove (cartella madre) |
|---|---|
| Regole d'esame e di progetto | `GUIDA_COMPLETA_ESAME_E_PROGETTO.md` |
| Struttura RAD e SDD, check-list | `04_MD_progetto_BiblioNet/1. RAD -- C07_CL_RAD.md`, `2. SDD -- C07_CL_SDD.md` |
| Struttura del SOW | `01_MD_dalle_lezioni/09.01-Esempio di statement of work….md` |
| Vincoli di progetto (slide) | `01_MD_dalle_lezioni/01.01-Introduzione al corso….md` |
| Esempio completo di progetto | `03_Progetto_BiblioNet/` *(riferimento di struttura, non da copiare)* |
| Diagrammi di esempio | `04_MD_progetto_BiblioNet/*.drawio` |
| Lab: Git, IntelliJ, Maven, CI, ChatGPT | `01_MD_dalle_lezioni/10.0*` |
| Teoria per l'esame (M1–M5) | `GUIDA_COMPLETA_ESAME_E_PROGETTO.md` §4 |