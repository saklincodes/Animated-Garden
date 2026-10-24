# 🌸 Animated Garden — A Living Floral Meadow

<div align="center">

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Vanilla JS](https://img.shields.io/badge/Vanilla-JavaScript-F7DF1E?logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![HTML5 & SVG](https://img.shields.io/badge/Render-SVG%20%2B%20Canvas-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/SVG)
[![Web Audio API](https://img.shields.io/badge/Audio-Web%20Audio%20API-4A90E2)](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/saklincodes/Animated-Garden/pulls)

**An interactive, procedurally generated audio-visual meadow built with SVG mathematics, Canvas physics, and native Web Audio synthesis.**

[Live Demo](#-quick-start) • [Features](#-features) • [URL Parameters & Personalization](#-url-parameters--personalization) • [Architecture](#-technical-architecture) • [License](#-license)

</div>

---

## 🌿 Overview

**Animated Garden** is a zero-dependency, cinematic generative web art experience. Designed as a digital keepsake that will never wilt, it renders a dense, breathing meadow of procedurally grown flowers, swaying foliage, glowing fireflies, and drifting petals accompanied by calming harmonic wind chimes.

Every single petal, stem, and stamen is computed dynamically in pure mathematical SVG paths, and all ambient sounds are synthesized in real-time via the browser's native **Web Audio API**—requiring zero external media files, bundles, or build tools.

---

## ✨ Features

- 🌸 **Procedural Botanical Generation**:
  - **Hero Peonies**: Complex multi-tiered rosette formations with breathing organic bloom stages.
  - **English Roses**: Layered cupped petals rendered with algorithmic curvature and gradient depth.
  - **Tulips & Sunflowers**: Graceful silhouettes, radial florets, and stippled seed discs.
  - **Daisies & Wild Lavender**: Multi-stem wind-responsive clusters adding organic meadow density.
- 🎨 **4 Atmospheric Curated Themes**:
  - `midnight`: Deep nocturnal sky with golden luminescent blooms and cozy romantic warmth.
  - `morning`: Soft daylight illumination with earthy terracotta tones and crisp greenery.
  - `vintage`: Nostalgic sepia parchment palette reminiscent of 19th-century botanical pressings.
  - `enchanted`: Bioluminescent mystic twilight with neon emerald greens and violet petals.
- 🎵 **Real-Time Web Audio Synthesizer**:
  - Native browser oscillator nodes producing organic harp arpeggios, bloom chimes, and modal chords (`Em9`, `Cmaj7`, `Dadd9`).
  - No `.mp3` or `.wav` dependencies—instant zero-latency audio generation.
  - Automatic gesture unlock compliant with modern browser autoplay policies.
- 💫 **Dual-Layer Canvas Particle Simulation**:
  - **Lucciole (Fireflies)**: Soft sine-oscillating light motes that drift ambiently across the meadow.
  - **Wind-blown Petals**: 2D tumbling physics reacting to screen velocity and ambient currents.
  - **Interactive Spark Bursts**: Radiant sparks emit whenever blossoms are touched.
- 📐 **Cinematic Parallax & Camera Dynamics**:
  - 4-layer spatial depth (foreground, hero, midground, background).
  - Smooth 2.5D cursor & pointer parallax.
  - Dynamic smooth zooming from bud stage to full panoramic bloom.
- 🎁 **Deterministic URL Personalization (PRNG)**:
  - Seeded using `xmur3` hash and `mulberry32` generator.
  - Generating links with custom names or messages deterministically produces an identical unique garden arrangement every time.
- 🔮 **Interactive Whispers & Secret Easter Egg**:
  - Tap any flower to trigger a harmonic chime, scale pulse, and romantic whisper toast.
  - **Secret**: Tapping 4 distinct floral varieties unlocks the rare *Enchanted Golden Rose*.
- ⚡ **Zero Dependencies & High Performance**:
  - 100% Vanilla HTML5, CSS3, and modern JavaScript.
  - Silky smooth 60 FPS animation loop with `requestAnimationFrame`.
  - Accessible: Full `prefers-reduced-motion` support.

---

## 🚀 Quick Start

### 1. Run Locally
Because this project uses 100% vanilla web standards with no build step required, you can run it instantly:

```bash
# Clone the repository
git clone https://github.com/saklincodes/Animated-Garden.git

# Navigate into the project folder
cd Animated-Garden
```

Simply open `index.html` in your favorite web browser, or serve it with any lightweight static server:

```bash
# Using Python
python -m http.server 3000

# Or using Node.js / npx
npx serve .
```

Visit `http://localhost:3000` to watch the garden bloom!

---

## 💌 URL Parameters & Personalization

You can personalize the garden for friends or loved ones simply by passing URL parameters:

| Parameter | Type | Default | Description |
|:---|:---|:---|:---|
| `to` | `string` | `"My Love"` | Recipient's name displayed in the document title |
| `from` | `string` | `"Alessio"` | Sender's name used for seeded layout hashing |
| `occasion` | `string` | `"just because"` | Occasion subtitle for the garden |
| `style` | `string` | `"midnight"` | Color theme: `midnight`, `morning`, `vintage`, or `enchanted` |
| `msg` | `string` | *See presets* | Pipe-delimited (`\|`) message lines |

### Example Personalized Links:

```text
# Midnight theme with custom message
https://saklincodes.github.io/Animated-Garden/?to=Sophia&style=midnight&msg=Every+day+with+you|is+a+garden+in+bloom.

# Enchanted bioluminescent theme
https://saklincodes.github.io/Animated-Garden/?to=Aria&style=enchanted

# Morning warmth theme
https://saklincodes.github.io/Animated-Garden/?to=Elena&style=morning
```

---

## 🛠️ Technical Architecture

```
Animated-Garden/
├── index.html       # Self-contained core engine (HTML5, SVG procedural math, Canvas, Web Audio)
├── LICENSE          # MIT Open Source License
└── README.md        # Documentation and customization guide
```

### Key Engineering Modules:

1. **Procedural Geometry Engine**:
   - `petalPath()`, `leafPath()`, `rosePetalPath()`, `tulipPetalPath()` construct cubic Bézier curves dynamically based on size, curl, and aspect ratio.
   - SVG `defs` share gradient profiles across 100+ blossoms to optimize GPU memory footprint.
2. **Stem Growth & Bloom Orchestration**:
   - Uses SVG quadratic curves (`Q` path syntax) and progressive `stroke-dashoffset` transitions.
   - Micro-animations powered by CSS keyframes (`breathe`, `sway`, `leafSway`) with randomized animation durations and negative delay phases to ensure non-synchronous, organic life.
3. **Sound Synthesis**:
   - Web Audio `OscillatorNode` combined with exponential gain curves creates natural bell-like decays.
   - Pentatonic frequency lookup maps ensure harmonic chord resolutions on every bloom stage and flower tap.

---

## 🎨 Themes Showcase

| Theme | Atmosphere | Primary Highlights |
|:---|:---|:---|
| **Midnight** | Starlit romantic dusk | Deep navy blue, champagne gold, ruby rose accents |
| **Morning** | Crisp dawn awakening | Warm cream, terracotta coral, vibrant meadow green |
| **Vintage** | Victorian botanical illustration | Aged parchment, burnt burgundy, antique ochre |
| **Enchanted** | Bioluminescent mystical forest | Deep abyss teal, glowing emerald, neon lilac |

---

## 🤝 Contributing

Contributions, bug reports, and creative flower variations are warmly welcomed!

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/NewFlowerType`)
3. **Commit** your changes (`git commit -m "feat: add glowing orchid variety"`)
4. **Push** to your branch (`git push origin feature/NewFlowerType`)
5. Open a **Pull Request**

---

## 📄 License

This project is open source and distributed under the [MIT License](LICENSE). Feel free to use, customize, and share it freely.

---

<div align="center">
  <sub>Crafted with tenderness and math by <a href="https://github.com/saklincodes">saklincodes</a>. If this project made you smile, feel free to give it a ⭐!</sub>
</div>
