# Lighthouse Archipelago

A short browser exploration and puzzle game built with Three.js.

You wake up shipwrecked on a chain of dark islands with nothing but a name, Mara, and a red light flashing far to the north. Relight six lighthouses by turning mirrors to route each island's sunstone beam into the lighthouse lens. Every light you restore raises a causeway to the next island, brings back a memory, and moves you closer to finding out how you ended up here.

## Play

Open `index.html` in any modern browser. There is no build step or install. Three.js and the fonts load from public CDNs.

To host it, enable GitHub Pages for this repo (Settings → Pages → Deploy from a branch → `main`, root folder).

## Controls

| Input | Action |
| --- | --- |
| WASD / arrow keys | Walk |
| Mouse drag | Look around |
| Scroll | Zoom |
| E / Space | Turn a mirror, read a note, interact |
| J | Open the journal |
| Touch | Left stick to walk, drag to look, Use button to interact |

## Mechanics

- **Mirrors** reflect the beam 90°. Each press flips them between `/` and `\`.
- **Splitting glass** passes the beam straight through and also reflects it, turning one beam into two.
- **Rune stones** open a stone sluice gate only while a beam is touching them.
- Some islands have several lamps or several sunstones, and every lamp must be lit at once.

## Structure

Everything lives in `index.html`:

- `ISLANDS` holds each island's puzzle layout on a 7×7 grid, its light characteristic, its bottled note and its memory.
- `traceOnce` / `trace` follow beams through the grid, including gates that open when switches are hit.
- The finale is a small state machine in the main loop (`lit → approach → blind → green → leave`).
