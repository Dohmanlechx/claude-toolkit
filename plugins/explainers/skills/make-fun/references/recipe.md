# make-fun recipe

The house look: a sticker book. Chunky 2px ink borders, hard offset shadows, rounded
corners, a dotted background, small tilts, bright food-ish colors, one moment of motion.
[example.html](example.html) implements all of it; copy its CSS rather than re-deriving.

## Tokens

Copy the `:root` block, both dark blocks and `body` from example.html verbatim. Names:

| Token | Role |
|---|---|
| `--bg`, `--surface`, `--ink`, `--muted`, `--line` | Ground, card, text, secondary text, borders/shadow |
| `--sun` | Primary highlight, selected state, hero marker |
| `--tomato` | Danger, failure, removed lines, backend calls |
| `--pickle` | Success, additions, primary button, waiting |
| `--sky` | Links, screens, info |
| `--grape` | Client/third party, "sneaky" tags, states |
| `--*-soft` | Pale fills of each color for tags and tinted stickers |
| `--on-color` | Text on a saturated chip (dark in both themes) |

Fonts (Google Fonts): Bricolage Grotesque 800 display, Figtree body, JetBrains Mono for
labels/code. Subject strongly suggests another vibe -> swap the accent hues only; keep the
structure.

## Pick sections

Order is fixed; include a section only when the source has its material.

| Section | Use when the source has | Component in example.html |
|---|---|---|
| Hero + ticket | Always. Thesis headline with one `.hl` marked phrase; ticket = 4-7 facts + one big number pair | `.hero`, `.ticket` |
| Playable journey | A flow, state machine, process, lifecycle, request path | `.picker` + `.board` + `SCENARIOS` JS |
| Menu board | A list of endpoints, commands, options, APIs, choices with outcomes | `.menu` (dark board), `.menu-item` |
| Big numbers | 2-3 striking figures (timeouts, counts, sizes, dates) | `.timers` |
| Trap wall | Gotchas, risks, surprises, edge cases, review findings | `.traps` with `.sev ouch / sneaky / nice` |
| Rulebook | Rules, principles, steps of a checklist (numbered = real order) | `.rules` (counter badges), `.types` |
| Shelf | An inventory: files changed, items, components; + 2-3 side notes | `.shelf`, `#files` bars, `.note` |
| Footer | Link back to the source + build date | `footer` |

## Playable journey

- 3-7 scenarios as pill buttons; the first is pre-selected on load.
- Each scenario: `name`, one-line `blurb`, 4-11 `steps` of `{ k, t, d, s }`:
  `k` kind (maps to a colored dot + tag), `t` title (real names in `<code>`), `d` one or
  two plain sentences, `s` the state at that step (or omit the state rail if no states).
- Share common steps as constants (`APPEAR`, `DONE`) instead of repeating them.
- Kinds are subject-specific; define `TAGS` and a legend to match (example: Screen,
  Client app, Shared core, Backend, Waiting, Succeeded, Failed).
- Include at least one unhappy scenario if the source describes failure.
- Controls: Play/Pause (1.1s per step), Step, Reset; clicking a step jumps to it.
- Reaching a success end -> confetti burst; failure end -> wobble. Both off under
  `prefers-reduced-motion`.

## Joy devices (use all, sparingly)

- Dotted radial background on `body`; hard offset shadow `4px 4px 0 var(--line)`.
- Tilt: the ticket +1.6deg, every other trap card +-0.7deg. No tilt below 760px.
- Buttons press in on `:active` (translate 2px, shadow shrinks).
- Hero phrase on a `--sun` marker; eyebrows in uppercase mono with letter-spacing.
- Ticket has punched half-circle notches and a dashed divider.
- One confetti canvas, fixed, pointer-events none.

## Copy

- Headings are short and human ("Watch your step", "The shelf", "Today's menu").
- Eyebrows say where the facts come from ("Picked from the 12 gotchas").
- Section intros: one or two sentences, what the reader can do here.
- Trap cards: a severity tag, the trap as a headline, the why in one or two sentences,
  the source file in mono.
- Escape `<`, `>` and `&` inside code shown in HTML.
