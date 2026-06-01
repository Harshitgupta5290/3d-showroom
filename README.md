# ✦ LUMINA — WebGL Interactive Particle Engine

<p align="center">
  <img src="https://img.shields.io/badge/WebGL-Bloom-00f2ff?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Three.js-r128-black?style=for-the-badge&logo=three.js" />
  <img src="https://img.shields.io/badge/MediaPipe-AI%20Hands-7c3aed?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Vanilla-JavaScript-yellow?style=for-the-badge&logo=javascript" />
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" />
</p>

<p align="center">
  <strong>Real-time 3D particle engine with UnrealBloom glow, AI hand tracking, and GPU cursor physics.</strong><br/>
  Particles flee your cursor. Click to attract them. Show your hand to command the cloud.<br/>
  9 shape templates. 9 color presets. Zero install. One file.
</p>

<p align="center">
  <a href="https://vercel.com/new/clone?repository-url=https://github.com/Harshitgupta5290/3d-showroom">
    <img src="https://vercel.com/button" alt="Deploy with Vercel" />
  </a>
</p>

---

## 🎮 Live Demo

**[→ Launch LUMINA](https://nova-particles.vercel.app)**

---

## 💼 IT Industry Use Cases

LUMINA is a ready-made WebGL showcase for any professional context:

| Use Case | How |
|---|---|
| **Tech Conference Backdrop** | Run fullscreen on a display behind your talk stage |
| **Client Pitch / Sales Demo** | Set brand colors via the color picker, morph to a relevant shape |
| **Developer Portfolio** | Deploy in 60 seconds — immediately demonstrates WebGL expertise |
| **Job Interview Showpiece** | Demonstrates Three.js, custom GLSL shaders, AI integration, real-time 3D |
| **Product Launch Screen** | Customize colors to brand palette, use as interactive loading/splash screen |
| **WebGL Capability Demo** | Show clients "what's possible in the browser" without any app download |
| **Workshop / Training** | Teach Three.js, shader programming, MediaPipe, post-processing concepts |

---

## ✨ What Makes It Wow

### Engine
- **UnrealBloom post-processing** — particles glow like real neon lights; bloom spreads across the scene
- **Custom GLSL ShaderMaterial** — per-particle soft circular glow with HSL hue/brightness variation
- **GPU cursor physics** — cursor repulsion/attraction computed entirely on the GPU in the vertex shader (zero CPU cost)
- **Background star field** — 2,200 tinted stars with slow rotation create depth and atmosphere

### Interaction (works without camera)
- **Cursor repel** — move your cursor and particles flee it in real-time
- **Click + hold** — particles rush toward your cursor (attract mode)
- **Mouse distance** controls particle expansion when no camera is active
- **Touch support** — full mobile gesture support

### AI Hand Tracking (optional, requires webcam)
- **Hand tension** — open palm expands the cloud, closed fist contracts it
- **Pinch gesture** — thumb + index cycle through 9 preset colors
- Powered by Google MediaPipe, runs entirely in the browser

### 9 Shape Templates
| # | Shape | Description |
|---|---|---|
| 1 | 💥 Fireworks | Explosive scatter |
| 2 | ❤️ Heart | Volumetric algebraic heart surface |
| 3 | 🌸 Flower | Parametric rose in spherical coords |
| 4 | 🪐 Saturn | Planet sphere + ring system |
| 5 | 🧘 Buddha | Procedural seated figure |
| 6 | 🌌 Nebula | 3-armed Archimedean spiral galaxy |
| 7 | 🧬 DNA | Double helix — two strands offset by π |
| 8 | 🌪️ Vortex | Expanding spiral cone |
| 9 | ⭐ Star | 8-arm starburst |

Every shape transition **scatters → reforms** with a dramatic explosion effect.

---

## 🚀 Deploy in 60 Seconds

### Vercel (recommended)

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/Harshitgupta5290/3d-showroom)

The included `vercel.json` sets `Permissions-Policy: camera=*` so webcam works on the deployed URL.

### Local

```bash
git clone https://github.com/Harshitgupta5290/3d-showroom.git
cd 3d-showroom

# Python
python3 -m http.server 8000
# → http://localhost:8000

# Node
npx serve .
# → http://localhost:3000
```

> Always serve via `http://localhost` — webcam requires a secure context (`file://` won't work).

---

## 🎮 Controls

| Input | Action |
|---|---|
| **Move cursor** | Particles flee (GPU repulsion field) |
| **Click + hold** | Particles rush toward cursor |
| **Scroll** | Zoom in/out |
| **Drag** | Orbit the 3D scene |
| `1` – `9` | Switch shape template |
| `Space` | Pause / Resume |
| `R` | Reset camera |
| `H` | Toggle control panel |
| `S` | Save screenshot as PNG |
| `F` | Fullscreen |
| `C` | Cycle color preset |
| **🤏 Pinch** | Cycle colors (camera mode) |
| **🖐️ Open palm** | Expand particles (camera mode) |
| **✊ Closed fist** | Contract particles (camera mode) |

---

## ⚙️ Configuration

Edit these values in the `CFG` object at the top of `<script>`:

```javascript
const CFG = {
    count:     15000,   // Particle count (lower for slow devices)
    size:      0.12,    // Base particle size (also controllable via UI slider)
    lerpSpeed: 0.08,    // Morph speed (0.01 = glacial, 0.3 = instant)
    bloom:     1.4,     // Bloom strength (also controllable via UI slider)
};
```

---

## 📁 What's Included

```
lumina/
├── index.html      # Landing page — marketing, use cases, live preview
├── app.html        # Particle engine — HTML + CSS + GLSL + JS (~1,700 lines)
├── vercel.json     # Vercel deployment config (camera permissions header)
├── LICENSE         # MIT License
└── README.md
```

Two files. No build step. No npm. No server required (beyond a basic HTTP server for camera).

---

## 🛠️ Tech Stack

| Technology | Role |
|---|---|
| [Three.js r128](https://threejs.org/) | WebGL 3D rendering, scene graph |
| Custom GLSL ShaderMaterial | Per-particle bloom glow + GPU cursor physics |
| [Three.js UnrealBloomPass](https://threejs.org/examples/?q=bloom) | HDR bloom post-processing |
| [Google MediaPipe Hands](https://mediapipe.dev/) | Real-time AI hand landmark detection |
| Vanilla JavaScript (ES6+) | Application logic |

---

## 🐛 Troubleshooting

| Issue | Fix |
|---|---|
| **Camera not starting** | Must be served over HTTPS or `localhost`. Check browser address-bar camera permission icon. |
| **Camera blocked on Vercel** | `vercel.json` sets `Permissions-Policy: camera=*` — ensure latest code is deployed. |
| **Bloom not visible** | Check browser console — post-processing CDN scripts must load. |
| **Low FPS** | Lower `CFG.count` to 8000 in the script config. |
| **Black screen** | WebGL must be enabled. Check `chrome://settings` → System → Hardware acceleration. |

---

## 📄 License

[MIT License](LICENSE) — free for personal and commercial use. Attribution appreciated.

---

**Made with ✦ by [Harshit Gupta](https://github.com/Harshitgupta5290)**
