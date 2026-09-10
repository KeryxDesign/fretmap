# FretMap

Cinque giochi per orientarsi sul manico della chitarra. Si gioca dal telefono, in orizzontale, senza installare niente.

**→ https://keryxdesign.github.io/fretmap/**

## I cinque giochi

| Gioco | Cosa chiede |
|---|---|
| **Distanza** | vedi due tasti accesi, conti quanti semitoni ci sono in mezzo |
| **Arrivo** | ti dice quanti semitoni salire o scendere, tocchi il tasto d'arrivo |
| **Nome** | conti l'intervallo e dici il nome della nota che esce |
| **Stessa nota** | trovi tutti gli altri posti dove vive la stessa nota |
| **Orecchio** | senti due note, conti la distanza |

Il motore sceglie da solo il gioco e la coppia di corde: tiene una mappa di quanto vai bene su ogni combinazione e ti serve quella che ti riesce peggio. Tre livelli di partenza, dichiarati da te alla prima apertura.

## Da telefono

- Si tiene **in orizzontale**. In verticale la partita mostra un avviso: il manico ha bisogno di tutta la larghezza.
- Alla partenza chiede lo schermo intero e blocca l'orientamento, dove il browser lo permette.
- Il gioco «Orecchio» usa l'audio del browser: il primo tocco sblocca il suono.
- I bersagli da dito sono almeno 38 px reali sul manico e 44 px sulla fila di risposta e sulla freccia indietro. Sul manico non c'è spazio morto: ogni tocco cade sulla casella più vicina.

## Dati

Tutto resta sul telefono, in `localStorage`: lingua, livello, punti, mappa delle competenze. **Nessun server, nessun account, nessun tracciamento.** Se cancelli i dati del sito, riparti da zero.

## Cosa c'è dentro

Pagina statica. Nessuna build, nessun bundler: si apre e funziona.

- `index.html` — il gioco
- `support.js` — il runtime di Claude Design, carica React da CDN da solo
- `_ds/keryx-design-system-…/` — il design system Keryx
- `manifest.webmanifest` — per aggiungerlo alla schermata home
- `sync/` — l'allineamento con Claude Design (vedi sotto)

## Allineamento con Claude Design

Il gioco nasce in Claude Design, progetto **FretMap Game**, file sorgente `SALTI.dc.html`. Il repo non è una copia identica: `index.html` è il sorgente **più** le riparazioni per il telefono, registrate in `sync/riparazioni-mobile.patch`.

La domanda del controllo non è «sono uguali?», è **«il repo si ricostruisce ancora dal sorgente applicando la patch?»**.

```bash
bash sync/verifica.sh <cartella-coi-file-scesi-da-claude-design>
```

I file di Claude Design **non si scaricano da riga di comando**: si leggono dentro una sessione con l'MCP e si salvano su disco. Procedura completa: `Sistema/_CORE/sop/operations/sop_allineamento_claude_design_repo.md`.

---

Keryx Design
