# WASM Arcade

4 browser games compiled from pure C (Raylib game logic) to WebAssembly via Emscripten.

Play at: **https://chongjie-ran.github.io/wasm-games/**

## Games

| Game | Folder | Controls |
|------|--------|----------|
| Frogger | `frogger/` | ← → A D Move, SPACE Jump |
| Pac-Man | `pacman/` | Arrow Keys / WASD, P Pause, R Restart |
| Space Invaders | `space-invaders/` | ← → A D Move, SPACE Shoot, R Restart, P Pause |
| Breakout | `breakout/` | ← → A/D Move Paddle, SPACE Launch Ball |

## Tech Stack

- **Game Logic**: Pure C (Raylib headers, no raylib dependency at runtime)
- **Compiler**: Emscripten (emcc)
- **Rendering**: HTML5 Canvas 2D (no external libraries)
- **Delivery**: WebAssembly (.wasm) + hand-written JS loaders

## Build from Source

```bash
# Emscripten required
emcc -O2 -s WASM=1 \
  -s EXPORTED_FUNCTIONS="['_init_game','_update_game',...]" \
  -s EXPORTED_RUNTIME_METHODS="['ccall','cwrap']" \
  game.c wasm_renderer.c -o game.js
```

## Architecture

Each game folder contains:
- `*.wasm` — compiled game logic
- `*.js` — hand-written JS loader (Emscripten-compatible)
- `index.html` — game page with Canvas 2D rendering

## License

CC0 — public domain
