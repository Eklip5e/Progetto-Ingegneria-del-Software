# TIRT — Test Incident Report Tracker — Progetto `IS3`

> **Scheletro 0.1 — da compilare.**
>
> Il **TIRT** è il **registro cumulativo**: **una riga per ogni incidente**,
> dall'apertura alla chiusura. A differenza del TIR (che descrive un incidente in
> dettaglio), il TIRT è la **vista d'insieme**.
>
> Il docente lo valuta perché mostra:
> - che i difetti sono stati **realmente gestiti** (non solo corretti: anche chiusi)
> - la loro **evoluzione temporale**
> - che c'è stato un **processo**, non solo un resultado finale

| Test Incident Report Tracker | `IS3` | |
|---|---|---|
| **Versione** | 0.1 | |
| **Data** | _gg/mm/aaaa_ | |
| **Aggiornato da** | _Cognome_ | |
| **Sessioni di test** | _3 (vedi §3)_ | |

---

## 1. Registro incidenti

| ID | Data apertura | Titolo | Severità | Priorità | Componente | Rilevato da (test) | Assegnato a | Stato | Data chiusura | TIR |
|---|---|---|---|---|---|---|---|---|---|---|
| INC-01 | _gg/mm_ | _Password corta accettata_ | Critico | Alta | `_Validatore_` | _STF-04_ | _Cognome1_ | ✅ Risolto | _gg/mm_ | _TIR-01_ |
| INC-02 | _gg/mm_ | _Email duplicata non gestita_ | Maggiore | Media | `_ServiceUtenti_` | _STF-03_ | _Cognome2_ | ✅ Risolto | _gg/mm_ | _TIR-02_ |
| INC-03 | _gg/mm_ | _Messaggio errore illeggibile_ | Minore | Bassa | `_View_` | _manuale_ | _Cognome3_ | 🔄 In correzione | — | _TIR-03_ |
| INC-04 | _gg/mm_ | _…_ | | | | | | | | |

---

## 2. Riepilogo quantitativo

| Severità | Aperti | Risolti | Chiusi senza correzione | Totale |
|---|---|---|---|---|
| Bloccante | 0 | 0 | 0 | 0 |
| Critico | 0 | 1 | 0 | 1 |
| Maggiore | 0 | 1 | 0 | 1 |
| Minore | 1 | 0 | 0 | 1 |
| **Totale** | **1** | **2** | **0** | **3** |

| Metrica | Valore |
|---|---|
| Incidenti totali rilevati | _3_ |
| Incidenti risolti | _2_ |
| Incidenti aperti alla consegna | _1_ |
| Tasso di risoluzione | _67%_ |
| Incidenti con test di regressione | _2/2_ |
| Incidenti riaperti | _0_ |

> **Se ci sono incidenti Bloccanti o Critici aperti alla consegna**, il criterio
> di uscita del TP non è soddisfatto e il progetto non è pronto.

---

## 3. Distribuzione per componente

| Componente | Incidenti | Test case che coprono il componente |
|---|---|---|
| `_Validatore_` | 1 | _STF-04_ |
| `_ServiceUtenti_` | 1 | _STF-03_ |
| `_View_` | 1 | _manuale_ |

> Un componente con incidenti ripetuti è un **segnale di design debole**.
> Se la stessa classe ha 3 incidenti, il problema è nell'SDD, non nel codice.

---

## 4. Distribuzione per sessione di test

| Sessione | Data | Test eseguiti | Esiti positivi | Incidenti aperti | Incidenti risolti in sessione |
|---|---|---|---|---|---|
| S-1 | _gg/mm_ | _20_ | _18_ | 2 | 0 |
| S-2 | _gg/mm_ | _22_ | _22_ | 1 | 2 |
| S-3 | _gg/mm_ | _8_ | _8_ | 1 | 0 |

---

## 5. Analisi delle cause

| Tipo di errore | Incidenti | % | Azione correttiva |
|---|---|---|---|
| Validazione input mancante | 2 | 67% | _classe Validatore centralizzata + test obbligatori sui boundary_ |
| Dati duplicati non gestiti | 1 | 33% | _vincolo di unicità sul DB + gestione errore_ |
| Refusi UI | 0 | — | — |

> Questa sezione è quella che il docente legge per capire se avete **imparato**
> qualcosa dal progetto. Un registro di incidenti senza analisi delle cause è
> una lista, non un report.

---

## 6. Incidenti chiusi

| ID | Causa | Risolto con | Test di regressione |
|---|---|---|---|
| INC-01 | _controllo solo `isEmpty()`_ | _aggiunto controllo lunghezza minima_ | `_TC-04_` |
| INC-02 | _nessun vincolo unique_ | _vincolo UNIQUE su email_ | `_TC-05_` |

---

## 7. Incidenti riaperti

| ID | Riapertura | Motivo | Risoluzione definitiva |
|---|---|---|---|
| — | — | — | — |

> *Una riga vuota qui è normale. Una riga compilata richiede spiegazione.*

---

## 8. Tracciabilità con la matrice

| Requisito | Test case | Incidenti su quel requisito | Stato finale |
|---|---|---|---|
| RF-02 | _STF-04_ | _INC-01 (risolto)_ | ✅ |
| RF-01 | _STF-03_ | _INC-02 (risolto)_ | ✅ |