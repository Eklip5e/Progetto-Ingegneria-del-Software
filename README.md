# Progetto `IS3` — Ingegneria del Software, A.A. 2026/2027

> Repository del progetto di Ingegneria del Software.
> Documentazione del progetto: cartella `Tasca/` (fuori da questo repository o
> dentro, secondo la scelta fatta nel SoW).

## Struttura del repository

```
Tasca/
├── INDICE.md                    ← cosa va dove: LEGGI PRIMA
├── PROPOSTE_PROGETTO.md         ← scelta del progetto
├── PIANO_LAVORO.md              ← milestone e ripartizione dei 3 membri
├── 0_amministrazione/           ← SoW, verbali, export Trello e Slack
├── 1_RAD/                       ← Requirements Analysis Document + diagrammi
├── 2_SDD/                       ← System Design Document + diagrammi
├── 3_ODD/                       ← i 2 design pattern
├── 4_Matrice_Tracciabilita/     ← requisiti ↔ design ↔ test
├── 5_testing/                   ← TP, TCS, TIR, TIRT, TSR
├── 6_codice/                    ← questo progetto Maven
└── .github/workflows/           ← CI
```

## Regole di contribution

Queste regole sono l'attuazione del criterio di accettazione "adeguato utilizzo
del pull-based development".

1. **Mai push diretti su `main`.** Tutto passa da un branch di feature.
2. **Un branch per problema:** `feature/validazione-registrazione`,
   `fix/data-paginazione`, `docs/rad-requisiti`.
3. **Pull request sempre con almeno una review** di un altro membro del team.
4. **La CI deve essere verde** prima del merge. Il branch protection lo impone.
5. **Nessun file `target/`, `.class`, `.db` o `.log` nel repository** (c'è già
   `.gitignore`).
6. **Il `pom.xml` non si tocca** per far passare un test: si sistema il test.

### Flusso di lavoro

```
git checkout -b feature/nome-del-coso
# ... scrivi codice e test ...
git commit -m "Descrizione breve di cosa cambia e perché"
git push -u origin feature/nome-del-coso
# -> apri la Pull Request su GitHub, tagga un collega per la review
# -> la CI gira, deve essere verde
# -> merge dopo la review
```

## Build e test

Prerequisiti: **JDK 17** e **Maven 3.9+**.

```bash
# Compila
mvn clean compile

# Esegue tutti i test
mvn test

# Test + verifica della soglia di copertura (quello che gira in CI)
mvn verify

# Genera il report HTML di copertura
mvn test jacoco:report
# -> target/site/jacoco/index.html
```

Il report di copertura è un **deliverable**: va allegato al TSR (`5_testing/`).

## Stack

| Componente | Scelta |
|---|---|
| Linguaggio | Java 17 |
| Build | Maven |
| Test | JUnit 5 |
| Mock | Mockito |
| Copertura | JaCoCo |
| CI | GitHub Actions |
| Persistenza | _(da definire — vedi SDD §3.4)_ |

> ⚠️ **Rinominare il package radice.** Da `it.unisa.is3` a `it.unisa.<sigla>`,
> coerentemente nel `pom.xml` e in tutti i sorgenti. Non lasciare package
> placeholder in un repository pubblico.

## Documenti

| Documento | Cartella |
|---|---|
| Statement of Work | `0_amministrazione/SoW/` |
| RAD | `1_RAD/` |
| SDD | `2_SDD/` |
| ODD (cenni) | `3_ODD/` |
| Matrice di tracciabilità | `4_Matrice_Tracciabilita/` |
| Test Plan, TCS, TIR, TIRT, TSR | `5_testing/` |

## Membri del team

| Nome | GitHub | Ruolo |
|---|---|---|
| _Cognome Nome_ | _@handle_ | _..._ |
| _Cognome Nome_ | _@handle_ | _..._ |
| _Cognome Nome_ | _@handle_ | _..._ |

## Licenza

_(da scegliere — MIT, Apache-2.0, o altra)_

## Note

- Questo progetto è stato sviluppato per l'esame di Ingegneria del Software,
  A.A. 2026/2027, Università degli Studi di Salerno.
- Il progetto BiblioNet presente nella cartella madre è **materiale di
  riferimento** del corso e non è parte di questo lavoro.