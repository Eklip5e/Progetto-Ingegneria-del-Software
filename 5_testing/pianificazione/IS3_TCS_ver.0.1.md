# TCS — Test Case Specification — Progetto `IS3`

> **Scheletro 0.1 — da compilare.**
>
> Il TCS contiene i **casi di test** con i risultati attesi.
>
> **VINCOLI:**
> - Ogni **studente** fa **esattamente 1 test di unità** (un metodo di una classe
>   sviluppata) con category partition → **3 test di unità**.
> - Ogni **studente** fa **esattamente 1 test di sistema** (una funzionalità) con
>   category partition → **3 test di sistema**.
>
> **Le tabelle di category partition sono il deliverable più richiesto dal docente.
> Devono essere complete: ogni categoria, ogni scelta, ogni classe limite.**

| Test Case Specification | `IS3` | |
|---|---|---|
| **Versione** | 0.1 | |
| **Data** | _gg/mm/aaaa_ | |
| **Autori** | _tutti_ | |
| **TP di riferimento** | `IS3_TP_ver._1.0` | |
| **RAD di riferimento** | `IS3_RAD_ver._1.0` | |

---

## Revision History

| Data | Versione | Descrizione | Autori |
|---|---|---|---|
| _gg/mm_ | 0.1 | Prima stesura | _tutti_ |

---

## Parte A — Test di unità (3, uno per studente)

> Un metodo di una classe **sviluppata da voi**. Ogni studente ne fa uno diverso.

## A.1 — UT-01: metodo `_nomeMetodo_` della classe `_NomeClasse`

**Autore:** _Cognome1_ · **Classe:** `it.unisa.is3._pkg_._NomeClasse` · **File:** `...java`

### Specifica del metodo

| | |
|---|---|
| **Firma** | `_public tipo nomeMetodo(tipo p1, tipo p2)_` |
| **Precondizione** | _cosa deve essere vero prima_ |
| **Postcondizione** | _cosa deve essere vero dopo il ritorno normale_ |
| **Effetti collaterali** | _cosa modifica: campi, file, DB_ |
| **Requisito tracciato** | _RF-0?_ |
| **Use case** | _UC-0?_ |

### Analisi dei parametri

> **Questo è il cuore del deliverable.** Per OGNI parametro, definisci le partizioni
> (classi di equivalenza) e le classi limite.

| Parametro | Tipo | Dominio | Partizioni | Classi limite | Valori scelti |
|---|---|---|---|---|---|
| `p1` | `String` | _es. nome utente_ | P11: nome valido · P12: nome vuoto · P13: nome con solo spazi · P14: nome > 20 char · P15: nome con caratteri non ammessi | _19, 20, 21 char_ | _"Mario", "", "   ", "A".repeat(21), "M4r!o"_ |
| `p2` | `int` | _es. età_ | P21: 0-17 · P22: 18-120 · P23: < 0 · P24: > 120 | _17, 18, 120, 121_ | _15, 30, -1, 500_ |

### Combinazioni e test frame

| Test frame | Combinazione | Input | Risultato atteso | Esito |
|---|---|---|---|---|
| TF-01 | _partitioni valide_ | _(p1="Mario", p2=30)_ | _nessun errore, oggetto creato_ | _Pass_ |
| TF-02 | _p1 non valida_ | _(p1="", p2=30)_ | _IllegalArgumentException("nome obbligatorio")_ | _Pass_ |
| TF-03 | _p2 non valida_ | _(p1="Mario", p2=500)_ | _IllegalArgumentException("età non valida")_ | _Pass_ |
| TF-04 | _entrambe non valide_ | _(p1="   ", p2=-1)_ | _eccezione: si valida prima p1_ | _Pass_ |
| TF-05 | _limite inferiore_ | _(p1="A".repeat(19), p2=17)_ | _accettato_ | _Pass_ |
| TF-06 | _limite superiore_ | _(p1="A".repeat(20), p2=120)_ | _accettato_ | _Pass_ |
| TF-07 | _oltre limite_ | _(p1="A".repeat(21), p2=121)_ | _rifiutato_ | _Pass_ |

> ⚠️ **Non fermarti al test "tutti i parametri validi".** Il caso interessante è
> quello in cui un singolo parametro è invalido: è lì che nasce il difetto.
> Includi sempre: ogni partizione da sola, i valori limite, e le combinazioni "a rischio".

### Test di confine

| ID | Confine | Atteso |
|---|---|---|
| BC-01 | _lunghezza nome = 20 (limite superiore valido)_ | _accettato_ |
| BC-02 | _lunghezza nome = 21 (oltre)_ | _rifiutato_ |

### Codice del test (JUnit 5)

```java
@Test
@DisplayName("TF-01 - nome ed età validi: crea l'utente")
void creaUtente_Validi_Ok() {
    // given
    String nome = "Mario";
    int eta = 30;
    // when
    Utente u = gestore.creaUtente(nome, eta);
    // then
    assertAll(
        () -> assertNotNull(u),
        () -> assertEquals("Mario", u.getNome()),
        () -> assertEquals(30, u.getEta())
    );
}

@Test
@DisplayName("TF-02 - nome vuoto: rifiutato")
void creaUtente_NomeVuoto_Exception() {
    assertThrows(IllegalArgumentException.class, () -> gestore.creaUtente("", 30));
}
```

---

## A.2 — UT-02: metodo `_nomeMetodo_` della classe `_NomeClasse`

_(Autore: _Cognome2_ — stessa struttura di A.1, su un metodo e una classe diversi)_

## A.3 — UT-03: metodo `_nomeMetodo_` della classe `_NomeClasse`

_(Autore: _Cognome3_ — stessa struttura di A.1)_

---

## Parte B — Test di sistema (3, uno per studente)

> Una **funzionalità** del sistema, vista dall'esterno come utente.
> Qui il category partition si fa sui **dati di input della funzionalità**, non sui
> parametri di un singolo metodo.

## B.1 — ST-01: funzionalità `_nomeFunzionalita_`

**Autore:** _Cognome1_ · **Use case:** _UC-01_ · **Requisito:** _RF-01, RF-02_

**Precondizioni:** _es. utente non registrato nel sistema_

### Partizioni dei dati di input

| Dato | Partizioni | Classi limite | Valori rappresentativi |
|---|---|---|---|
| _email_ | B1: formato valido · B2: senza @ · B3: dominio inesistente · B4: già registrata | _@, ._ | _"a@b.it", "ab.it", "a@b", "a@b.it"_ |
| _password_ | C1: 8+ char · C2: < 8 char · C3: senza maiuscola · C4: senza numero | _7, 8 char_ | _"Password1", "Pass1", "password1", "PASSWORD1"_ |

### Combinazioni e test frame

| Test frame | Input | Passi | Risultato atteso | Esito |
|---|---|---|---|---|
| STF-01 | _(email valida, password valida)_ | _1. apri registrazione 2. inserisci 3. conferma_ | _utente creato, messaggio di conferma_ | _Pass_ |
| STF-02 | _(email senza @)_ | _stessi passi_ | _errore "email non valida", nessun utente creato_ | _Pass_ |
| STF-03 | _(email già registrata)_ | _stessi passi_ | _errore "email già in uso", nessun duplicato_ | _Pass_ |
| STF-04 | _(password troppo corta)_ | _stessi passi_ | _errore "password min 8 caratteri"_ | _Pass_ |
| STF-05 | _(email valida, password < 8)_ | _stessi passi_ | _errore sulla password_ | _Pass_ |
| STF-06 | _(entrambi non validi)_ | _stessi passi_ | _errore: entrambi i messaggi_ | _Pass_ |

**Casi limite:** _es. password di esattamente 8 caratteri (accettata), 7 (rifiutata)_

---

## B.2 — ST-02: funzionalità `_nomeFunzionalita_`

_(Autore: _Cognome2_, use case _UC-02_)_

## B.3 — ST-03: funzionalità `_nomeFunzionalita_`

_(Autore: _Cognome3_, use case _UC-03_)_

---

## Parte C — Riepilogo

| ID | Tipo | Oggetto | Autore | N° frame | Esiti positivi |
|---|---|---|---|---|---|
| UT-01 | unit | `_Classe.metodo_` | _Cognome1_ | _7_ | _7/7_ |
| UT-02 | unit | `_Classe.metodo_` | _Cognome2_ | _7_ | _7/7_ |
| UT-03 | unit | `_Classe.metodo_` | _Cognome3_ | _7_ | _7/7_ |
| ST-01 | system | _funzionalità_ | _Cognome1_ | _6_ | _6/6_ |
| ST-02 | system | _funzionalità_ | _Cognome2_ | _6_ | _6/6_ |
| ST-03 | system | _funzionalità_ | _Cognome3_ | _6_ | _6/6_ |

**Totale: 6 test case** (3 unit + 3 system) — come richiesto dal SOW.

---

## Appendice — Tracciabilità dei test

| Test frame | Requisito | Scenario | Esito | Defect ID |
|---|---|---|---|---|
| _TF-01_ | _RF-01_ | _SC-01_ | _Pass_ | — |
| _STF-03_ | _RF-01_ | _SC-02_ | _Fail→Fix_ | _INC-01_ |