# Piano di lavoro — Progetto `IS3`

> Documento di lavoro interno al team.
> Il formato delle date è `gg/mm/aaaa`; gli orari sono quelli della piattaforma.
>
> **Le date contrassegnate con ⚠️ vanno confermate col docente:** la piattaforma
> Moodle mostra dati internamente incoerenti (si veda `../INDICE.md` §1 e §3).

---

## 1. Il calendario, in una tabella

| Data | Milestone | Deliverable | Note |
|---|---|---|---|
| **subito** | Scelta del progetto | — | `PROPOSTE_PROGETTO.md` |
| **subito** | Setup repository, Trello, Slack | — | vedi §3 |
| **10 ott 2026** ⚠️ | **Consegna SoW** | `IS3_SOW_ver.1.0` | prima scadenza, obbligatoria |
| 11–31 ott 2026 | Analisi e specifica | `IS3_RAD_ver.1.0` | the bulk of the work |
| 1–10 nov 2026 | Progettazione | `IS3_SDD_ver.1.0` | |
| 11–20 dic 2026 | **Consegna intermedia (opzionale)** | RAD+SDD in **un solo file** | ⚠️ data senza anno sulla piattaforma |
| 21 dic – 2 gen 2027 | Implementazione + test | `IS3_TCS`, `IS3_TIR/TIRT` | |
| **3–5 gen 2027** | Stesura TSR e check-list | `IS3_TSR_ver.1.0` | compilare le CL! |
| **6 gen 2027, 23:59** ⚠️ | **Consegna finale** | **tutti, in un solo file** | |
| **7 gen 2027** ⚠️ | **Discussione** | — | prenotare lo slot |

> ⚠️ **La consegna intermedia del 20 dicembre è opzionale ma va fatta.**
> Chi consegna in tempo riceve i commenti del docente e può migliorare la
> documentazione. È l'unico riscontro strutturato che avete prima della valutazione:
>|reportatelo come costo, ma è un vantaggio netto.

---

## 2. Ripartizione dei 3 membri

> Il principio: **i vincoli quantitativi sono per membro**, quindi ogni membro deve
> avere un **use case di proprietà**, uno **statechart o sequence diagram**, e
> **un test di unità + un test di sistema**. Nessuno può essere "solo quello che
>-programma".

| Attività | Membro 1 | Membro 2 | Membro 3 |
|---|---|---|---|
| **Use case di proprietà (1 ciascuno)** | UC-01 | UC-02 | UC-03 |
| **Scenari (2-4 ciascuno)** | SC-01, SC-02 | SC-03, SC-04 | SC-05, SC-06 |
| **Requisiti funzionali (2-4 ciascuno)** | RF-01…RF-04 | RF-05…RF-08 | RF-09…RF-12 |
| **Requisiti non funzionali (2-4 ciascuno)** | RNF-01…RNF-04 | RNF-05…RNF-08 | RNF-09, RNF-12 |
| **Sequence diagram (2 totali)** | AD-01 con il 2 | AD-02 con il 3 | ← vedi nota |
| **Statechart (2 totali)** | STC-01 | STC-02 con il 3 | ← vedi nota |
| **Activity diagram (1)** | ADM-01 (coordinato) | | |
| **Class diagram (1)** | CDM-01 (coordinato) | | |
| **Design goal (2-4 ciascuno)** | DG-01…DG-04 | DG-05…DG-08 | DG-09…DG-12 |
| **Unit test CP (1 ciascuno)** | UT-01 | UT-02 | UT-03 |
| **System test CP (1 ciascuno)** | ST-01 | ST-02 | ST-03 |
| **Design pattern (2 totali)** | PAT-01 (leader) | PAT-02 (leader) | review |
| **Deployment diagram** | DEPL-01 (coordinato) | | |
| **Decomposizione sottosistemi** | SUB-01 (coordinato) | | |

> **I 2 sequence diagram e i 2 statechart si dividono a coppie**, perché il vincolo
> è "1 ogni 2 membri" e i membri sono 3 (3/2 = 1,5 → 2 diagrammi).
> Una divisione naturale: **M1+M2 fanno il primo, M3 il secondo.** Decidetela
> nella prima riunione e scrivetela nel RAD.

### Chi fa cosa, in pratica

| Membro | Ruolo suggerito | Perché |
|---|---|---|
| **M1** | ** RAD e specifica** | Il RAD è il deliverable più pesante e va tenuto coerente; chi lo scrive deve poter rispondere a ogni domanda in discussione |
| **M2** | **Design e codice** | SDD e implementazione sono collegati: chi progetta l'architettura deve scrivere il codice che la realizza |
| **M3** | **Testing e qualità** | I 6 test CP sono il vincolo più distribuito; chi li coordina garantisce che siano fatti e siano confrontabili |

> Nessuno fa solo un ruolo: ognuno ha il suo use case, i suoi requisiti, i suoi
> diagrammi e i suoi test. I ruoli servono a non disperdere il lavoro, non a
> creare compartimenti.

---

## 3. Setup dei tool (da fare nella prima settimana)

> I 4 tool sono **criteri di accettazione**. Se non sono configurati e usati
> *durante* il progetto, il progetto è bocciato indipendentemente dalla qualità.

### GitHub

- [ ] Creare l'organizzazione (o il repository) `is3-<sigla>`
- [ ] Repository **privato** (il progetto non deve essere pubblico: è materiale d'esame)
- [ ] `git init` in `6_codice/` + primo commit
- [ ] Branch `main` protetta: **CI verde richiesta** prima del merge
- [ ] **Branch policy:** nessun merge diretto su `main`, sempre via PR
- [ ] Attivare i template di issue e di pull request
- [ ] Impostare la CI: il file è già in `.github/workflows/maven.yml`

**Configurazione Git consigliata** (ciascuno la fa sulla sua macchina):

```bash
git config --global user.name "Cognome Nome"
git config --global user.email "nome.cognome@studenti.unisa.it"
git config --global pull.rebase true
```

### Trello

- [ ] Board `Progetto IS3`
- [ ] 4 liste: **Backlog · In corso · In review · Done**
- [ ] Una card per ogni **use case**, con la checklist dei deliverable che produce
- [ ] Label per membro (`@m1`, `@m2`, `@m3`) e per artefatto (`#rad`, `#sdd`, `#test`)
- [ ] **Export del board a fine ogni sprint** → `0_amministrazione/Gestione_task/`
- [ ] Stabilire la **durata dello sprint**: 1 settimana è il minimo per vedere l'avanzamento

### Slack

- [ ] Workspace del gruppo, canale `#is3-progetto`
- [ ] Canali per area: `#rad`, `#design`, `#test` (o un canale solo con thread)
- [ ] **Regola del project's charter:** ogni decisione tecnica si prende in Slack
      e si **collega** alla card Trello
- [ ] **Export dei canali** a fine progetto → `0_amministrazione/Comunicazioni/`
- [ ] Non usare canali privati: la tracciabilità dev'essere ispezionabile

### Riunioni

- [ ] **Frequenza:** settimanale, 1 ora, data fissa
- [ ] Un verbale in `0_amministrazione/Riunioni/` dopo ogni riunione:
      data, presenti, decisioni, task assegnati, link ai branch
- [ ] Tra una riunione e l'altra: **nessun giorno senza commit** da nessun membro

---

## 4. Sprint di lavoro

| Sprint | Periodo | Obiettivo | Esito verificabile |
|---|---|---|---|
| **S-0** | questa settimana | scelta progetto, setup tool, prima stesura SoW | repo su GitHub, board Trello aperto, Slack attivo |
| **S-1** | 1–8 ott | SoW completo e revisionato | `IS3_SOW_ver.1.0` |
| **S-2** | 9–15 ott | RAD §1-§2 (introduzione, sistema attuale) | RAD parziale + CL compilata a metà |
| **S-3** | 16–22 ott | requisiti RF e RNF + scenari | 6-12 RF, 6-12 RNF, 6-12 SC |
| **S-4** | 23–29 ott | diagrammi RAD (UC, activity, class) | **3 UC**, **1 activity**, **1 class** |
| **S-5** | 30 ott – 5 nov | sequence e statechart | **2 sequence**, **2 statechart** |
| **S-6** | 6–12 nov | SDD: design goal, trade-off, architettura | SDD §1-§3.2 |
| **S-7** | 13–19 nov | SDD: persistenza, accessi, condizioni limite | SDD completo |
| **S-8** | 20–26 nov | ODD + 2 design pattern | `IS3_ODD_ver.1.0` |
| **S-9** | 27 nov – 3 dic | implementazione + primi test | codice che gira, CI verde |
| **S-10** | 4–10 dic | category partition test (6 test) | 6 TCS + tabelle CP |
| **S-11** | 11–20 dic | **consegna intermedia** | RAD+SDD in un file |
| **S-12** | 21 dic – 2 gen | integrazione commenti docente, colmare le lacune | documentazione aggiornata |
| **S-13** | 3–5 gen | TIR/TIRT/TSR + check-list finali | TSR + CL compilate |
| **S-14** | 6 gen | **consegna finale** | tutti i file, un solo documento |

> ⚠️ **Il margine è quasi zero.** I primi 3 sprint (S-2, S-3, S-4) sono quelli che
> il corso ha ridimensionato di meno: lì il margine è ampio. Usatelo per
> costruire un buffer, non per iniziare a scrivere il codice.

---

## 5. Definizione di "fatto"

> Per non avere discussioni in fase di review, ogni task ha questi criteri.

### Un deliverable di documentazione è "fatto" quando

- [ ] ha la **struttura** corretta (corrisponde alla gerarchia del check-list)
- [ ] tutte le sezioni hanno **contenuto**, nessuna è un placeholder
- [ ] i **numeri** sono rispettati (3 UC, 2 sequence, 2 statechart, 6-12 requisiti, 6-12 scenari)
- [ ] il **glossario** contiene tutti i termini nuovi
- [ ] la **revision history** è aggiornata
- [ ] i **diagrammi** hanno un sorgente modificabile, non solo un PNG
- [ ] i **riferimenti** indicano documento, versione e data
- [ ] nessun errore di formattazione (doppi spazi, spazi prima di punteggiatura)
- [ ] è stato **compilato da un altro membro** (code review della documentazione)

### Un task di codice è "fatto" quando

- [ ] è su un **branch**, non su `main`
- [ ] c'è un **test** che fallirebbe senza la modifica
- [ ] `mvn verify` passa **in locale**
- [ ] la **CI è verde** (non solo verde in locale)
- [ ] la **pull request** ha una **review** approvata
- [ ] il branch è stato **mergeato** in `main`
- [ ] la card Trello è spostata in **Done** con il link alla PR

> ⚠️ **Una pull request senza test non viene approvata.** È il criterio di code
> review, che è anche uno dei premi. La regola vale per voi quanto per il codice
> del progetto: se la documentazione non è revisionata, non si corregge.

---

## 6. Checklist di rischio, da rivedere a ogni riunione

| # | Rischio | Segnale precoce | Azione |
|---|---|---|---|
| 1 | Scope creep (troppi use case) | il RAD ha >3 casi d'uso | fermarsi e scegliere i 3 |
| 2 | Documentazione scritta solo alla fine | nessun file in `1_RAD/` dopo S-3 | sprint bloccato, parlare col docente |
| 3 | Merge senza review | PR senza approvazione | attivare branch protection |
| 4 | Test mai eseguiti | `mvn test` non lanciato da settimane | CI obbligatoria |
| 5 | Nessun commit per giorni | attività Trello senza commit | stand-up quotidiano 15 min |
| 6 | Diagrammi prodotti solo come PNG | nessun sorgente | il docente non può verificarli |
| 7 | Pattern forzati | "abbiamo messo Observer perché lo richiedeva" | scegliere pattern motivati (§`PROPOSTE_PROGETTO.md`) |
| 8 | Scadenza intermedia saltata | nessuna consegna il 20 dic | consegnare comunque: è una rete di sicurezza |

---

## 7. Le prime 5 azioni, in ordine

1. **Decidere il progetto** — leggete `PROPOSTE_PROGETTO.md` e scegliete.
   Se confermate il progetto esistente, fate prima l'audit della Parte 4.
2. **Rinominare `IS3`** nella sigla definitiva, ovunque (i nomi dei file contengono
   `IS3_`: cambiateli con ricerca e sostituzione).
3. **Rinominare il package** `it.unisa.is3` → `it.unisa.<sigla>` in `6_codice/`.
4. **Aprire repository GitHub, board Trello e canale Slack.** Fatelo oggi, non
   dopo il SoW: le tracce devono esserci dal primo giorno.
5. **Compilare il SoW** (`0_amministrazione/SoW/IS3_SOW_ver.0.1.md`) e farlo
   revisionare dai tre. È la scadenza più vicina e quella che definisce tutto il resto.