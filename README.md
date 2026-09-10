# Quadretti

Lavagna a quadretti per scrivere a mano nel browser. Quando una riga finisce con `=`,
il testo viene riconosciuto e il risultato compare in rosso subito dopo l'uguale.
Se il risultato l'hai già scritto tu, viene controllato: ✓ se torna, altrimenti il valore giusto.

**Online:** https://aledallas01.github.io/quadretti/

## Come funziona

Tutto gira nel browser, senza server e senza servizi esterni:

- i tratti vengono raggruppati in righe e simboli in base alle scatole di contenimento;
- ogni simbolo viene rasterizzato, assottigliato (Zhang-Suen) e confrontato con modelli
  generati a runtime dai font disponibili;
- `=`, `+`, `-`, `×`, `÷`, `1` e il punto sono riconosciuti prima per geometria;
- l'espressione viene valutata con un parser shunting-yard: `+ - × ÷ ^ ( ) % !`,
  `sqrt`, `sin/cos/tan` (gradi), `ln`, `log`, `pi`, virgola decimale italiana.

## Strumenti

Penna, evidenziatore, gomma, sei colori, tre spessori, annulla/rifai, esportazione PNG.
La lavagna si salva da sola nel browser (localStorage).

Scorciatoie: `P` penna · `H` evidenziatore · `G` gomma · `Ctrl+Z` annulla · `Ctrl+Invio` risolvi.

## Sviluppo

È un unico file statico: `index.html`. Per provarlo in locale basta un server statico,
per esempio `python -m http.server`.
