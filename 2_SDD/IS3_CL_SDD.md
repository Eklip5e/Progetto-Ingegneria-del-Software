# Check-list SDD — Progetto `IS3`

> **Strumento di autocontrollo, NON un deliverable da consegnare.**
> Riprende le voci del check-list del docente (`C07_CL_SDD`, 51 voci nella versione
> di riferimento).
>
> **Attenzione:** nella versione di riferimento, il gruppo BiblioNet aveva
> **49/51 soddisfatte con 2 non soddisfatte** — entrambe sulla tracciabilità
> tra requisiti non funzionali e design goal. Sono esattamente il tipo di errore
> che viene ripetuto: controlla il §D con attenzione.

**Progetto:** `IS3` · **Versione documento:** _0.1_ · **Autori del controllo:** _tutti_
**Data:** _gg/mm/aaaa_

| Voci soddisfatte | N/A | Non soddisfatte | % soddisfatte |
|---|---|---|---|
| _0_ | _0_ | _0_ | _0%_ |

---

## A. Aspetti di carattere generale

| # | Voce | Risposta | Note |
|---|---|---|---|
| 1 | Il documento è strutturato gerarchicamente, con l'indice che ne evidenzia l'annidamento? | _SI_ | |
| 2 | L'indice dei contenuti è aggiornato e punta correttamente alle sezioni? | _SI_ | |
| 3 | Sono stati trattati tutti gli aspetti del System Design (allocazione HW, persistenza, condizioni limite)? | _SI_ | §3.2-§3.7 |
| 4 | Il documento è correttamente impaginato? | _SI_ | |
| 5 | Lo stile è piano e scorrevole, forma diretta, periodi brevi, poche incidentali? | _SI_ | |
| 6 | Il documento è coerente con gli altri deliverable e le versioni sono in §1.5? | _SI_ | ⚠️ controlla i numeri di versione |
| 7 | L'identificativo e la denominazione corrispondono al SoW? | _SI_ | |
| 8 | Ogni documento citato è denominato conformemente al SoW? | _SI_ | |
| 9 | Il documento è privo di errori sintattici e di formattazione? | _SI_ | |
| 10 | Ogni concetto introdotto è definito nel glossario? | _SI_ | §5 |

## B. Rationale delle scelte (le 5 voci più importanti)

> Il check-list chiede esplicitamente, per **ciascuna** delle 5 scelte:
> rationale fornito + argomenti **a favore e contrari** + coerenza con i design goal.
> Una voce "NO" qui è una delle cause più frequenti di valutazione mediocre.

| # | Voce | Risposta | Note |
|---|---|---|---|
| 11 | **Rationale dell'architettura software** fornito, con pro e contro, coerente con i design goal? | _SI_ | §3.1-§3.2 |
| 12 | **Rationale del mapping HW/SW** fornito, con pro e contro? | _SI_ | §3.3 |
| 13 | **Rationale della gestione dei dati persistenti** fornito, con pro e contro? | _SI_ | §3.4 |
| 14 | **Rationale del controllo degli accessi** fornito, con pro e contro? | _SI_ | §3.5 |
| 15 | **Rationale del flusso di controllo** fornito, con pro e contro? | _SI_ | §3.6 |

> ⚠️ **Se scrivete solo il "pro"**, le 5 voci valgono zero. Il "contro" è ciò
> dimostra che avete considerato l'alternativa.

## C. Design goal e trade-off

| # | Voce | Risposta | Note |
|---|---|---|---|
| 16 | Sono stati identificati e descritti gli obiettivi di design? | _SI_ | §1.2 |
| 17 | Sono stati individuati i trade-off fra gli obiettivi identificati? | _SI_ | §1.3 |
| 18 | **Tutti** i design goal rispettano i requisiti non funzionali? | _SI_ | ⚠️ |
| 19 | **Ogni** design goal è ricondotto a un RNF o a un'esigenza di management? | _SI_ | ⚠️ |
| 20 | I design goal sono stati **prioritizzati**? | _SI_ | |
| 21 | I design goal sono **realistici** (non irraggiungibili)? | _SI_ | |
| 22 | **Ogni** requisito non funzionale è stato considerato ai fini dei design goal? | _SI_ | ⚠️ |

> **Voci 18, 19 e 22 sono le 2 che BiblioNet non aveva soddisfatto.**
> Verificale in modo esplicito: fai una tabella RNF ↔ DG e conta le caselle vuote.

**Tabella di controllo RNF ↔ DG:**

| | DG-01 | DG-02 | DG-03 | DG-04 | DG-05 | DG-06 |
|---|---|---|---|---|---|---|
| RNF-01 | ✅ | | | | | |
| RNF-02 | | ✅ | | | | |
| _RNF-03_ | | | | | | |
| _RNF-04_ | | | | | | |
| _RNF-05_ | | | ✅ | | | |
| _RNF-06_ | | | | ✅ | | |
| _RNF-07_ | | | | | | |
| _RNF-08_ | | | | | | |
| _RNF-09_ | | | | | | |

> **Casella vuota** = RNF non considerato = **voce 22 non soddisfatta**.
> **Nessun DG senza RNF** = **voce 19 non soddisfatta**.

## D. Architettura

| # | Voce | Risposta | Note |
|---|---|---|---|
| 23 | È stata identificata e descritta l'architettura software del sistema? | _SI_ | §3.1-§3.2 |
| 24 | Il livello di accoppiamento fra sottosistemi è adeguato rispetto ai design goal? | _SI_ | |
| 25 | I sottosistemi sono realmente sottosistemi (con interfaccia e responsabilità autonoma)? | _SI_ | non classi rinominate |
| 26 | I nomi dei sottosistemi sono significativi e rispecchiano le responsabilità? | _SI_ | niente `Modulo1` |
| 27 | Il diagramma di **decomposizione in sottosistemi** è presente (1 per team)? | _SI_ | |
| 28 | Il diagramma è accompagnato da descrizione e motivazione? | _SI_ | |
| 29 | Il **deployment diagram** è presente (1 per team)? | _SI_ | |
| 30 | Il deployment diagram è accompagnato da descrizione e motivazione? | _SI_ | |

## E. Dati, accessi e flusso di controllo

| # | Voce | Risposta | Note |
|---|---|---|---|
| 31 | La strategia di gestione dei dati persistenti è definita? | _SI_ | §3.4 |
| 32 | Il modello dati è completo (entità, PK, relazioni)? | _SI_ | |
| 33 | Sono definite le politiche di controllo degli accessi? | _SI_ | §3.5 |
| 34 | I ruoli e i permessi sono definiti senza ambiguità? | _SI_ | |
| 35 | Il flusso di controllo globale è definito? | _SI_ | §3.6 |
| 36 | La gestione degli errori è definita? | _SI_ | |
| 37 | Le condizioni limite sono identificate e descritte? | _SI_ | §3.7 — ⚠️ non omettere |

## F. Servizi

| # | Voce | Risposta | Note |
|---|---|---|---|
| 38 | I servizi offerti da ogni sottosistema sono definiti? | _SI_ | §4 |
| 39 | Le firme dei servizi sono specificate (input, output, errori)? | _SI_ | |
| 40 | Gli errori di ogni servizio sono enumerati? | _SI_ | |

## G. Object Design

| # | Voce | Risposta | Note |
|---|---|---|---|
| 41 | Sono identificati i **2 design pattern** del team? | _SI_ | cenni ODD |
| 42 | Per ogni pattern sono indicati **obiettivo** e **come sarebbe implementato**? | _SI_ | |
| 43 | I pattern sono scelti **tra quelli presentati a lezione**? | _SI_ | ⚠️ verificare il syllabus |
| 44 | Sono presentati i trade-off dell'uso di ciascun pattern? | _SI_ | |

## H. Verifiche trasversali

| # | Voce | Risposta | Note |
|---|---|---|---|
| 45 | I diagrammi sono in formato **modificabile** (non solo PNG)? | _SI_ | `.drawio` / `.puml` |
| 46 | I diagrammi sono coerenti tra loro e con il testo? | _SI_ | |
| 47 | Non sono stati prodotti object diagram (non valutati)? | _SI_ | |
| 48 | I nomi dei casi d'uso del RAD sono usati coerentemente anche nell'SDD? | _SI_ | niente rinomine |
| 49 | Le classi dell'ODD sono presenti nel class diagram del RAD? | _SI_ | ⚠️ coerenza RAD↔ODD |
| 50 | Il glossario contiene i termini tecnici usati? | _SI_ | §5 |
| 51 | Il documento è completo: nessuna sezione con solo placeholder? | _SI_ | |

---

## Esito

| | |
|---|---|
| **Voci soddisfatte** | _N. / 51_ |
| **Voci N/A** | _N._ |
| **Voci non soddisfatte** | _N._ |
| **Percentuale** | _N_% |

## Azioni correttive

| Voce | Azione | Responsabile | Scadenza | Fatto |
|---|---|---|---|---|
| _19/22_ | _costruire la tabella RNF ↔ DG e colmarla_ | _Cognome?_ | _gg/mm_ | ☐ |
| _13_ | _riscrivere il rationale della persistenza con pro/contra_ | _Cognome?_ | _gg/mm_ | ☐ |
| _37_ | _aggiungere 2 condizioni limite_ | _Cognome?_ | _gg/mm_ | ☐ |