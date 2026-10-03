# Matrice di Tracciabilità — Progetto `IS3`

> **Scheletro 0.1 — da compilare.**
>
> Non è un documento "da fare per completezza": è la prova che il progetto è
> **coerente dall'inizio alla fine**. Un requisito senza test, o un test che non
> copre alcun requisito, sono difetti che la matrice rende visibili.

| Matrice di Tracciabilità | `IS3` | |
|---|---|---|
| **Versione** | 0.1 | |
| **Data** | _gg/mm/aaaa_ | |
| **Autori** | _tutti_ | |
| **Copre** | RAD v.\_, SDD v.\_, ODD v.\_, TCS v.\_ | |

---

## 1. Scopo

_Questo documento garantisce che ogni requisito del RAD sia tracciato fino ai
test che lo verificano, e che ogni test copra un requisito. Una matrice
bidirezionale: si legge sia per righe (requisito → test) sia per colonne
(test → requisito)._

---

## 2. Matrice bidirezionale

| Req | Tipo | UC | Scenario | Design goal | Sottosistema | Pattern | Test case | Esito |
|---|---|---|---|---|---|---|---|---|
| RF-01 | F | UC-01 | SC-01 | — | SS-01 | — | _TC-01_ | _Pass_ |
| RF-02 | F | UC-01 | SC-02 | — | SS-01 | _P1_ | _TC-02_ | _Pass_ |
| RF-03 | F | UC-02 | SC-03 | DG-01 | SS-02 | — | _TC-03_ | _Pass_ |
| RF-04 | F | UC-02 | SC-04 | — | SS-02 | — | _TC-04_ | _Pass_ |
| RF-05 | F | UC-03 | SC-05 | DG-03 | SS-01 | _P2_ | _TC-05_ | _Pass_ |
| RF-06 | F | UC-03 | SC-06 | — | SS-03 | — | _TC-06_ | _Pass_ |
| RNF-01 | NF | UC-0x | — | DG-01 | — | — | _TC-07_ | _Pass_ |
| RNF-02 | NF | UC-0x | — | DG-02 | — | — | _TC-08_ | _Pass_ |
| RNF-03 | NF | — | — | DG-0x | — | — | _TC-09_ | _Pass_ |
| _…_ | | | | | | | | |

**Legenda:** F = funzionale · NF = non funzionale · P1/P2 = design pattern

---

## 3. Copertura dei requisiti

> **Ogni requisito del RAD deve comparire in §2.** Se un RF o RNF non c'è, manca.

| Requisito | Coperto da test? | Stato |
|---|---|---|
| RF-01 | _TC-01_ | ✅ |
| RF-02 | _TC-02_ | ✅ |
| RF-03 | _TC-03_ | ✅ |
| RNF-03 | _TC-09_ | ⚠️ coperto solo da test manuale |
| _…_ | | |

**Totale requisiti:** _12_ · **Coperti:** _12_ (100%)

---

## 4. Copertura dei test

> Verifica il contrario: nessun test deve essere "orfano".

| Test case | Copre | Tipo | Autore |
|---|---|---|---|
| _TC-01_ | RF-01 | system | _Cognome_ |
| _TC-02_ | RF-02 | system | _Cognome_ |
| _UT-01_ | RF-01 | unit | _Cognome_ |
| _…_ | | | |

---

## 5. Copertura dei vincoli del SOW

| Vincolo SOW | Artefatto che lo soddisfa | Dove |
|---|---|---|
| 1 use case per membro | 3 use case | RAD §3.4.2 |
| 1 sequence diagram ogni 2 membri | 2 sequence diagram | RAD §3.4.4 |
| 1 statechart ogni 2 membri | 2 statechart | RAD §3.4.4 |
| 1 activity diagram per team | 1 | RAD §3.4.4 |
| 1 class diagram per team | 1 | RAD §3.4.3 |
| 1 diagramma decomposizione sottosistemi | 1 | SDD §3.2 |
| 1 deployment diagram | 1 | SDD §3.3 |
| 2-4 requisiti funzionali per membro | _6-12 totali_ | RAD §3.2 |
| 2-4 requisiti non funzionali per membro | _6-12 totali_ | RAD §3.3 |
| 2-4 scenari per membro | _6-12 totali_ | RAD §3.4.1 |
| 2-4 design goal per membro | _6-12 totali_ | SDD §1.2 |
| Trade-off su almeno 2 coppie | 2 coppie | SDD §1.3 |
| 2 design pattern per team | 2 | ODD §2, §3 |
| 1 unit test CP per studente | 3 | `5_testing/…/category_partition/` |
| 1 system test CP per studente | 3 | `5_testing/…/category_partition/` |

- [ ] **Tutti i 15 vincoli soddisfatti.**

---

## 6. Tracciabilità inversa: dal test al requisito

> Serve quando il docente chiede "questo test perché esiste?".
> Ogni test deve essere giustificato da almeno un requisito.

| Test | Requisito che giustifica | Se il requisito cambia, il test cambia? |
|---|---|---|
| _TC-01_ | RF-01 | _sì/no_ |
| _UT-01_ | RF-01 | _..._ |

---

## 7. Incidencias e difetti (riferimento a TIRT)

| Difetto | Requisito coinvolto | Test che l'ha rilevato | Incident ID | Stato |
|---|---|---|---|---|
| _es. campo accetta stringa vuota_ | RNF-01 | _TC-07_ | _INC-01_ | _Risolto_ |

---

## 8. Note

_Qualsiasi decisione che non è evidente dalla matrice va motivata qui: es. un
requisito coperto solo da test manuale, un test che copre più requisiti, un
requisito escluso e perché._ _TBD_