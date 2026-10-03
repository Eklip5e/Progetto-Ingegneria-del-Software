# TSR — Test Summary Report — Progetto `IS3`

> **Scheletro 0.1 — da compilare.**
>
> ⚠️ **Il TSR si scrive ULTIMO**, dopo che tutti i test sono stati eseguiti.
> Riassume i risultati di tutti i TIR. I dati qui devono essere **quelli reali**,
> non quelli desiderati: un TSR falsato è peggio di un TSR con risultati negativi.

| Test Summary Report | `IS3` | |
|---|---|---|
| **Versione** | 0.1 | |
| **Data** | _gg/mm/aaaa_ | |
| **Autori** | _tutti_ | |
| **TP** | `IS3_TP_ver._1.0` | |
| **TCS** | `IS3_TCS_ver._1.0` | |
| **TIRT** | `IS3_TIRT_ver._1.0` | |

---

## 1. Scopo

_2 paragrafi. Quali artefatti sono stati testati, con quale tecnica, e su quale
ambiente. Riepilogo del TP._ _TBD_

---

## 2. Riepilogo dell'esecuzione

| Metrica | Valore |
|---|---|
| **Test case totali previsti (TCS)** | _6_ (3 unit + 3 system) |
| **Test case eseguiti** | _6_ |
| **Test case non eseguiti** | _0_ |
| **Test frame totali eseguiti** | _39_ |
| **Test passati** | _36_ |
| **Test falliti (alla prima esecuzione)** | _3_ |
| **Test falliti (dopo le correzioni)** | _0_ |
| **Percentuale di successo finale** | _100%_ |
| **Ore totali di test** | _12h_ |

> ⚠️ **I test "falliti" alla prima esecuzione sono una buona notizia**, se poi
> sono stati corretti e ricontrollati. Un TSR con 0 fallimenti iniziali *e* 0
> incidenti significa che i test non hanno mai provato a fallire.

---

## 3. Risultati per test case

| Test case | Tipo | Autore | Frame eseguiti | Esiti positivi | Incidenti | Stato |
|---|---|---|---|---|---|---|
| UT-01 | unit | _Cognome1_ | 7 | 7/7 | _INC-01_ | ✅ |
| UT-02 | unit | _Cognome2_ | 7 | 7/7 | — | ✅ |
| UT-03 | unit | _Cognome3_ | 7 | 7/7 | _INC-03_ | ✅ |
| ST-01 | system | _Cognome1_ | 6 | 6/6 | _INC-02_ | ✅ |
| ST-02 | system | _Cognome2_ | 6 | 6/6 | — | ✅ |
| ST-03 | system | _Cognome3_ | 6 | 6/6 | — | ✅ |

---

## 4. Copertura del codice

> Da generare con JaCoCo: `mvn test jacoco:report` → report in
> `6_codice/target/site/jacoco/index.html`. Allegare l'HTML.

| Classe | Istruzioni coperte | Branch coperti | Note |
|---|---|---|---|
| `_Validatore_` | _92%_ | _88%_ | _classe critica_ |
| `_ServiceUtenti_` | _85%_ | _76%_ | |
| `_Controller_` | _71%_ | _60%_ | _sotto la soglia, da migliorare_ |

| Metrica | Valore | Soglia TP §4 | Esito |
|---|---|---|---|
| **Copertura istruzioni** | _84%_ | ≥ 70% | ✅ |
| **Copertura branch** | _72%_ | ≥ 70% | ✅ |
| **Copertura metodi** | _88%_ | ≥ 80% | ✅ |
| **Copertura righe** | _84%_ | ≥ 70% | ✅ |

**Classi con copertura 0%:** _nessuna_

> ⚠️ Se ci sono classi a 0%, il criterio di uscita del TP non è soddisfatto.
> Una classe scritta e mai testata è un difetto, non un dettaglio.

---

## 5. Copertura dei requisiti

| Tipo | Requisiti totali | Coperti da test | % |
|---|---|---|---|
| Funzionali | _6-12_ | _..._ | _100%_ |
| Non funzionali | _6-12_ | _..._ | _100%_ |

Dettaglio nella Matrice di Tracciabilità (`4_Matrice_Tracciabilita/`).

> I RNF che non sono verificabili automaticamente (usabilità, legali) si dichiarano
> verificati **per ispezione**, dichiarando chi e con quale criterio.

---

## 6. Incidenti

| Metrica | Valore |
|---|---|
| Incidenti rilevati | _3_ |
| Incidenti risolti | _3_ |
| Incidenti aperti alla consegna | _0_ |
| Bloccanti aperti | _0_ |
| Critici aperti | _0_ |

Riferimento completo: `IS3_TIRT_ver.1.0`.

---

## 7. Valutazione dei criteri di uscita

> Copia i criteri dal TP §4 e verifica **uno per uno**.

| Criterio (TP §4) | Soglia | Valore | Esito |
|---|---|---|---|
| Test case eseguiti | 100% | _6/6_ | ✅ |
| Test passati | ≥ 90% | _100%_ | ✅ |
| Difetti Bloccanti/Critici aperti | 0 | _0_ | ✅ |
| Copertura del codice | ≥ 70% | _84%_ | ✅ |
| TSR compilato | sì | sì | ✅ |

**Esito complessivo del testing:** ✅ **COMPLETATO**

---

## 8. Conclusioni e valutazione

> Sezione più importante per la discussione. **Tre domande:**

**8.1 Il sistema è pronto per la consegna?**

_Sì / No, motivando con i dati del documento._ _TBD_

**8.2 I difetti residui sono accettabili?**

_Gli incidenti rimasti sono … e il loro impatto sui requisiti è …_ _TBD_

**8.3 Cosa è stato imparato?**

<!-- Il docente chiede la riflessione. Qualcosa di specifico, non generico:
     es. "la specifica dei confini delle classi di equivalenza nei metodi di
     validazione ha eliminato 2 dei 3 incidenti" — un fatto, non una frase. -->

_TBD_

---

## 9. Sforzo e risorse

| Attività | Ore stimate | Ore effettive | Persona |
|---|---|---|---|
| Progettazione unit test CP | 6h | _7h_ | _3 membri_ |
| Progettazione system test CP | 9h | _10h_ | _3 membri_ |
| Esecuzione | 4h | _4h_ | _tutti_ |
| Gestione incidenti | 3h | _5h_ | _chi gira i test_ |
| Stesura TSR | 2h | _2h_ | _Cognome?_ |
| **Totale** | **24h** | **_28h_** | |

---

## 10. Allegati

| Allegato | Contenuto |
|---|---|
| `jacoco/index.html` | report di copertura |
| `surefire-reports/` | output JUnit dettagliato per test |
| `IS3_TIRT_ver.1.0` | registro incidenti |
| Screenshot test manuali | _..._ |