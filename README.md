<div align="center">

# 📦 3D Bin Packer — Pack Master

**An interactive, browser-based 3D bin-packing visualizer.**  
Add boxes, hit **Pack**, and watch them fill a container in real time — no install required.

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-6c63ff?style=for-the-badge&logo=github)](https://ormosco.github.io/3d-bin/)

</div>

---

## ✨ Features

| Feature | Details |
|---|---|
| **3D Visualization** | Interactive WebGL scene powered by [Three.js](https://threejs.org/) |
| **Guillotine Algorithm** | Fast, deterministic bin-packing; items sorted by volume descending |
| **Live Stats** | Packed / Unpacked counts and % volume utilization |
| **Custom Items** | Name, W × H × D dimensions, and per-item color picker |
| **Paginated Item List** | Handles large item sets without cluttering the UI |
| **Responsive Design** | Works on desktop and mobile (stacked layout below 580 px) |
| **Zero Dependencies** | Pure HTML + CSS + JavaScript; Three.js loaded via CDN |
| **One-file Deployment** | Single `index.html` — drop it anywhere and it just works |

---

## 🚀 Live Demo

👉 **[https://ormosco.github.io/3d-bin/](https://ormosco.github.io/3d-bin/)**

Deployed automatically to GitHub Pages on every push to `main`.

---

## 🖥️ How to Run Locally

No build step needed.

```bash
# clone and open
git clone https://github.com/OrMosco/3d-bin.git
cd 3d-bin
# open index.html in your browser
open index.html          # macOS
xdg-open index.html      # Linux
start index.html         # Windows
```

> **Note:** Some browsers restrict ES module imports from `file://`. If the 3D view doesn't load, serve the file over HTTP instead:
> ```bash
> npx serve .
> # then visit http://localhost:3000
> ```

---

## 🧠 Algorithm — Guillotine Bin Packing

The packing logic lives entirely in `index.html` (the `packItems` function).

1. **Sort** items by volume, largest first.
2. Maintain a list of **free rectangular spaces**, starting with the whole container.
3. For each item, find the **first space** that fits it (First-Fit Decreasing strategy).
4. **Split** the used space into up to three new sub-spaces (top, right, back — Guillotine split).
5. Items that never find a fit are marked **unpacked** (shown with ✗ in the list).

This gives O(n²) worst-case complexity — perfectly adequate for the interactive item counts this tool targets.

---

## 🗂️ Project Structure

```
3d-bin/
├── index.html          # Entire application (HTML + CSS + JS)
└── .github/
    └── workflows/
        └── deploy.yml  # GitHub Actions — deploy to GitHub Pages
```

---

## 🛠️ Tech Stack

- **[Three.js](https://threejs.org/) v0.160** — WebGL rendering, OrbitControls
- **Vanilla JS (ES Modules)** — no framework, no bundler
- **CSS Custom Properties** — dark-mode design system built with variables
- **GitHub Actions** — CI/CD pipeline for GitHub Pages deployment

---

## 📸 Screenshots

> *Launch the [live demo](https://ormosco.github.io/3d-bin/) to see it in action.*

The app opens with five pre-loaded demo boxes.  
Click **▶ Pack** to place them all inside the container and inspect utilization stats in the sidebar.  
Use **drag** to orbit, **scroll** to zoom, and **right-drag** to pan the 3D view.

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
