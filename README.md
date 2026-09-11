# Quadretti

Lavagna a quadretti per scrivere a mano nel browser. Quando una riga finisce con `=`,
il testo viene riconosciuto e il risultato compare in rosso subito dopo l'uguale.
Se il risultato l'hai già scritto tu, viene controllato: ✓ se torna, altrimenti il valore giusto.

**Online:** https://aledallas01.github.io/quadretti/

## Cosa capisce

- **Conti in riga** — `12 + 7 =`, `80 - 9 =`, `9 × 8 =`
- **Variabili** — scrivi `x = 2` in un punto qualsiasi della lavagna e da lì in poi
  `x + 8 =` vale 10. Le definizioni valgono ovunque e possono dipendere l'una dall'altra.
  Una `x` scritta fra due numeri resta una moltiplicazione.
- **Frazioni impilate** — numeratore, riga e denominatore: `1/2 + 1/4 =` fa 0,75
- **Esponenti** — una cifra scritta in alto a destra diventa una potenza: `2³ =` fa 8, `x² =` funziona
- **Parentesi** — `(2 + 3) × 4 =` fa 20
- Più `^ % !`, `sqrt`, `sin/cos/tan` in gradi, `ln`, `log`, `pi`, virgola decimale italiana

La riga in basso mostra sempre **cosa ha letto**, così una svista del riconoscimento si vede subito.

## Come funziona

Tutto gira nel browser, senza server e senza servizi esterni:

- i tratti vengono raggruppati in righe di scrittura (vicinanza verticale *e* orizzontale,
  così due colonne affiancate non si mescolano) e poi in simboli;
- ogni simbolo viene rasterizzato, assottigliato (Zhang-Suen) e confrontato con modelli
  generati a runtime dai font disponibili; il conteggio degli anelli chiusi separa 0/6/8/9 da 3/5/2;
- `=`, `+`, `-`, `×`, `÷`, `1`, `(`, `)` e il punto sono riconosciuti prima per geometria;
- un passaggio di layout 2D ricostruisce frazioni ed esponenti dalla posizione dei simboli;
- l'espressione viene valutata con un parser shunting-yard, con le variabili risolte in più passate.

## Strumenti

Penna, evidenziatore, gomma, sei colori, tre spessori, annulla/rifai, esportazione PNG.
La lavagna si salva da sola nel browser (localStorage).

Scorciatoie: `P` penna · `H` evidenziatore · `G` gomma · `Ctrl+Z` annulla · `Ctrl+Invio` risolvi.

## Sviluppo

È un unico file statico: `index.html`. Per provarlo in locale basta un server statico,
per esempio `python -m http.server`.
