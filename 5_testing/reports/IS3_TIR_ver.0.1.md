# TIR — Test Incident Report — Progetto `IS3`

> **Scheletro 0.1 — da compilare.**
>
> Il **TIR** descrive **un incidente** (un difetto) in dettaglio.
> Se ne scrive **uno per difetto rilevato** (o uno per sessione, con appendici).
> Il **TIRT** è il registro cumulativo che li elenca tutti.
>
> ⚠️ Se durante i test **non trovate nessun difetto**, è improbabile che i test
> siano stati fatti bene. Un TSR con 30/30 passati e zero incidenti è una red flag.

| Test Incident Report | `IS3` | |
|---|---|---|
| **Incident ID** | _INC-00_ | |
| **Versione** | 0.1 | |
| **Data apertura** | _gg/mm/aaaa_ | |
| **Autore del report** | _Cognome_ | |
| **Stato** | _Aperto / In correzione / Risolto / Chiuso_ | |

---

## 1. Descrizione dell'incidente

| Campo | Contenuto |
|---|---|
| **ID** | _INC-00_ |
| **Titolo** | _es. "Password troppo corta accettata in registrazione"_ |
| **Severità** | _Bloccante / Critico / Maggiore / Minore_ (criteri nel TP §5) |
| **Priorità** | _Alta / Media / Bassa_ |
| **Tipo** | _funzionale / interfaccia / dati / performance / sicurezza_ |
| **Test case che l'ha rilevato** | _STF-04 (ST-01, B.1)_ |
| **Requisito coinvolto** | _RF-02_ |
| **Componente** | `_es. it.unisa.is3.pkg.Validatore_` |

---

## 2. Condizioni di riproduzione

<!-- Deve essere riproducibile da chiunque. Se servono undici passi, il test è scritto male. -->

**Precondizioni:**
1. _Il sistema è avviato_
2. _Non esiste alcun utente registrato_
3. _..._

**Passi per riprodurre:**

| # | Azione | Risultato atteso | Risultato attuale |
|---|---|---|---|
| 1 | _Apri la pagina di registrazione_ | _form mostrato_ | ✅ |
| 2 | _Inserisci email: a@b.it_ | _accettato_ | ✅ |
| 3 | _Inserisci password: `abc`_ (3 caratteri) | _**errore** "password minimo 8 caratteri"_ | ❌ **accettata** |
| 4 | _Clic su "Registrati"_ | _errore di validazione_ | ❌ **utente creato** |

**Risultato attuale:** _il sistema crea l'utente con password di 3 caratteri_
**Risultato atteso:** _rifiuto con messaggio di validazione_

---

## 3. Evidenza

<!-- Screenshot, log, stack trace. Incolla qui il messaggio di errore
     o la schermata. -->

```
_es. log_:
2026-12-28 14:22:01 ERROR Validatore - password "abc" accettata (len=3)
```

**Screenshot:** `allegati/INC-00_registrazione.png`

---

## 4. Analisi della causa

| | |
|---|---|
| **Componente** | `_Classe_Validatore_` |
| **Metodo** | `_validaPassword(String)_` |
| **Causa** | _la condizione verifica solo che non sia vuota, non la lunghezza minima_ |
| **Riga** | `_42_` |

```java
// codice attuale (difettoso)
if (password.isEmpty()) {
    throw new IllegalArgumentException("password obbligatoria");
}

// codice corretto
if (password.length() < MIN_PASSWORD_LENGTH) {   // MIN = 8
    throw new IllegalArgumentException("password minimo " + MIN_PASSWORD_LENGTH + " caratteri");
}
```

---

## 5. Risoluzione

| Campo | Contenuto |
|---|---|
| **Data correzione** | _gg/mm/aaaa_ |
| **Autore della correzione** | _Cognome_ |
| **Branch / PR** | `_feature/validazione-password_` (#12) |
| **Commit** | `_abc1234 - fix: lunghezza minima password_` |
| **Test di regressione** | _TC-04 aggiunto in TC-04-password-troppo-corta_ |
| **Stato** | ✅ Risolto e verificato |

> Il TIR si **chiude** solo quando c'è un test di regressione che fallirebbe senza
> la correzione. Una correzione non coperta da test è una correzione che regredisce.

---

## 6. Riferimenti

| Documento | Riferimento |
|---|---|
| TCS | _ST-01, test frame STF-04_ |
| TP | _severità secondo §5_ |
| Matrice di tracciabilità | _RF-02_ |
| TIRT | _riga INC-00_ |