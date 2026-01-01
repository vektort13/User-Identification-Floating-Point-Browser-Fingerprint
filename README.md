# Vektor T13 - Floating Point Browser Fingerprint

Offline single‑file checker for floating‑point determinism and WebAudio stability tests.

**By:** Vektor T13 Technologies  
**Developed by:** Dmytro Momot  
**Site:** https://detect.expert

## Overview

This project is a standalone HTML page that runs locally in your browser and **does not make any network requests** (CSP: `connect-src 'none'`).

It generates a reproducible “profile” you can export to JSON and compare **before/after** changes (e.g., overclock/undervolt, driver updates, thermal changes, BIOS tweaks).

## Features

### Floating‑Point (FP)
- Deterministic IEEE‑754 sanity checks (double + float32 via `Math.fround`)
- Non‑associativity check and optional raw hex dumps (for deeper inspection)
- Stress invariants:
  - `sin²(x) + cos²(x) ≈ 1`
  - `exp(log(y)) ≈ y`
  - `sqrt(y)² ≈ y`
  - `1 / (1 / y) ≈ y`
- Micro‑benchmarks (median runtime, ns/iter)

### WebAudio
- AudioContext capability + parameters (sampleRate, latency buckets, etc.)
- Realtime graph probe (quiet oscillator → analyser)
- OfflineAudioContext render of a fixed audio graph:
  - oscillator → filter → waveshaper → compressor → gain
- Buffer metrics (mean/rms/peak/zero‑crossings) + optional checksum

### Reports
- Export current run as JSON
- Import a previous JSON report and show a **diff** (only changed keys)

## Usage

1. Save the file as `index.html` (or any name).
2. Open it in a browser (Chrome/Edge/Firefox).
3. Click **“Запустить тесты”**.
4. (Optional) enable **“Детально (raw значения)”** for deeper diagnostics.
5. Export JSON, repeat after system changes, then import to compare.

## Security / Privacy

- Runs fully offline.
- No external assets, no fetch/XHR/WebSocket (blocked by CSP).
- Everything stays on your machine unless you manually share exported JSON.

## Notes

Some browsers require a user gesture to start/resume AudioContext — the “Run tests” button satisfies that requirement.

## Credits

© Vektor T13 Technologies — https://detect.expert  
Developed by Dmytro Momot
