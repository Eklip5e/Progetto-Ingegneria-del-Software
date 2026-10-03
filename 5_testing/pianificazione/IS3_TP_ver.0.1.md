# TP — Test Plan — Progetto `IS3`

> **Scheletro 0.1 — da compilare.**
>
> Il TP **non** contiene i test: contiene la **strategia** di test.
> I test stanno nel TCS. La confusione tra i due documenti è l'errore più comune.

| Test Plan | `IS3` | |
|---|---|---|
| **Versione** | 0.1 | |
| **Data** | _gg/mm/aaaa_ | |
| **Autori** | _tutti_ | |
| **Riferimento** | `IS3_TCS_ver._1.0`, `IS3_RAD_ver._1.0` | |

---

## Revision History

| Data | Versione | Descrizione | Autori |
|---|---|---|---|
| _gg/mm_ | 0.1 | Prima stesura | _tutti_ |

---

## 1. Scopo del Test Plan

_2 paragrafi. Quali artefatti del progetto sono soggetti a test e con quale
profondità. Cosa NON è in scope._

**In scope:** funzionalità descritte dai 3 use case · metodi delle classi sviluppate
**Out of scope:** _es. test di usabilità con utenti reali, test di carico su scala_

---

## 2. Strategia di test

### 2.1 Livelli di test

| Livello | Oggetto | Tecnica | Strumento | Chi |
|---|---|---|---|---|
| **Unit test** | 1 metodo di una classe per studente (3 totali) | **black-box, category partition** | JUnit 5 + Mockito | _Cognome1/2/3_ |
| **Integration test** | _es. Control ↔ Entity_ | _white-box_ | JUnit 5 | _..._ |
| **System test** | 1 funzionalità per studente (3 totali) | **black-box, category partition** | JUnit 5 / test manuali | _Cognome1/2/3_ |
| **Acceptance test** | _es. le 9 sezioni RNF_ | _ispezione_ | _manuale_ | _tutti_ |

### 2.2 Perché category partition

<!-- Il docente la richiede esplicitamente: spiega il razionale, non solo il metodo. -->

_Giustificazione:_ la tecnica richiesta dal SOW è la **category partition** (partizionamento
in classi di equivalenza): si identificano le **partizioni** (classi di input
equivalenti) e si sceglie un rappresentante per ciascuna, includendo le **classi
di confine**. È scelta perché i nostri metodi hanno parametri con domini
discreti e continui ben separati, e perché produce il numero minimo di casi
con copertura massima delle classi.

**Classi limite:** sono i valori ai **confini** di ogni partizione, non i valori
estremi assoluti. Sono la fonte principale dei difetti (off-by-one).

---

## 3. Ambiente di test

| Componente | Specifica |
|---|---|
| **SO** | _es. Windows 11 / Ubuntu 22.04_ |
| **JVM** | _OpenJDK 17_ |
| **Build** | _Maven 3.9_ |
| **Framework** | _JUnit 5.10_ |
| **Mock** | _Mockito 5_ |
| **Coverage** | _JaCoCo_ |
| **CI** | _GitHub Actions su ogni push/PR_ |
| **DB** | _es. SQLite in-memory per i test_ |

> **I test devono girare da riga di comando** (`mvn test`) senza setup manuale.
> Se richiedono un database avviato a mano, in CI falliranno.

---

## 4. Criteri di entry e di uscita

**Entry** (quando si può iniziare a testare):
- [ ] Il codice è compilato (`mvn clean package` senza errori)
- [ ] Il RAD è alla versione stabile e i requisiti sono approvati
- [ ] I test case del TCS sono scritti

**Exit** (quando il testing si considera concluso):
- [ ] **100%** dei test case del TCS eseguiti
- [ ] **≥ 90%** di test passati
- [ ] Nessun difetto con severità **Bloccante** o **Critico** aperto
- [ ] **Coverage ≥ 70%** sulle classi di dominio (verificato con JaCoCo)
- [ ] TSR compilato con i risultati

> Se i criteri di uscita non sono soddisfatti, il testing **non è finito**:
> il TSR deve riportare la percentuale reale, non quella desiderata.

---

## 5. Criteri di graduazione dei difetti

| Severità | Definizione | Tempo di risoluzione | Esempio |
|---|---|---|---|
| **Bloccante** | Il sistema non parte / si blocca | immediato | _crash all'avvio_ |
| **Critico** | Funzionalità principale assente o errata | prima della consegna | _login non funziona_ |
| **Maggiore** | Funzionalità presente ma errata in un caso specifico | prima della consegna | _email duplicata non gestita_ |
| **Minore** | Funzionalità corretta con difetto di forma | se tempo | _messaggio non tradotto_ |

---

## 6. Deliverable del testing

| Documento | Quando | Contenuto |
|---|---|---|
| **TP** (questo) | prima dei test | strategia |
| **TCS** | prima dei test | casi di test con expected result |
| **TIR** | durante | un report per sessione di test |
| **TIRT** | durante e alla fine | registro cumulativo degli incidenti |
| **TSR** | **alla fine** | sintesi: quanti test, copertura, esito |

> ⚠️ **Il TSR si scrive per ultimo** e riassume i TIR. Se lo scrivi prima, è falso.
> Il TIRT (tracker) è il **registro cumulativo**: ogni riga è un incidente, con
> ID, data, severità, stato, autore.

---

## 7. Risorse e responsabilità

| Attività | Responsabile | Stima |
|---|---|---|
| Progettazione dei 3 unit test CP | _Cognome1/2/3_ (1 ciascuno) | _2h ciascuno_ |
| Progettazione dei 3 system test CP | _Cognome1/2/3_ (1 ciascuno) | _3h ciascuno_ |
| Esecuzione dei test | _tutti_ | _4h_ |
| Gestione incidenti | _chi gira i test_ | _3h_ |
| Stesura TSR | _Cognome?_ | _2h_ |

---

## 8. Rischi del processo di test

| # | Rischio | Prob. | Impatto | Mitigazione |
|---|---|---|---|---|
| 1 | _copertura insufficiente_ | M | A | _JaCoCo in CI segnala il calo_ |
| 2 | _test flaky (dipende dall'ordine)_ | M | M | _isolare lo stato, no test paralleli su DB condiviso_ |
| 3 | _scadenza 6 gennaio troppo stretta_ | M | A | _test incrementali, non tutto alla fine_ |

---

## 9. Glossario

| Termine | Definizione |
|---|---|
| _Category partition_ | _tecnica black-box che suddivide il dominio di input in partizioni_ |
| _Copertura_ | _misura di quanto il codice è eseguito dai test_ |
| _Caso di test_ | _un insieme di input e il risultato atteso_ |