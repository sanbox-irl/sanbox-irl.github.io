---
title: OMNIO
date: 2024-03-04 17:46:54
---

*OMNIO*, made with art by Yuko Ota, is a game about combining blocks into complicated shapes and forms.

<div style = "text-align:center;">
    <canvas id="canvas" width="1280" height="720"></canvas>
</div>
<div>
    <script type=module> import init from '../../../../game_wasm/omnio/omnio.js'; async function run() { await init(); } run(); </script>
</div>

## Controls

You can **only** combine and split blocks using the machines.

Unfortunately, it is not possible to rebind control currently.

| Action        | Keyboard | Xbox | Nintendo |
| ------------- | ---------| -----| -------- |
| **Pickup and Place**| `E` | `X` | `Y` |
| **Rotate**| `R` | `LB`/`RB` | `L`/`R` |
| **Restart Level**| `ENTER` | `Y` | `X` |
