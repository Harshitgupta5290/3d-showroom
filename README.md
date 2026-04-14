# ✨ Flux Particles — 3D Hand-Reactive Particle System

<p align="center">
  <img src="https://img.shields.io/badge/Three.js-r128-black?style=for-the-badge&logo=three.js" />
  <img src="https://img.shields.io/badge/MediaPipe-Hands-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/WebGL-2.0-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Vanilla-JavaScript-yellow?style=for-the-badge&logo=javascript" />
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" />
</p>

<p align="center">
  <strong>A real-time, browser-based 3D particle system that reacts to your hand gestures via webcam</strong><br/>
  Open your hand to expand the particle cloud — close your fist to contract it.<br/>
  Switch between stunning particle templates: Heart, Nebula, Saturn, and more.
</p>

---

## 📺 Live Demo

> **Try it now:** Open your webcam and watch 15,000 particles respond to your hand in real-time. No installation required.

[🎮 Open Live Demo](your-demo-url-here) | [📹 Watch Video](your-video-url-here)

---

## 🌟 Features

### Core Features
- **Real-Time Hand Tracking** — Uses Google MediaPipe Hands to detect and track up to 2 hands via webcam, with no backend required.
- **Hand Tension Interaction** — Measures the openness of your hand (closed fist vs. open palm) and maps it to particle scale dynamically.
- **15,000 Particles** — Smooth, responsive 60 FPS performance on modern browsers.

### 6 Beautiful Particle Templates
Morph particles into stunning 3D formations:
- 💥 **Fireworks** — Random explosive scatter pattern
- ❤️ **Heart** — Volumetric 3D heart using the algebraic heart surface equation
- 🌸 **Flower** — 3D parametric rose with petals
- 🪐 **Saturn** — Planet sphere with a tilted particle ring system
- 🧘 **Buddha** — Procedurally generated seated meditation figure
- 🌌 **Nebula** — 3-armed spiral galaxy formation

### User Experience
- **Smooth Morphing** — Particles lerp (linearly interpolate) to target positions for fluid transitions
- **Color Picker** — Choose any particle color with native color picker + neon glow effect
- **Orbit Controls** — Click and drag to rotate freely; auto-rotates when no hands detected
- **Depth Fog** — Exponential fog for enhanced 3D perception
- **Responsive Design** — Adapts for desktop, tablet, and mobile screens
- **Zero Setup** — Runs entirely in the browser; no server or build tools needed

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| [Three.js r128+](https://threejs.org/) | 3D WebGL rendering engine |
| [MediaPipe Hands](https://google.github.io/mediapipe/solutions/hands) | AI-powered hand landmark detection |
| [MediaPipe Camera Utils](https://www.npmjs.com/package/@mediapipe/camera_utils) | Webcam frame capture & streaming |
| Three.js OrbitControls | Mouse/touch-based 3D navigation |
| Vanilla JavaScript (ES6+) | Pure JS application logic |
| HTML5 Canvas + CSS3 | Rendering & UI styling |

---

## 🚀 Quick Start

### Prerequisites
- ✅ Modern browser with **WebGL 2.0 support** (Chrome 56+, Firefox 51+, Edge 15+, Safari 15+)
- ✅ A **working webcam** for hand tracking
- ✅ **No** Node.js, npm, or build tools needed — all dependencies load from CDN

### Setup Instructions

#### Option 1: Open Local File (No Server Needed)
```bash
# 1. Clone the repository
git clone https://github.com/Harshitgupta5290/3d-showroom.git
cd 3d-showroom

# 2. Simply open in browser
open index.html
# OR in Linux:
xdg-open index.html
```

#### Option 2: Use a Local Server (Recommended)
> **Why?** Browsers block webcam access for `file://` URLs. A local server resolves this.

```bash
# Using Node.js (npx serve)
npx serve .
# Visit: http://localhost:3000

# OR using Python 3
python -m http.server 8000
# Visit: http://localhost:8000

# OR using Python 2
python -m SimpleHTTPServer 8000
# Visit: http://localhost:8000
```

---

## 📁 Project Structure

```
3d-showroom/
├── index.html          # Single-file app (HTML + CSS + JavaScript)
├── README.md           # Documentation (this file)
└── .git/               # Version control
```

**Note:** All application logic is self-contained in `index.html` (~2000 lines). No external files needed. Libraries load via CDN at runtime.

---

## 🎮 How to Use

### Getting Started
1. **Allow Camera Access** — Grant webcam permissions when prompted
2. **Show Your Hand** — Position your hand(s) in front of the camera
3. **Interact** — Open/close your hand to expand/contract the particle cloud

### Controls

#### Hand Gestures
- **Open Hand** → Particle cloud expands (max size)
- **Closed Fist** → Particle cloud contracts (min size)
- **Two Hands** → Both hands influence the same particle cloud

#### Keyboard Shortcuts
| Key | Action |
|---|---|
| `1` - `6` | Switch between particle templates (Fireworks, Heart, Flower, Saturn, Buddha, Nebula) |
| `C` | Toggle color picker open/close |
| `R` | Reset camera to default view |
| `SPACE` | Pause/resume particles |
| `M` | Mute/unmute console logs |
| `?` | Show keyboard shortcuts (if implemented) |

#### Mouse/Touch
- **Click + Drag** → Rotate and zoom the 3D scene
- **Scroll Wheel** → Zoom in/out
- **Color Button** → Click to pick a new particle color

### Tips for Best Experience
1. **Lighting** — Use good lighting on your hand for accurate detection
2. **Distance** — Keep hand 12-24 inches from camera
3. **Speed** — Move hands slowly for smooth particle transitions
4. **Browser** — Use Chrome/Edge for best performance

---

## 🐛 Troubleshooting

### Camera Won't Start / "Camera Permission Denied"
- **Solution 1:** Grant camera permission in browser settings (check address bar)
- **Solution 2:** Use a local server instead of `file://` URLs
  ```bash
  npx serve .  # Then visit http://localhost:3000
  ```
- **Solution 3:** Check browser privacy settings (Chrome > Settings > Privacy > Camera)
- **Solution 4:** Try a different browser (Chrome works best)

### Hand Not Detected / Tracking Stutters
- **Check lighting** — Ensure good ambient light on your hand
- **Check distance** — Hand should be 12-24 inches from camera
- **Check performance** — Close other heavy applications
- **Use Chrome** — Chrome has best WebGL + MediaPipe performance
- **Check camera feed** — Verify camera is working in other apps

### Laggy Performance / Low FPS
- **Reduce particles** — Edit `index.html`, find `PARTICLE_COUNT = 15000` and lower the value
- **Close other tabs** — Free up GPU resources
- **Try HD resolution** — Some GPUs handle HD better than 4K
- **Update drivers** — Update graphics card drivers
- **Use Chrome** — Generally fastest browser for WebGL

### "WebGL Not Supported" Error
- **Solution:** Use a modern browser (Chrome, Firefox, Edge, Safari 15+)
- **Check:** Visit [WebGL Checker](https://www.khronos.org/webgl/wiki/Getting_Started)
- **Alt:** Use an older device or cloud-based solutions

### Colors Not Changing / Glowing Effect Disabled
- **Full Screen** — Maximize browser window for best visual effect
- **Dark Room** — Colors look better against dark backgrounds
- **Refresh** — Hard refresh page (`Ctrl+Shift+R` or `Cmd+Shift+R`)

### Mobile App Crashes or Freezes
- **Use landscape mode** — Better for hand visibility
- **Close background apps** — Free up RAM
- **Use Chrome/Safari** — Best performance on mobile
- **Check device temp** — Phone may throttle if too hot

---

## 📚 How It Works

### Hand Detection Pipeline
1. Camera feed → MediaPipe Hands → 21 hand landmarks per hand
2. Landmarks include: palm, fingers, knuckles, fingertips
3. Hand "openness" calculated from finger distance to palm
4. Openness value (0–1) mapped to particle scale

### Particle Morphing
1. Target shape generated based on selected template (Heart, Nebula, etc.)
2. Each particle interpolates from current position → target position
3. Lerp factor: `0.05` for smooth, fluid motion (adjustable)
4. As hand opens → particles spread; as hand closes → particles contract

### 3D Rendering
- **Engine:** Three.js WebGL
- **Geometry:** BufferGeometry with 15,000 Point sprites
- **Blending:** AdditiveBlending for neon glow effect
- **Fog:** Exponential fog scale ~6–15 units
- **Camera:** Perspective camera with OrbitControls

---

## 🤝 Contributing

We welcome contributions! Whether it's bug fixes, new features, or documentation improvements.

### How to Contribute
1. **Fork** the repository
2. **Create a branch** for your feature: `git checkout -b feature/your-feature-name`
3. **Make changes** to `index.html` (or create new files if helpful)
4. **Test thoroughly** — Especially hand tracking and particle morphing
5. **Commit** with clear messages: `git commit -m "Add: new Saturn ring effects"`
6. **Push** to your fork: `git push origin feature/your-feature-name`
7. **Open a Pull Request** with a description of your changes

### Contribution Ideas
- [ ] New particle shape templates (Cube, Donut, DNA Helix, etc.)
- [ ] Hand pose recognition (thumbs up, peace sign, etc.)
- [ ] Sound/music visualization modes
- [ ] Performance optimizations
- [ ] Mobile touch gesture improvements
- [ ] Multiplayer hand tracking (WebSocket)
- [ ] Recording/export particle animations as video
- [ ] Dark/Light theme toggle
- [ ] Accessibility improvements (keyboard-only mode)

### Code Style
- Use **ES6+ syntax** and **semantic HTML5**
- Keep code **self-documented** with clear variable names
- Add **comments** for complex math (e.g., particle morphing, hand calculation)
- Test on **Chrome, Firefox, Safari, and Edge**

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

### Summary
- ✅ Free for personal and commercial use
- ✅ Modify and distribute freely
- ✅ Include license and copyright notice

---

## 🎓 Resources & References

### Learning Materials
- [Three.js Documentation](https://threejs.org/docs/)
- [MediaPipe Hands Overview](https://google.github.io/mediapipe/solutions/hands)
- [WebGL Concepts](https://learnopengl.com/) (Graphics fundamentals)
- [Parametric Surfaces](https://en.wikipedia.org/wiki/Parametric_surface) (Math behind shapes)

### Useful Tools
- [Free CDN Links](https://cdnjs.com) — Hosting for Three.js, MediaPipe libraries
- [Shader Toy](https://www.shadertoy.com/) — Inspiration for particle effects
- [Babylon.js Playground](https://www.babylonjs-playground.com/) — Alternative 3D framework

---

## 💡 Tips & Best Practices

### Performance Optimization
- **Reduce particle count** for slower devices (change `PARTICLE_COUNT`)
- **Lower camera FPS** in MediaPipe settings if CPU-bound
- **Disable fog** for marginal performance gains (edit shader)
- **Use hardware acceleration** enabled in browser settings

### Visual Improvements
- Export screenshots via THREE.js renderer capture
- Use orbit controls in a controlled manner (avoids motion sickness)
- Adjust color picker brightness for better visual pop

### Customization Examples
```javascript
// Edit these values in index.html to customize:
const PARTICLE_COUNT = 15000;        // Reduce to 8000 for slow devices
const MORPH_SPEED = 0.05;            // Higher = faster morphing (0.1)
const CAMERA_AUTO_ROTATE = true;     // Auto-rotate when no hands
const FOG_FAR = 15;                  // Adjust fog distance
```

---

## 🚨 Known Issues & Limitations

- **Two-hand Input** — Currently averages both hands into one control (future: independent control)
- **Low Light** — Hand detection fails in very dim environments
- **Partial Hand** — If hand is cut off by camera edge, detection degrades
- **Mobile Performance** — Some older devices may struggle with 15K particles
- **Chrome Only** — Best experience on Chrome/Edge; Firefox/Safari slightly slower

**Report Issues:** Please open a GitHub issue with:
- Browser & version
- Device specs (GPU, CPU)
- Error messages (browser console: F12)
- Screenshots/video of the problem

---

## 🎯 Roadmap

### Planned Features (v2.0)
- [ ] Hand pose recognition (gesture library)
- [ ] Multi-user support (WebSocket multiplayer)
- [ ] AR/VR mode integration
- [ ] Custom shape uploader
- [ ] Particle trail effects
- [ ] Sound-reactive visualizer
- [ ] Recording & GIF export
- [ ] Mobile app (React Native / Flutter)

### Community Requests
- Suggest features in GitHub Discussions!

---

## 📞 Contact & Support

- **Issues & Bug Reports:** [GitHub Issues](https://github.com/Harshitgupta5290/3d-showroom/issues)
- **Discussions & Ideas:** [GitHub Discussions](https://github.com/Harshitgupta5290/3d-showroom/discussions)
- **Email:** [Your Email Here]

---

## 🙏 Acknowledgments

- **Google MediaPipe Team** — For the amazing hand-tracking ML model
- **Three.js Community** — For the incredible 3D graphics library
- **Inspired by:** {Inspiration sources, if any}

---

**Made with ❤️ by [Harshit Gupta](https://github.com/Harshitgupta5290)** | [Star ⭐ if you found this useful!](https://github.com/Harshitgupta5290/3d-showroom)

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
