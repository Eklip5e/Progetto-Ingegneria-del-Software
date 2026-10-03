# Check-list RAD — Progetto `IS3`

> **Strumento di autocontrollo, NON un deliverable da consegnare.**
> Riprende le voci del check-list del docente (`C07_CL_RAD`, 42 voci nella versione
> di riferimento) e le rende una lista di lavoro utilizzabile.
>
> **Come si usa:** a circa una settimana dalla consegna, scegliere la risposta
> **SI / NO / NA** per ogni voce e annotare le note. I **NA** devono essere
> giustificati. Ogni **NO** è una lacuna da colmare prima della consegna.
>
> ⚠️ Il docente usa questo strumento per valutare. Compilarlo a mano è il modo
> più economico di evitare un rigetto su un dettaglio formale.

**Progetto:** `IS3` · **Versione documento:** _0.1_ · **Autore del controllo:** _Cognome_
**Data:** _gg/mm/aaaa_

| Voci soddisfatte | N/A | Non soddisfatte | % soddisfatte |
|---|---|---|---|
| _0_ | _0_ | _0_ | _0%_ |

---

## A. Aspetti di carattere generale

| # | Voce | Risposta | Note |
|---|---|---|---|
| 1 | Il nome del documento rispetta il formato `<Sigla>_<Acronimo>_ver.<Versione>`? | _SI_ | `IS3_RAD_ver._1.0` |
| 2 | Il documento è strutturato gerarchicamente con l'indice **esatto** previsto dal corso? | _SI_ | vedi struttura in `IS3_RAD_ver.0.1.md` |
| 3 | L'indice dei contenuti punta correttamente a tutti i capitoli, con rientri e stili? | _SI_ | |
| 4 | L'indice è aggiornato rispetto al corpo del documento? | _SI_ | |
| 5 | I font utilizzati sono quelli previsti dal template? | _SI_ | |
| 6 | La formattazione è uniforme (stili di titolo, corpo, tabelle)? | _SI_ | |
| 7 | Il documento è privo di errori sintattici, grammaticali e di formattazione? | _SI_ | doppi spazi, spazi prima di punteggiatura |
| 8 | Il documento è coerente con gli altri deliverable e con le versioni dichiarate? | _SI_ | controlla la revision history |
| 9 | L'identificativo e la denominazione corrispondono a quanto dichiarato nel SoW? | _SI_ | |
| 10 | Ogni documento citato è denominato conformemente al SoW? | _SI_ | |

## B. Struttura del documento

| # | Voce | Risposta | Note |
|---|---|---|---|
| 11 | Sono presenti: Introduzione con obiettivo, ambito, criteri di successo, definizioni, riferimenti, organizzazione? | _SI_ | §1.1-§1.6 |
| 12 | Il capitolo "Sistema attuale" è presente e NON vuoto? | _SI_ | §2 |
| 13 | Il capitolo "Sistema proposto" è presente con tutti i paragrafi richiesti? | _SI_ | §3 |
| 14 | Il glossario finale è presente? | _SI_ | §4 |
| 15 | L'introduzione non contiene informazioni presenti altrove nel documento? | _SI_ | no ridondanza |
| 16 | La sezione "Organizzazione del documento" descrive lo scopo di ogni capitolo? | _SI_ | §1.6 |

## C. Requisiti funzionali

| # | Voce | Risposta | Note |
|---|---|---|---|
| 17 | I requisiti funzionali sono specificati in numero **da 6 a 12** (2-4 per membro × 3)? | _SI_ | _N. totale: ___ |
| 18 | Ogni membro ha **2-4** requisiti funzionali? | _SI_ | _C1:__ C2:__ C3:__ |
| 19 | I requisiti sono in forma attiva, con soggetto esplicito? | _SI_ | |
| 20 | I requisiti sono enunciati positivi (niente "deve poter", niente "must")? | _SI_ | |
| 21 | I requisiti sono sintatticamente completi (`[Condizione][Soggetto][Azione][Oggetto][Vincolo]`)? | _SI_ | |
| 22 | I termini usati sono definiti nel glossario? | _SI_ | |
| 23 | Ogni requisito è **singolare** (un requisito = una funzione, niente "e")? | _SI_ | |
| 24 | I requisiti sono verificabili (si può dire se sono soddisfatti)? | _SI_ | |
| 25 | I requisiti sono coerenti tra loro (nessuna contraddizione)? | _SI_ | |
| 26 | I requisiti sono coperti da almeno uno scenario? | _SI_ | |

## D. Requisiti non funzionali

| # | Voce | Risposta | Note |
|---|---|---|---|
| 27 | I requisiti non funzionali sono specificati in numero **da 6 a 12**? | _SI_ | _N. totale: ___ |
| 28 | Ogni membro ha **2-4** requisiti non funzionali? | _SI_ | _C1:__ C2:__ C3:__ |
| 29 | **Tutte e 9** le sottosezioni sono presenti (Usabilità, Affidabilità, Prestazioni, Supportability, Implementazione, Interfacce, Operation, Packaging, Legali)? | _SI_ | ⚠️ **nessuna sezione vuota** |
| 30 | I requisiti non funzionali sono quantificati misurabilmente? | _SI_ | niente "deve essere veloce" |
| 31 | I RNF sono classificati correttamente (una prestazione non è usabilità)? | _SI_ | |
| 32 | I RNF sono coerenti con i vincoli tecnologici del SoW? | _SI_ | Java 17, Maven, JUnit 5 |

## E. Modello del sistema

| # | Voce | Risposta | Note |
|---|---|---|---|
| 33 | Gli scenari sono specificati in numero **da 6 a 12** (2-4 per membro)? | _SI_ | _N. totale: ___ |
| 34 | Gli scenari sono **istanze concrete** con valori reali, non ripetizioni del caso d'uso? | _SI_ | |
| 35 | Ci sono **esattamente 3** casi d'uso (1 per membro)? | _SI_ | ⚠️ **non di più** |
| 36 | Il diagramma dei casi d'uso è presente, con attori fuori dal boundary? | _SI_ | |
| 37 | Ci sono **esattamente 2** sequence diagram (1 ogni 2 membri)? | _SI_ | ⚠️ **non di più** |
| 38 | I sequence diagram fanno riferimento agli use case specificati? | _SI_ | |
| 39 | Ci sono **esattamente 2** statechart diagram (1 ogni 2 membri)? | _SI_ | ⚠️ **non di più** |
| 40 | Ci sono **esattamente 1** activity diagram e **1** class diagram per team? | _SI_ | |
| 41 | Sono specificati gli oggetti **boundary, control, entity** per gli use case? | _SI_ | |
| 42 | Sono presenti i mock-up dell'interfaccia e i percorsi di navigazione? | _SI_ | §3.4.5 |

---

## Esito

| | |
|---|---|
| **Voci soddisfatte** | _N. / 42_ |
| **Voci N/A** (giustificate) | _N._ |
| **Voci non soddisfatte** | _N._ |
| **Percentuale** | _N_% |

> **Regola del 70%** usata dal docente: si seleziona 70% se la voce non è soddisfatta
> per almeno il 70%; 50% se non è soddisfatta per almeno il 50% ma meno del 70%.
> Nel check-list di riferimento il gruppo BiblioNet aveva 42/42 con 3 NA.

**Le 3 voci NA tipiche (se legittime):** _es. "Sistema attuale" se il progetto è
greenfield → in realtà va descritto il processo manuale, quindi NA non sempre
applicabile. Verifica con il docente._

---

## Azioni correttive

| Voce | Azione | Responsabile | Scadenza | Fatto |
|---|---|---|---|---|
| _n._ | _cosa devo fare_ | _Cognome_ | _gg/mm_ | ☐ |
| _n._ | | | | ☐ |