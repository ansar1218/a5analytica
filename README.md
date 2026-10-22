# A5Analytica.ai

A5Analytica.ai — AI-powered decision analytics application.

## Published app

The live Manus app is available at:

https://analyticaai-5ddqq6rx.manus.space/

## Repository contents

This repository contains a production snapshot exported from the published app:

- `index.html` — production entry document
- `assets/` — compiled JavaScript and CSS assets

The published URL exposes the compiled build rather than the original editable Manus project source. As a result, this repository contains the deployable snapshot, not the original React/TypeScript source tree.

## Run locally

Serve the repository with any static web server, for example:

```bash
python3 -m http.server 8080
```

Then open http://localhost:8080.

## Data City 3D

`Analytics → Data City 3D` opens a 3D view of the active dataset:

- Each numeric column (up to 8) becomes a building; its height and screen track the current row.
- Roads are relationships between columns with |r| ≥ 0.4, including lagged ones (up to 6 rows). Data packets travel from the column that moves first.
- The central dome scores how unusual the current row is across all columns. Beacons turn amber or red on rolling z-score spikes (2σ / 3σ against the previous 20 rows).
- Each building shows a Holt linear forecast for the next 7 rows.
- **What-if ±20%** on a column propagates expected changes one and two hops along the roads (Δb = r · σb/σa · Δa).
- With no dataset loaded, a simulated sample business is shown.

The view lives in `data-city/index.html` and also works on its own (it accepts a CSV upload). The app panel embeds it in an iframe and sends the dataset with:

```js
frame.contentWindow.postMessage({ type: 'a5-dataset', name, rows, numericCols }, origin)
```

Because this repository is a compiled snapshot, the panel was added directly to the bundle (`assets/index-Bh0nVBbt-dc.js`, renamed to bust caches). When the React source is available, port it as `client/src/components/panels/DataCityPanel.tsx`, add `datacity` to the Analytics nav group and the panel switch in `AppShell.tsx`, and copy `data-city/` into `client/public/`.
