# Proposte di progetto — cosa costruire

> Documento di lavoro. **Nessuna di queste proposte è scritta in questa cartella come
> progetto**: sono opzioni da valutare. La decisione finale si prende prima di
> scrivere il SoW (scadenza **10 ottobre 2026**).

---

## Parte 1 — Come scegliere il progetto

I vincoli del corso sono **quantitativi e rigidi**. Questo significa che la scelta
del progetto non è una scelta di gusto, ma una scelta di **compatibilità**. Un
progetto "bello" ma che non ci sta dentro i vincoli è un progetto che non si può
consegnare.

### I 6 filtri da applicare a ogni idea

| # | Filtro | Perché | Come verificarlo |
|---|---|---|---|
| 1 | **Esattamente 3 use case** | Il SOW dice che gli use case aggiuntivi **non saranno valutati** | Riesci a scegliere 3 casi d'uso e a **scartare il resto**? |
| 2 | **Parametri divisibili in classi di equivalenza** | Il testing è **solo** category partition | Ogni metodo del percorso principale ha input con domini separabili? |
| 3 | **2 design pattern motivati, di famiglie diverse** | Servono 2 pattern, non di più, tra quelli di lezione | I pattern sono **naturali** o stanno forzati? |
| 4 | **Un processo attuale da descrivere** | Il RAD ha il capitolo "Sistema attuale" | Esiste un modomanuale/storico di fare la stessa cosa? |
| 5 | **Nessuna dipendenza esterna fragile** | Senza internet o senza chiavi API la build si rompe | Si può fare tutto in locale? |
| 6 | **Finitura in ~10 settimane, 3 persone** | Il tempo è quello che è | Il perimetro è riducibile senza mentire? |

### I 4 errori che fanno perdere il progetto

1. **Scegliere un progetto troppo grande.** Il vincolo "esattamente 3 use case" non
   è un limite da raggiungere: è un **tetto**. Un progetto con 15 funzionalità ti
   costringe a **nasconderne 12**, e il docente vede che il codice contiene cose
   non documentate. È incoerenza, non ricchezza.
2. **Scegliere un dominio "troppo facile".** Una to-do list non ha: gestione degli
   accessi, condizioni limite, architettura, dati persistenti, ruoli. Tutto il SDD
   diventa una formalità. Il dominio deve avere **regole** (che generano difetti,
   che generano test, che generano condizioni limite).
3. **Scegliere un dominio irrealistico.** "Una piattaforma di e-commerce completa"
   in 10 settimane non esiste. Esiste solo la versione tagliata, e a quel punto ne
   hai scelto un'altra.
4. **Scegliere un dominio identico a BiblioNet.** Il docente ha visto quel progetto
   ogni anno. Un clone del gestore di prestiti è il modo più rapido per essere
   confrontati con l'originale — e il confronto non vi favorisce.

---

## Parte 2 — Quattro proposte

Tutte quarte rispettano i 6 filtri. Differiscono per tipo di ragione e per
pattern. Scegline una e **leggila tutta** prima di decidere.

---

## Proposta A — **HelpDesk** · gestione delle richieste di assistenza

### Il dominio

Un reparto IT di un'azienda o di un ateneo riceve richieste di assistenza da
utenti non tecnici (problema con la casella email, account bloccato, software che
non parte). Oggi le richieste finiscono in una casella email condivisa: nessuno
sa a chi è affidata una richiesta, nessuno tiene traccia delle richieste chiuse,
nessuno può dire "quante richieste di tipo X gestiamo al mese".

Il sistema introduce un **ticket** con stato, priorità, assegnatario e storico.

### I 3 use case (uno per membro)

| ID | Use case | Attore | Scenari (≥2) | Parametri partizionabili |
|---|---|---|---|---|
| **UC-01** | Apertura ticket da richiesta dell'utente | Utente | 1. urgenza bloccante, 2. dubbio informativo, 3. categoria inesistente | **categoria** (enum: 6 valori + "non valida"), **urgenza** (bassa/media/alta/critica), **descrizione** (vuota/corta/valida/oltre 500 char) |
| **UC-02** | Assegnazione e gestione del ciclo di vita del ticket | Operatore | 1. assegnazione a operatore libero, 2. riassegnazione, 3. ticket già chiuso | **nuovo assegnatario** (esiste/non esiste/già assegnato), **nuova priorità** (regola di promozione automatica) |
| **UC-03** | Monitoraggio e reportistica del servizio | Responsabile | 1. report mensile per categoria, 2. ticket scaduti, 3. filtro per intervallo date | **intervallo date** (valido/invertito/futuro), **categoria** (tutte/una), **formato** |

### I 2 design pattern

| Pattern | Famiglia | Perché è naturale qui | Dove |
|---|---|---|---|
| **Strategy** | comportamentale | La **priorità** non dipende da una sola regola: dipende da categoria + urgenza + cliente. Regole diverse, sostituibili a runtime, senza `switch` che cresce | `CalcolatorePriorita` + 3 strategie concrete |
| **State** | comportamentale | ⚠️ Due pattern della stessa famiglia: **preferiscilo ad altri** se vuoi varietà | Il ciclo di vita del ticket è il cuore del dominio: `Aperto → InCorso → InAttesa → Risolto → Chiusato`, con transizioni e guard |

**Alternativa consigliata al posto di State:** **Observer** (chiudi un ticket →
notifica via email all'utente e aggiorna il pannello dell'operatore). Così hai
comportamentale + comportamentale comunque, ma almeno uno dei due è *push*.
Se vuoi varietà di famiglia: **Factory Method** per creare ticket da fonti diverse
(web, email, form) con campi diversi.

> **Nota:** il pattern State è **eccellente** per il vostro 2° statechart diagram.
> Se lo scegliete come pattern, il statechart lo avrete gratis. Ma attenzione a non
> avere 2 statechart che descrivono lo stesso oggetto: uno per il pattern, uno per
> UC-02.

### Architettura proposta (con i 5 rationale da scrivere)

- **3-tier**: presentation (controller REST o CLI) / business (servizi + entità) / persistence (repository).
- **Persistenza**: database relazionale. Rationale facile da scrivere: *pro* integrità referenziale e query; *contro* setup e mapping. Con SQLite in-memory nei test la CI resta verde senza servizi esterni.
- **Accessi**: 3 ruoli (Utente, Operatore, Responsabile). Rationale ricco: autorizzazione per ruolo vs per proprietà della risorsa (un operatore vede solo i propri ticket? il responsabile vede tutti?).
- **Flusso di controllo**: MVC, propagazione errori con eccezioni tipizzate.
- **Condizioni limite** (facili da scrivere bene): ticket assegnato a un operatore
  eliminato · categoria rimossa dopo che esistono ticket · utente disattivato con
  ticket aperti · ticket chiuso che riceve un commento · due operatori che
  assegnano lo stesso ticket simultaneamente.

### Data model (sintesi)

```
Utente(id, nome, email, ruolo, attivo)
Ticket(id, codice, categoria, urgenza, stato, utente_id, assegnatario_id, 
       descrizione, created_at, closed_at)
Commento(id, ticket_id, autore_id, testo, created_at)
TransizioneStato(id, ticket_id, da, a, chi, quando)   ← storico, ottimo per lo statechart
```

### Pro e contro

| ✅ Pro | ❌ Contro |
|---|---|
| Domino ricco di regole (priorità, transizioni) | Le regole di priorità vanno definite bene, altrimenti il RAD diventa vago |
| Category partition molto naturale su categorie/urgenze | Richiede attenzione alle transizioni di stato (facile sbagliare) |
| Ottimo per 2 statechart (ticket, utente) | Rischio di documentare troppe entità |
| Non somiglia a nulla del materiale del docente | — |

---

## Proposta B — **MensaCampus** · gestione pasti, prenotazioni e allergie

### Il dominio

La mensa universitaria serve 2000 pasti al giorno. Oggi: un banchetto fisico
all'ingresso, e gli studenti con allergie o intolleranze non possono sapere cosa
possono mangiare senza chiedere. Il sistema gestisce **menù settimanali**,
**prenotazione del pasto**, e soprattutto il **calcolo degli allergeni** di ogni
piatto con le regole di contaminazione crociata.

Questa è la proposta con la **logica di dominio più ricca**: le regole di
allergeni sono un problema reale, non un esercizio di stile.

### I 3 use case (uno per membro)

| ID | Use case | Attore | Scenari (≥2) | Parametri partizionabili |
|---|---|---|---|---|
| **UC-01** | Prenotazione del pasto per una data | Studente | 1. prenotazione con largo anticipo, 2. prenotazione oltre il limite, 3. modifica dopo prenotazione, 4. annullamento | **giorno** (oggi/domano/entro il limite/oltre/prenotazione chiusa), **tipo pasto** (pranzo/cena), **numero persone** (0/1/4/5 oltre il limite) |
| **UC-02** | Verifica compatibilità allergeni | Studente con allergia registrata | 1. piatto senza allergeni, 2. piatto con l'allergene, 3. cross-contamination, 4. allergene non nei dati | **tipo allergene** (8-14 categorie), **livello** (intolleranza/celiachia/anafilassi → severità crescente) |
| **UC-03** | Gestione del menù settimanale | Chef/catering | 1. inserimento nuovo piatto, 2. modifica prezzi, 3. pubblicazione settimana, 4. bozza non pubblicata | **giorno** (non valido/passato), **visibilità** (bozza/pubblicato), **prezzo** (negativo/zero/valido) |

### I 2 design pattern

| Pattern | Famiglia | Perché è naturale | Dove |
|---|---|---|---|
| **Strategy** | comportamentale | Il calcolo della **compatibilità** cambia per tipo di severità: un'intolleranza è un avviso, l'anafilassi è un blocco. Stesso algoritmo, regole diverse | `CalcolatoreCompatibilita` + 3 strategie |
| **Decorator** | strutturale | Il **prezzo** di un pasto si compone: base + extra + sconto abbonamento + tassa. Una classe con 6 `if` per i totali è il caso d'uso canonico di Decorator | `PrezzoBase`, `ExtraPortata`, `ScontoAbbonamento`, `Tassa` |

> Qui i due pattern sono di **famiglie diverse** (comportamentale + strutturale):
> esattamente ciò che rende la scelta facile da valutare. È la proposta con la
> coppia di pattern più solida.

### Architettura

- **3-tier** con **servizi di dominio separati** (`ServizioPrenotazioni`, `ServizioAllergeni`, `ServizioMenu`): i 3 use case sono 3 servizi, ed è una decomposizione in sottosistemi naturale da motivare.
- **Persistenza**: relazionale. Le regole di allergene stanno in una tabella `Piatto_Allergene(piatto_id, allergene, tipo_contaminazione)`. La query di compatibilità è una join: ottimo materiale per la sezione "gestione dei dati persistenti".
- **Condizioni limite**: prenotazione oltre il limite di chiusura · menu modificato dopo la prenotazione (prezzo congelato o aggiornato?) · allergene nuovo aggiunto a un piatto già prenotato · studente con allergia grave prenota mentre il piatto è in cross-contaminazione · doppio click (due prenotazioni identiche).

### Pro e contro

| ✅ Pro | ❌ Contro |
|---|---|
| **Pattern ideali e motivati** (Strategy + Decorator, famiglie diverse) | Il dominio va capito bene: le regole di contaminazione richiedono ricerca |
| Category partition eccellente (giorni, quantità, severità, allergeni) | Più entità da documentare → rischio di sforare i vincoli |
| Il class diagram ha significato naturale e non meccanico | Il docente potrebbe chiedere perché non avete usato una web app |
| Il progetto "si spiega da solo" in 5 minuti | Serve una decisione esplicita su congelamento dei prezzi |

---

## Proposta C — **Noleggio** · gestione di un autonoleggio

### Il dominio

Un autonoleggio di piccole dimensioni (5-20 veicoli) riceve prenotazioni. Il problema
non è prenotare: è la **riconciliazione**. Un cliente prenota per il 3, la vettura
rientra il 5. Il sistema deve impedire doppie prenotazioni, gestire la catena di
noleggi consecutivi (un cliente che riconsegna e riprende in giornata), e produrre
il rendiconto mensile.

È la proposta con la **logica temporale** più interessante, che è quella che il
docente misura di più.

### I 3 use case (uno per membro)

| ID | Use case | Attore | Scenari (≥2) | Parametri partizionabili |
|---|---|---|---|---|
| **UC-01** | Ricerca disponibilità e prenotazione | Cliente | 1. prenotazione libera, 2. veicolo già occupato, 3. periodo che "copre" una prenotazione, 4. ritiro e riconsegna stessa giornata | **date** (ritiro ≥ riconsegna / riconsegna < ritiro / nel passato), **classe auto** (5 categorie + non disponibile), **età conducente** (under 21 / 21-25 / over 25) |
| **UC-02** | Riconsegna, pulizia e rimessa in disponibilità | Operatore | 1. riconsegna in orario, 2. ritardo, 3. danni rilevati, 4. pulizia incompleta | **stato pulizia** (pulito/da pulire/non accessibile), **danni** (nessuno/lievi/gravi), **carburante** (pieno/mezzo/vuoto) |
| **UC-03** | Rendiconto e report operativo | Proprietario | 1. mensile per vettura, 2. per classe, 3. per periodo, 4. veicolo fuori servizio | **periodo** (mese corrente/chiuso/anno), **vettura** (attiva/fuori servizio), **formato** (PDF/CSV) |

### I 2 design pattern

| Pattern | Famiglia | Perché è naturale | Dove |
|---|---|---|---|
| **Strategy** | comportamentale | Il **calcolo del prezzo** è una formula diversa per cliente fedele, noleggio lungo, promozione. Sostituirla a runtime per cliente è il caso d'uso esatto | `CalcolatorePrezzo` + 3 strategie |
| **Observer** | comportamentale | La **riconsegna** innesca più azioni: notifica al cliente, aggiornamento disponibilità, aggioramento rendiconto, eventuale revisione della pulizia. Un osservatore per ciascun | `GestoreRiconsegna` + osservatori |

**Alternativa strutturale:** **Facade** per nascondere la complessità del calcolo
prezzo dietro un'unica operazione, e **Factory Method** per i vari tipi di veicolo.

### Architettura

- **3-tier**, con la peculiarità che il **calcolo del prezzo è un sottosistema a sé** (`SS-Prezzi`), con la sua persistenza (tabelle prezzi, sconti, stagionalità) e i suoi servizi. Decomposizione in sottosistemi facile da motivare.
- **Condizioni limite** (ricche): veicolo riconsegnato in ritardo mentre un altro cliente lo aspetta · veicolo in manutenzione che scompare dalla disponibilità · doppio noleggio della stessa auto in sovrapposizione parziale · tariffa applicata al giorno sbagliato per un cambio · noleggio che si chiude oltre la data prevista.
- **Vantaggio specifico**: il vincolo sulle **prestazioni** è naturale ("la ricerca
  su 20 veicoli deve rispondere in meno di 1 secondo") ed è verificabile davvero.

### Pro e contro

| ✅ Pro | ❌ Contro |
|---|---|
| La logica temporale (sovrapposizioni, catene di noleggi) è un ottimo materiale di stato | La sovrapposizione di intervalli è il punto dove il codice sbaglia: servono test mirati |
| Le prestazioni sono un RNF naturale e verificabile | Il dominio "noleggio auto" è invecchiato: verificare che non sembri un progetto generico |
| Conditioni limite ricche e concrete | Richiede attenzione a non confondersi con "sistema di prenotazioni generico" |
| Pattern motivati e diversi tra loro | — |

---

## Proposta D — **Archivio** · gestione documentale con revisioni

### Il dominio

Un ufficio tecnico (o un laboratorio) conserva documenti (relazioni, disegni,
verbali) che vengono **revisionati**. Oggi: cartelle condivise con nomi tipo
`relazione_v2_finale_definitiva.pdf`. Il sistema gestisce documenti con versioni,
ruoli di revisione, e **storico immutabile**.

È la proposta **più semplice da realizzare** e quella con la persistenza più
densa di concorrenza (versioni concurrenti = conflitti).

### I 3 use case (uno per membro)

| ID | Use case | Attore | Scenari (≥2) | Parametri partizionabili |
|---|---|---|---|---|
| **UC-01** | Caricamento e versionamento di un documento | Utente | 1. prima versione, 2. nuova versione, 3. ricaricamento identico, 4. formato non ammesso | **formato** (pdf/docx/zip/altro), **dimensione** (vuoto/piccolo/2 GB/troppo grande), **nome** (vuoto/troppo lungo/caratteri invalidi) |
| **UC-02** | Revisione e approvazione | Revisore | 1. approvazione, 2. rigetto con note, 3. revisione di una versione già approvata, 4. revisione di se stesso | **stato** (nuovo/in revisione/approvato/rigettato), **autore** (autore del documento/altro/revisore stesso) |
| **UC-03** | Ricerca e recupero versioni | Utente | 1. ricerca per testo, 2. per data, 3. per versione storica, 4. documento archiviato | **criterio** (testo/data/tag/autore), **versione richiesta** (ultima/precedente/specifica/inesistente) |

### I 2 design pattern

| Pattern | Famiglia | Perché è naturale | Dove |
|---|---|---|---|
| **Strategy** | comportamentale | La **ricerca** su criteri diversi è il caso Strategy per antonomasia: filtro testuale, per data, per tag, combinati | `FiltroRicerca` + implementazioni |
| **Observer** | comportamentale | Il caricamento di una nuova versione notifica: la vista utente, il pannello del revisore, l'indice di ricerca | `Documento` + osservatori |

**Alternativa creazionale:** **Factory Method** / **Abstract Factory** per creire
oggetti documento in base al formato (PDF → `DocumentoPDF` con metodo `estraiTesto`,
DOCX → `DocumentoDOCX`, ZIP → `ArchivioZIP` con metodo `estraiElenco`). È **il**
caso d'uso canonico di Factory: ogni tipo sa come estrarre i propri metadati.

### Architettura

- **3-tier**, con il vantaggio che il **formato del documento** è una scelta di design naturale: ognuno ha un parser diverso → questo è il **mapping HW/SW e la strategia di persistenza** (i metadati sono relazionali, il contenuto è su filesystem: due strategie diverse da motivare, con pro e contro).
- **Condizioni limite**: due revisioni simultanee della stessa versione (conflito) · upload di un file identico (duplicato) · documento che supera lo spazio disponibile · recupero di una versione eliminata · ricerca durante l'indicizzazione.

### Pro e contro

| ✅ Pro | ❌ Contro |
|---|---|
| **Il più veloce da realizzare**: se il tempo stringe, questo lo finisci | È "solo" un gestionale documentale: meno spettacolare |
| Factory Method è il pattern più facile da spiegare e da valutare bene | Pochi RNF "interessanti": le prestazioni sono il punto forte |
| La gestione delle versioni è un problema reale e riconoscibile | Rischio: se il vostro progetto esistente è simile, diventa plagiato |
| Il dual storage (DB + filesystem) è un buon esercizio di rationale | |

---

## Parte 3 — Confronto

| | **A HelpDesk** | **B MensaCampus** | **C Noleggio** | **D Archivio** |
|---|---|---|---|---|
| Complessità di realizzazione | media | alta | media | **bassa** |
| Ricchezza della logica di dominio | alta | **molto alta** | alta | media |
| Pattern naturali | buona (con forzatura su State) | **ottima, famiglie diverse** | buona | buona |
| Category partition | ottima | **ottima** | ottima | buona |
| RNF prestazioni naturale | media | bassa | **alta** | media |
| Simile a materiali noti del docente | no | no | no | no |
| Rischio di andare lunghi | medio | **alto** | medio | **basso** |
| **Adatta se…** | volete un dominio corporate e neutro | volete il progetto più completo e distintivo | vi piace la logica temporale | **il tempo è il vincolo principale** |

### La mia indicazione

**Scegliete B (MensaCampus) se avete tempo.** È la proposta in cui i vincoli del
corso sono più naturali: i pattern sono giustificati senza forzature, la logica di
dominio è ricca, e il RAD ha materiale reale. È anche il progetto in cui è più
difficile dire "questo l'ho scritto solo per fare punti".

**Scegliete D (Archivio) se il tempo è stretto o se la discussione è vicina.**
Un progetto finito e documentato bene vale più di un progetto ambizioso e a metà.

**Scegliete C (Noleggio) se vi piace lavorare sulla logica temporale** e volete
un RNF di prestazioni veramente misurabile.

**A (HelpDesk)** è la scelta più "neutra" e la più sicura sul piano del dominio,
ma richiede attenzione a non usare State come pattern *e* a fare il 2° statechart
su un oggetto diverso.

---

## Parte 4 — Se decidete di usare il vostro progetto full-stack esistente

Questa sezione riguarda voi: avete già un progetto funzionante di un altro corso.

### Il progetto esistente è un vantaggio reale

- Il codice **esiste e funziona**: la parte più lenta di un progetto da zero è
  costruire qualcosa che gira. Voi avete già quello.
- Potete misurare i requisiti non funzionali **sui fatti**, non sulle stime.
- Potete scrivere il RAD **a posteriori ma vero**: descrivete il sistema che è,
  non quello che sperate che sia.

### Ma ci sono quattro rischi reali

| # | Rischio | Gravità | Come lo gestite |
|---|---|---|---|
| 1 | **Il progetto è più grande di 3 use case.** Il vincolo è un *tetto*, non un obiettivo | 🔴 alta | **Ridimensionate lo scope documentato a esattamente 3 casi d'uso.** Tutto il resto esiste ma non è documentato — e communicate esplicitamente cosa avete escluso e perché (§1.2 "Ambito" del RAD) |
| 2 | **Il progetto è stato copiato o generato** da un'altra fonte | 🔴 alta | Il docente usa il **plagiarism detection** e lo dichiara nei criteri. Se il progetto è vostro (l'hai scritto tu, o nel team di allora), non c'è problema: **dichiara la provenienza nel SoW**. Se ha parti di terzi, devi rifare quelle parti o cambiar progetto |
| 3 | **Non sapete spiegare il codice** | 🔴 alta | Nessuna documentazione al mondo regge se in discussione non rispondi alle domande sul codice. Rileggi il codice prima di scrivere l'ODD |
| 4 | **Il progetto non è Java / Maven / JUnit** | 🟡 media | Verifica i vincoli tecnologici del vostro SOW. Se il progetto è in un altro stack, **decidete ora** se riscriverlo o se dichiarare lo stack reale nel SoW §4.7 |

### Il percorso consigliato in 5 passi

**Passo 1 — Audit (2-3 ore).** Rispondi per iscritto:

1. Il dominio ha **almeno 3 casi d'uso** che si possono descrivere bene?
2. Ci sono **almeno 2 pattern** che il codice usa *davvero* (non forzati)?
3. Ha una **persistenza reale** (non solo in memoria)?
4. Ha **ruoli/permessi** distinti?
5. Il codice è **vostro** e lo capite?

Se le risposte sono tutte sì → **procedete con il progetto esistente**.
Se 1 o 2 sono no → **partite da zero** (una delle proposte qui sopra) o fatene
una versione ridotta che le soddisfa.

**Passo 2 — Ridimensiona a 3 use case.** Scegli i 3 casi d'uso *più rappresentativi*
del tuo progetto e **documenta solo quelli**. Gli altri vai a scriverli in
`1_RAD/` §1.2 come "funzionalità fuori scope". Questo non è censurare: è scoping,
ed è esattamente ciò che il SOW chiede.

**Passo 3 — Reverse-engineering del RAD (1 settimana).** Ricostruite la
documentazione **dal codice vero**:

- I **requisiti funzionali** si deducono dalle schermate e dagli endpoint che
  esistono davvero.
- I **non funzionali** si misurano: tempi di risposta reali, dimensione del DB,
  numero di utenti Concurrenti. *«Il sistema risponde in 340 ms con 5000 record,
  misurato il 3 novembre»* è un RNF di prim'ordine. Un RNF inventato è fragile.
- Il **class diagram** si disegna dal codice: dal package, dalle classi, dalle
  associazioni nei costruttori e nei metodi. È un ottimo esercizio: obbliga a
  capire l'architettura propria.

**Passo 4 — Riallinea i nomi (mezza giornata).** Il progetto esistente ha
nominato le cose in un certo modo. I documenti devono usare **gli stessi nomi**,
o meglio: rinominate il codice in termini di dominio chiari (`UserService` →
`GestioneUtenti`) e usate quelli ovunque. Una delle voci del check-list SDD è
esattamente *"i nomi dei casi d'uso sono usati coerentemente"*.

**Passo 5 — Ricostruisci la cronologia (mezza giornata).** Il progetto è stato
fatto in un altro corso, magari mesi fa. Per GitHub, Trello e Slack servono
**tracce di questo progetto, di questi 3 membri, in queste date**.
Non potete fingere. Ma potete — e dovete — **ricominciare le tracce da adesso**:
repository nuovo del progetto IS, primo commit oggi, board Trello creato oggi,
canale Slack aperto oggi. Le linee guida dicono che i tool siano usati *durante
il progetto*, e lo saranno: dalla settimana prossima alla consegna.

### Cosa guadagnate e cosa perdete

| | Progetto esistente | Da zero |
|---|---|---|
| Tempo per avere qualcosa che funziona | **immediato** | 2-3 settimane |
| RNF misurabili | **sì, subito** | da stimare |
| Rischio di non finire | **basso** | medio-alto |
| Rischio di non capire il codice | **medio** | basso |
| Percezione del docente ("ha solo adattato un progetto") | **possibile** | nessuno |
| Plagiarism | **da verificare** | nessuno |

> **Il punto critico è l'ultimo.** Se il docente riconosce il progetto di un altro
> corso, il giudizio non è "ha riutilizzato", è "non ha prodotto nulla di nuovo".
> La difesa è una sola: averlo **ridisegnato riducendolo a 3 use case e
> riscrittolo** in modo che la documentazione sia stata prodotta ex nihilo per
> questo corso. Se il ridimensionamento è solo cosmetico, non regge.

---

## Parte 5 — Cosa fare adesso

1. **Leggete** `../INDICE.md` §3 (i numeri che dovete rispettare).
2. **Scegliete** una proposta (o confermate il progetto esistente con l'audit).
3. **Rinominate** `IS3` in tutta la cartella con la sigla definitiva.
4. **Riaggiornate** il SoW: scopo, capacità, team, milestone, **pattern prescelti**.
5. **Compilate** `1_RAD/IS3_CL_RAD.md` e `2_SDD/IS3_CL_SDD.md` a circa una settimana
   dalla consegna — sono lo strumento che vi fa prendere 24 invece di 30.