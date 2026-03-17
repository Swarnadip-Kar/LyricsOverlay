# Lyrics Overlay Pro

A single-file browser tool that generates a **YouTube Music–style scrolling lyrics overlay** for use in video editors like DaVinci Resolve. No installation, no server, no build step — open `index.html` and go.

**[Live Demo →](https://YOUR_USERNAME.github.io/lyrics-overlay)**

---

## What it does

You paste your lyrics, set a BPM, and the tool displays them as a smooth tape-scroll overlay — the active line sits bright in the center, lines above and below fade out progressively toward the edges, exactly like YouTube Music or Apple Music's lyrics view.

You screen-record the result and drop it into your video editor as a transparent overlay track.

---

## Features

### Lyrics & Timing
- Paste any lyrics — one line per row
- Set **BPM** or **ms / beat** — the two fields are linked and update each other in real time
- Total duration is derived automatically from `lines × ms/beat` — no manual duration entry
- Live readout: total duration, ms per line

### Scroll Engine
- All lyrics rendered as one continuous vertical tape
- Active line stays centered; the whole tape scrolls as a single unit
- Opacity and font size fall off smoothly with distance from the active line
- Top and bottom edges fade out via CSS gradient masks — lines never pop in or disappear abruptly
- Scroll speed, active font size, inactive font size, and slot height are all independently adjustable

### Themes — 18 presets
Dark · Rose · Gold · Cyan · Amber · Ember · Frost · Clean · Parchment · Dusk · Indigo · Blush · Nebula · Crimson · Voltage · Petal · Sepia · Slate

Each preset configures font, weight, colors, and glow in one click.

### Fonts — 35+ typefaces across 4 categories
| Category | Fonts |
|---|---|
| **Instagram** | Inter, Montserrat, Lato, DM Sans, Space Grotesk, Outfit, Plus Jakarta Sans, Poppins, Raleway, Nunito, Quicksand, Josefin Sans |
| **Script** | Great Vibes, Pacifico, Satisfy, Allura, Tangerine, Pinyon Script, Sacramento, Alex Brush, Parisienne, Marck Script, Italianno, Euphoria Script, Courgette, Kaushan Script, Mr Dafoe |
| **Elegant** | Playfair Display, Cormorant Garamond, Bodoni Moda, DM Serif Display, Libre Baskerville, Cinzel |
| **Display** | Bebas Neue, Barlow Condensed, Oswald, Abril Fatface, Black Han Sans, Righteous, Exo 2, Orbitron, Press Start 2P |

Font weight (Thin / Regular / Semi / Bold / Black) and italic are independently toggleable for every font.

### Visual Controls
- Active line color, inactive line color
- Glow color + intensity on the active line
- Drop shadow toggle
- Edge fade opacity (how dark the farthest lines get)
- UPPERCASE toggle for the active line

### Layout Controls
- Vertical position: Center / Upper Center / Lower Center / Upper Third / Lower Third
- Text alignment: Center / Left / Right

### Player
- Play / Pause / Reset
- Seekable progress bar
- Line counter
- **Record Mode** — hides all controls for a clean screen capture
- Keyboard shortcuts: `Space` = Play/Pause · `R` = Record Mode · `Esc` = Back to settings

---

## How to use

### 1. Set up your overlay
1. Open `index.html` in any modern browser
2. Paste your lyrics into the text area (one line per row)
3. Enter your track's BPM — the ms/beat field updates automatically (or enter ms/beat directly)
4. Pick a theme, font, and adjust visual settings in the sidebar
5. Watch the live preview on the right update in real time

### 2. Record
1. Click **Launch Player**
2. Press **R** to enter Record Mode (controls hide)
3. Start your screen recorder:
   - **Windows**: Win + G (Xbox Game Bar)
   - **macOS**: QuickTime → New Screen Recording
   - **Cross-platform**: OBS Studio
4. Press **Space** to play — the tape will scroll through all lines at your set BPM
5. Stop recording when it finishes

### 3. Import into DaVinci Resolve

**Option A — Black background (Screen blend)**
> Use this when your text is white or light-colored.
1. Drop the recording onto a track above your video
2. In the Inspector, set **Composite Mode → Screen**
3. The black background disappears; only the text remains

**Option B — Green background (Chroma key)**
> Use this when you need colored text.
1. Drop the recording onto a track above your video
2. Open the **Color** page → Add **Delta Keyer** node
3. Pick the green background color to key it out

---

## Keyboard shortcuts

| Key | Action |
|---|---|
| `Space` | Play / Pause |
| `R` | Toggle Record Mode |
| `Esc` | Exit player, back to settings |

---

## Technical notes

- **Single file** — everything (HTML, CSS, JS, all fonts via Google Fonts CDN) is in `index.html`. No dependencies to install.
- **Fonts** require an internet connection to load from Google Fonts. Everything else works offline.
- **Screen recording cannot capture true alpha transparency.** The two workarounds (Screen blend for black bg, Delta Keyer for green bg) are both lossless when done correctly in DaVinci.
- The scroll engine works by rendering all lines as a single vertical strip and translating the whole strip with one CSS `transform`. The gradient masks on the container edges are the only thing that fades lines — nothing is ever added or removed from the DOM during playback.

---

## Project structure

```
lyrics-overlay/
└── index.html    # Everything — the entire app
└── README.md
```

---

## Deployment

### GitHub Pages (free, instant)
```bash
git init
git add .
git commit -m "Initial release"
git remote add origin https://github.com/YOUR_USERNAME/lyrics-overlay.git
git branch -M main
git push -u origin main
```
Then: **GitHub repo → Settings → Pages → Source: main / root**

Your app will be live at `https://YOUR_USERNAME.github.io/lyrics-overlay`

---

## License

MIT — do whatever you want with it.
