<div align="center">

```
██████╗ ███████╗ █████╗  ██████╗████████╗    ██╗███████╗
██╔══██╗██╔════╝██╔══██╗██╔════╝╚══██╔══╝    ██║██╔════╝
██████╔╝█████╗  ███████║██║        ██║       ██║███████╗
██╔══██╗██╔══╝  ██╔══██║██║        ██║       ██║╚════██║
██║  ██║███████╗██║  ██║╚██████╗   ██║    ██╗██║███████║
╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝ ╚═════╝   ╚═╝    ╚═╝╚═╝╚══════╝
```

### ⚛️ React.js — Quick Command Reference

![Node.js](https://img.shields.io/badge/Node.js-LTS-339933?style=flat-square&logo=node.js&logoColor=white)
![React](https://img.shields.io/badge/React-18+-61DAFB?style=flat-square&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-5+-646CFF?style=flat-square&logo=vite&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)
![Made by](https://img.shields.io/badge/Made%20by-Lalit%20Tomer-blueviolet?style=flat-square)

</div>

---

## 🖥️ Environment Check

> Before anything else — verify your tools are ready.

```bash
# Check Node.js version (LTS recommended: 18.x or 20.x)
node -v

# Check npm version
npm -v
```

**Expected output:**
```
v20.11.0
10.2.4
```

---

## 🚀 Create a New React App

### ⚡ Option 1 — Vite (Recommended)

> Faster builds. Modern tooling. Zero config to get started.

```bash
# Step 1 — Scaffold the project
npm create vite@latest my-react-app -- --template react

# Step 2 — Enter the project directory
cd my-react-app

# Step 3 — Install all dependencies
npm install

# Step 4 — Launch dev server
npm run dev
```

```
  VITE v5.x.x  ready in 300ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
```

---

### 🐢 Option 2 — Create React App (Legacy)

> Slower, but widely documented. Not recommended for new projects.

```bash
npx create-react-app my-app
cd my-app
npm start
```

---

## 📦 Install Popular Packages

### 🔀 React Router — Client-side Navigation

```bash
npm install react-router-dom
```

### 🌐 Axios — HTTP Requests

```bash
npm install axios
```

### 🎨 Bootstrap — CSS Framework

```bash
npm install bootstrap
```

### 💨 Tailwind CSS — Utility-first CSS (Vite)

```bash
npm install tailwindcss @tailwindcss/vite
```

---

## 🏗️ Build & Preview

### 📦 Production Build

```bash
npm run build
```

```
✓ 42 modules transformed.
dist/index.html                  0.46 kB
dist/assets/index-Cx3k2d1s.js   142.35 kB │ gzip: 45.91 kB
✓ built in 1.84s
```

> Output goes to the `dist/` folder — ready to deploy.

### 👁️ Preview Production Build Locally

```bash
npm run preview
```

```
  ➜  Local:   http://localhost:4173/
```

---

## 🧹 Troubleshooting — Clean Reinstall

> When things break, nuke and reinstall.

```bash
# Remove node_modules and lock file
rm -rf node_modules package-lock.json

# Fresh install
npm install
```

---

## ⚡ All Commands at a Glance

```bash
node -v                                                    # Check Node version
npm -v                                                     # Check npm version

npm create vite@latest my-react-app -- --template react   # Create React app (Vite)
cd my-react-app                                            # Enter project folder
npm install                                                # Install dependencies
npm run dev                                                # Start dev server

npm install react-router-dom                               # React Router
npm install axios                                          # Axios HTTP client
npm install bootstrap                                      # Bootstrap CSS
npm install tailwindcss @tailwindcss/vite                  # Tailwind CSS

npm run build                                              # Production build
npm run preview                                            # Preview build locally

rm -rf node_modules package-lock.json && npm install       # Clean reinstall

npx create-react-app my-app                                # CRA (alternative)
cd my-app && npm start                                     # Start CRA dev server
```

---

## 🗂️ Project Structure (Vite + React)

```
my-react-app/
├── 📁 public/              → Static assets (favicon, images)
├── 📁 src/
│   ├── 📁 assets/          → Fonts, icons, images
│   ├── 📁 components/      → Reusable UI components
│   ├── 📄 App.jsx           → Root component
│   ├── 📄 main.jsx          → Entry point
│   └── 📄 index.css         → Global styles
├── 📄 index.html            → HTML shell
├── 📄 package.json          → Dependencies & scripts
├── 📄 vite.config.js        → Vite configuration
└── 📄 .gitignore
```

---

## 💡 Tips

| Tip | Details |
|-----|---------|
| 🔥 HMR | Vite's Hot Module Replacement updates instantly — no full reload |
| 🌿 `.env` | Prefix vars with `VITE_` to expose them in your app |
| 📦 `dist/` | This folder is your deployable — push to Vercel, Netlify, or S3 |
| 🧩 Components | Keep them small, focused, and in separate files |
| 🚫 Secrets | Never hardcode API keys — use environment variables |

---

<div align="center">

```
// crafted by
const author = {
  name:    "Lalit Tomer",
  org:     "Popup Core Technology",
  office:  "WeWork Cyberhub, Gurgaon",
};
```

![Footer](https://img.shields.io/badge/Popup%20Core%20Technology-Gurgaon-0a0a0a?style=for-the-badge&logo=react&logoColor=61DAFB)

</div>
