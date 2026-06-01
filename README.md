# ✨ Flux Particles — 3D Hand-Reactive Particle System

<p align="center">
  <img src="https://img.shields.io/badge/Three.js-r128-black?style=for-the-badge&logo=three.js" />
  <img src="https://img.shields.io/badge/MediaPipe-Hands-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/WebGL-2.0-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Vanilla-JavaScript-yellow?style=for-the-badge&logo=javascript" />
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" />
</p>

<p align="center">
  <strong>A real-time, browser-based 3D particle system that reacts to your hand gestures via webcam.</strong><br/>
  Open your hand → particles expand. Close your fist → they contract.<br/>
  Switch between 6 stunning particle templates: Heart, Nebula, Saturn, and more.
</p>

<p align="center">
  <a href="https://vercel.com/new/clone?repository-url=https://github.com/Harshitgupta5290/3d-showroom">
    <img src="https://vercel.com/button" alt="Deploy with Vercel" />
  </a>
</p>

---

## 🎮 Live Demo

> Open your webcam and watch 15,000 particles respond to your hand in real-time. No installation, no backend — just a browser.

**[→ Open Live Demo](https://3d-showroom-harshit.vercel.app)**

---

## 🌟 Features

### Core
- **Real-Time Hand Tracking** — Google MediaPipe Hands; up to 2 hands, no backend
- **Hand Tension Interaction** — Maps open palm → expand / closed fist → contract
- **15,000 Particles** — Smooth 60 FPS with custom GLSL shader
- **Custom Glow Shader** — Per-particle soft circular glow with HSL color variation (not PointsMaterial)
- **Organic Idle Animation** — Phase-offset sin/cos noise keeps particles alive when no hand is present

### 9 Particle Templates
| # | Template | Description |
|---|---|---|
| 1 | 💥 Fireworks | Random explosive scatter |
| 2 | ❤️ Heart | Volumetric 3D algebraic heart surface |
| 3 | 🌸 Flower | Parametric rose in spherical coords |
| 4 | 🪐 Saturn | Planet sphere + ring system |
| 5 | 🧘 Buddha | Procedural seated meditation figure |
| 6 | 🌌 Nebula | 3-armed Archimedean spiral galaxy |
| 7 | 🧬 DNA | Double helix — two strands offset by π |
| 8 | 🌪️ Vortex | Expanding spiral cone (tornado) |
| 9 | ⭐ Star | 8-arm starburst |

### Interaction
- **Pinch gesture** (thumb + index) → cycles through 9 preset colors
- **Morph speed slider** — tune interpolation from glacial to instant
- **Particle size slider** — live-update via shader uniform
- **Pause / Resume** — freeze the animation mid-morph
- **Screenshot / Save** — one-click PNG download of the current frame

### UX
- First-run onboarding overlay (shown once, stored in localStorage)
- Keyboard shortcuts: `1–9` shapes, `Space` pause, `R` reset camera, `H` hide panel, `S` screenshot
- 9 quick-pick color presets + full color picker
- Hide/show control panel (clean fullscreen mode)
- OrbitControls — drag to rotate; auto-rotates when idle
- Depth fog for 3D perception
- Responsive (desktop, tablet, mobile)
- **Zero dependencies to install** — all libs load from CDN

---

## 🚀 Deploy to Vercel (One Click)

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/Harshitgupta5290/3d-showroom)

The included `vercel.json` sets the required `Permissions-Policy: camera=*` header so webcam access works on the deployed URL.

---

## 💻 Run Locally

**Requirements:** Any modern browser with WebGL support. No Node.js or build tools needed.

```bash
git clone https://github.com/Harshitgupta5290/3d-showroom.git
cd 3d-showroom

# Option A — Python (recommended for webcam access)
python3 -m http.server 8000
# Visit: http://localhost:8000

# Option B — Node.js
npx serve .
# Visit: http://localhost:3000
```

> **Note:** Open via `http://localhost:...`, not `file://` — browsers block webcam for file:// URLs.

---

## 📁 What's Included

```
3d-showroom/
├── index.html      # Complete app (HTML + CSS + JS, ~660 lines)
├── vercel.json     # Vercel deployment config (camera header)
├── LICENSE         # MIT License
└── README.md
```

All logic is self-contained in `index.html`. No build step, no npm install, no server required.

---

## 🎮 How to Use

1. **Allow camera** when the browser prompts
2. The status dot turns green once the camera is active
3. **Show your hand** to the webcam:
   - ✊ Close fist → particles contract
   - 🖐️ Open palm → particles expand
   - 🤏 Pinch (thumb + index) → cycle colors
4. **Select a template** from the panel (or press `1–9`)
5. **Adjust sliders** to tune morph speed and particle size
6. **Click + drag** anywhere to orbit the 3D scene
7. Press `H` to hide the panel for a clean view · `S` to save a screenshot

### Keyboard Shortcuts
| Key | Action |
|---|---|
| `1` – `9` | Switch particle template |
| `Space` | Pause / Resume animation |
| `R` | Reset camera to default view |
| `H` | Toggle control panel |
| `S` | Save screenshot as PNG |

---

## ⚙️ Configuration

Edit these values near the top of the `<script>` in `index.html`:

```javascript
const CONFIG = {
    count: 15000,       // Particle count (lower = better performance on slow devices)
    size: 0.12,         // Particle point size in world units
    lerpSpeed: 0.08,    // Morphing speed (0.01 = slow, 0.3 = instant)
    defaultColor: 0x00f2ff  // Default color (hex)
};
```

Hand sensitivity (adjust if your hand size differs):
```javascript
const minVal = 0.15;  // Closed fist threshold
const maxVal = 0.45;  // Open palm threshold
```

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| [Three.js r128](https://threejs.org/) | WebGL 3D rendering |
| [MediaPipe Hands](https://google.github.io/mediapipe/solutions/hands) | Real-time hand landmark detection |
| [MediaPipe Camera Utils](https://www.npmjs.com/package/@mediapipe/camera_utils) | Webcam frame capture |
| Three.js OrbitControls | Mouse/touch 3D navigation |
| Vanilla JavaScript (ES6+) | Application logic |

---

## 🐛 Troubleshooting

| Issue | Fix |
|---|---|
| Camera blocked | Serve via `http://localhost` (not `file://`); check browser camera permission |
| Hand not detected | Improve lighting; keep hand 30–60 cm from camera; use Chrome |
| Low FPS | Lower `CONFIG.count` to 5000–8000 |
| OrbitControls missing | Check browser console; CDN may be unavailable — use a local server |
| Webcam blocked on Vercel | `vercel.json` sets `Permissions-Policy: camera=*` — re-deploy if missing |

---

## 📄 License

[MIT License](LICENSE) — free for personal and commercial use. Attribution appreciated.

---

## 🙏 Acknowledgements

- [Three.js](https://threejs.org/) by Mr.doob and contributors
- [Google MediaPipe](https://mediapipe.dev/) for real-time ML hand tracking
- Algebraic heart surface formula from the mathematics community

---

**Made with ❤️ by [Harshit Gupta](https://github.com/Harshitgupta5290)**  
If you found this useful, consider giving it a ⭐ on GitHub!
