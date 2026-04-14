# ✨ Flux Particles — 3D Hand-Reactive Particle System

<p align="center">
  <img src="https://img.shields.io/badge/Three.js-r128-black?style=for-the-badge&logo=three.js" />
  <img src="https://img.shields.io/badge/MediaPipe-Hands-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/WebGL-2.0-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Vanilla-JavaScript-yellow?style=for-the-badge&logo=javascript" />
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" />
</p>

<p align="center">
  A real-time, browser-based 3D particle system that reacts to your hand gestures via webcam. <br/>
  Open your hand to expand the particle cloud — close your fist to contract it. <br/>
  Switch between stunning particle templates: Heart, Nebula, Saturn, and more.
</p>

---

## 🎥 Demo

> Open your webcam, show your hand, and watch 15,000 particles respond to your every move.

![Demo Placeholder](https://via.placeholder.com/900x450/050505/00f2ff?text=Flux+Particles+Demo)

---

## 🌟 Features

- **Real-Time Hand Tracking** — Uses Google MediaPipe Hands to detect and track up to 2 hands via webcam, with no backend required.
- **Hand Tension Interaction** — Measures the openness of your hand (closed fist → expand → open palm) and maps it to particle scale in real time.
- **6 Particle Shape Templates** — Morph 15,000 particles between beautiful 3D formations:
  - 💥 **Fireworks** — Random explosive scatter
  - ❤️ **Heart** — Volumetric 3D heart using the classic algebraic heart surface formula
  - 🌸 **Flower** — 3D parametric rose / polar flower
  - 🪐 **Saturn** — Planet sphere with a tilted particle ring system
  - 🧘 **Buddha** — Procedurally generated seated figure
  - 🌌 **Nebula** — 3-armed spiral galaxy
- **Smooth Morphing** — Particles lerp (linearly interpolate) to their target positions for fluid shape transitions.
- **Color Picker** — Choose any particle color using the native color picker, powered by Three.js `AdditiveBlending` for a glowing neon aesthetic.
- **Orbit Controls** — Click and drag to rotate the scene freely. Auto-rotation kicks in when no hands are detected.
- **Depth Fog** — Exponential fog adds depth perception to the 3D scene.
- **Responsive Design** — UI adapts for mobile screens with bottom-panel layout.
- **No Server Required** — Runs entirely in the browser. Just open the HTML file.

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| [Three.js r128](https://threejs.org/) | 3D WebGL rendering engine |
| [MediaPipe Hands](https://google.github.io/mediapipe/solutions/hands) | Real-time hand landmark detection |
| [MediaPipe Camera Utils](https://www.npmjs.com/package/@mediapipe/camera_utils) | Webcam capture and frame streaming |
| Three.js OrbitControls | Mouse/touch-based camera navigation |
| Vanilla JavaScript (ES6+) | Application logic, no framework needed |
| HTML5 / CSS3 | UI overlay, glassmorphism panels |

---

## 🚀 Getting Started

### Prerequisites

- A modern browser with **WebGL support** (Chrome, Firefox, Edge, Safari 15+)
- A **webcam** for hand-tracking interaction
- No Node.js, npm, or build tools needed — all dependencies load from CDN

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/your-username/flux-particles.git

# 2. Navigate into the project folder
cd flux-particles

# 3. Open index.html directly in your browser
#    OR serve it locally (recommended to avoid camera permission issues):
npx serve .
# then visit http://localhost:3000
```

> ⚠️ **Important:** Most browsers block webcam access for `file://` URLs. Use a local server (e.g., `npx serve`, `python -m http.server`, or VS Code Live Server) for the hand-tracking to work correctly.

---

## 📁 Project Structure

```
flux-particles/
│
├── index.html          # Single-file application (HTML + CSS + JS)
└── README.md           # This file
```

All logic is contained within `index.html` for zero-dependency portability. The project loads its libraries via CDN at runtime.

---

## 🎮 How to Use

1. **Open the app** in your browser (served via a local server).
2. **Grant webcam access** when the browser prompts you.
3. The status indicator in the panel will turn **green** once the camera is active.
4. **Show your hand** to the webcam:
   - ✊ **Close your fist** → particles contract inward
   - 🖐️ **Open your palm** → particles expand outward
5. **Select a template** from the panel buttons to morph particles into a new shape.
6. **Pick a color** using the color input to change the particle glow.
7. **Click and drag** anywhere on the canvas to orbit the camera around the scene.

---

## ⚙️ Configuration

You can tweak the following constants near the top of the `<script>` section in `index.html`:

```javascript
const CONFIG = {
  count: 15000,       // Total number of particles (lower for better performance)
  size: 0.12,         // Particle point size in world units
  lerpSpeed: 0.08,    // Morphing speed (0.01 = very slow, 0.3 = near-instant)
  defaultColor: 0x00f2ff  // Default particle color (hex)
};
```

### Hand Sensitivity Tuning

The hand tension mapping can be adjusted in the `onResults` callback:

```javascript
const minVal = 0.15;  // Wrist-to-fingertip distance for a fully closed fist
const maxVal = 0.45;  // Wrist-to-fingertip distance for a fully open palm
```

Adjust these if your hand size or camera distance requires different calibration.

---

## 🧠 How It Works

### Hand Detection Pipeline

```
Webcam Feed (640x480)
      ↓
MediaPipe Hands Model
      ↓
21 Landmarks per hand (x, y, z normalized coords)
      ↓
Measure average distance: Wrist (landmark 0) → 5 Fingertips (4,8,12,16,20)
      ↓
Normalize to [0..1] tension value
      ↓
Map tension → 3D particle scale via Three.js Vector3.lerp()
```

### Particle Morphing System

Each of the 15,000 particles has a **current position** (rendered) and a **target position** (shape formula output). Every animation frame, current positions move toward targets using linear interpolation:

```
new_pos = current_pos + (target_pos - current_pos) * lerpSpeed
```

Switching templates recalculates all target positions using the selected shape's mathematical formula, and the particles smoothly flow into the new configuration.

### Shape Formulas

- **Heart** — Uses the implicit algebraic surface: `(x² + 9/4·z² + y² − 1)³ − x²y³ − 9/80·z²y³ ≤ 0` with rejection sampling for volume fill.
- **Flower** — Polar parametric: `r = 10 + 5·cos(5θ)·sin(3φ)` in spherical coordinates.
- **Nebula** — Archimedean spiral with 3 arms rotated 120° apart, with vertical thickness tapering from center.
- **Saturn** — 75% torus ring (r = 14–20) + 25% sphere (r = 9), combined via random weight.

---

## 🔧 Performance Tips

- Lower `CONFIG.count` to `5000–8000` on lower-end devices.
- The MediaPipe model uses `modelComplexity: 1` (full accuracy). Set to `0` for faster, slightly less accurate tracking.
- The renderer caps pixel ratio at `2` via `Math.min(window.devicePixelRatio, 2)` to avoid excessive GPU load on high-DPI displays.

---

## 🤝 Contributing

Contributions are welcome! Here are some ideas:

- [ ] Add more particle shape templates (DNA helix, skull, text mesh, etc.)
- [ ] Pinch gesture to change color dynamically
- [ ] Two-hand gestures for rotation/zoom control
- [ ] Audio reactivity (microphone frequency → particle behavior)
- [ ] Export current frame as image
- [ ] GUI slider controls for particle size, speed, and count

To contribute:

```bash
# Fork the repo, then:
git checkout -b feature/your-feature-name
git commit -m "Add: your feature description"
git push origin feature/your-feature-name
# Open a Pull Request
```

---

## 🐛 Known Issues / Troubleshooting

| Issue | Solution |
|---|---|
| Camera not starting | Make sure you're serving via a local server, not `file://`. Check browser permissions. |
| Hand not detected | Ensure adequate lighting. Keep your hand within ~50–80cm of the camera. |
| Low performance / lag | Reduce `CONFIG.count` to 5000 or lower in the script config. |
| OrbitControls not working | Ensure the `three@0.128.0` OrbitControls script is loading correctly (check browser console). |
| Particles not morphing | Check browser console for JavaScript errors. CDN libraries may be unavailable offline. |

---

## 📜 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- [Three.js](https://threejs.org/) by Mr.doob and contributors
- [Google MediaPipe](https://mediapipe.dev/) for the incredible real-time ML hand tracking solution
- Mathematical heart surface formula from the mathematical community

---

## 📬 Contact

Made with ❤️ and particles.

If you found this project interesting, consider giving it a ⭐ on GitHub!

> **GitHub About (one-liner):**
> *Real-time 3D particle system that reacts to hand gestures via webcam — built with Three.js & MediaPipe Hands. 15,000 particles morph into Hearts, Nebulae, Saturn rings & more.*
