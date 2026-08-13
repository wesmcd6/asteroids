# Asteroids

### ▶ [Play it live](https://wesmcd6.github.io/asteroids/)

The classic vector arcade game, rebuilt in a **single self-contained HTML file** —
white wireframe graphics on black, a ship that drifts with real momentum, rocks
that split when you shoot them, saucers that hunt you, and hyperspace when it all
goes wrong. No build step, no dependencies, no server.

## Play it

Open `index.html` in any modern browser — that's the whole game.

```
xdg-open index.html      # Linux
open index.html          # macOS
start index.html         # Windows
```

Or serve the folder with any static server (e.g. `python3 -m http.server`).

## Controls

| Action | Keyboard | Touch |
|---|---|---|
| Rotate | `←` `→` (or `A` `D`) | ↺ ↻ buttons |
| Thrust | `↑` (or `W`) | ▲ button |
| Fire | `Space` | FIRE |
| Hyperspace | `Shift` (or `H`) | HYPER |
| Pause | `P` | — |

On phones the play field switches to a **tall portrait layout** so it fills the
screen, and on-screen thumb controls appear automatically.

## Scoring

| Target | Points |
|---|---|
| Large asteroid | 20 |
| Medium asteroid | 50 |
| Small asteroid | 100 |
| Large saucer | 200 |
| Small saucer | 1000 |

An extra ship every **10,000** points. Your high score is saved locally.

## Faithful details

- **Newtonian drift** — you thrust and coast; there is no brake
- **Everything wraps** around the screen edges, including objects drawn
  half-on-each-side
- Asteroids split **large → 2 medium → 2 small → dust**
- The **small saucer aims at you**, and its aim tightens as your score climbs
- **Hyperspace** teleports you anywhere — with the original's small chance of
  destroying you instead
- Only **4 of your shots** can be in flight at once, as in the arcade
- The iconic **two-note heartbeat** that speeds up as the field empties
- Your ship breaks apart into its own line segments when destroyed
- A **vector-monitor CRT look**: phosphor persistence (bright lines leave a
  decaying trail), beam bloom, scanlines and a soft vignette
- **Screen shake** on impacts and a white **flash** when your ship is destroyed

## How it works

Everything is plain JavaScript on a `<canvas>`:

- Vector shapes are point lists stroked at nine wrapped offsets, so objects
  crossing an edge appear on both sides seamlessly
- Space is treated as a torus — collision and saucer aiming use the shortest
  *wrapped* distance between two points
- Sound is synthesized live with the Web Audio API (no audio files): fire,
  explosions, thrust rumble, saucer siren, and the heartbeat
- The simulation runs on a fixed 60 Hz timestep, decoupled from rendering

## Disclaimer

This is an original, independent implementation written from scratch, inspired by
the classic vector-shooter genre. It is **not affiliated with, endorsed by, or
derived from Atari** or any other rights holder. No third-party code, artwork,
sounds, or other assets are used — all graphics are generated from vector
coordinates and all audio is synthesized at runtime. "Asteroids" is used here
only as a descriptive title; any trademarks are the property of their respective
owners.

## License

Released under the [MIT License](LICENSE).
