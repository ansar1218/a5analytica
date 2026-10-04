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
