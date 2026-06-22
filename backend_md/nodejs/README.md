<div align="center">

```
███╗   ██╗ ██████╗ ██████╗ ███████╗   ██╗███████╗
████╗  ██║██╔═══██╗██╔══██╗██╔════╝   ██║██╔════╝
██╔██╗ ██║██║   ██║██║  ██║█████╗     ██║███████╗
██║╚██╗██║██║   ██║██║  ██║██╔══╝     ██║╚════██║
██║ ╚████║╚██████╔╝██████╔╝███████╗██╗██║███████║
╚═╝  ╚═══╝ ╚═════╝ ╚═════╝ ╚══════╝╚═╝╚═╝╚══════╝
```

### 🟢 Node.js — Quick Command Reference

![Node.js](https://img.shields.io/badge/Node.js-LTS-339933?style=flat-square&logo=node.js&logoColor=white)
![npm](https://img.shields.io/badge/npm-10+-CB3837?style=flat-square&logo=npm&logoColor=white)
![Express](https://img.shields.io/badge/Express-5+-000000?style=flat-square&logo=express&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)
![Made by](https://img.shields.io/badge/Made%20by-Lalit%20Tomer-blueviolet?style=flat-square)

</div>

---

## 🖥️ Environment Check

> Before anything else — verify your tools are ready.

```bash
# Check Node.js version (LTS recommended: 20.x or 22.x)
node -v

# Check npm version
npm -v

# Check npx is available
npx -v
```

**Expected output:**
```
v20.11.0
10.2.4
10.2.4
```

---

## 🚀 Initialize a New Node.js Project

### ⚡ Option 1 — Quick Init (Recommended)

> Skips all prompts. Creates `package.json` with defaults instantly.

```bash
# Step 1 — Create and enter your project folder
mkdir my-node-app && cd my-node-app

# Step 2 — Initialize with defaults (no prompts)
npm init -y

# Step 3 — Open in editor
code .
```

**Generated `package.json`:**
```json
{
  "name": "my-node-app",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

---

### 🐢 Option 2 — Interactive Init

> Answer prompts to fill in project metadata manually.

```bash
npm init
```

---

## 🟢 Run a Node.js File

```bash
# Run a JS file directly
node index.js

# Run with environment variable
NODE_ENV=production node index.js

# Run with auto-restart on file changes (Node 18+)
node --watch index.js
```

---

## 📦 Install Popular Packages

### 🚂 Express — Web Framework

```bash
npm install express
```

### 🔁 Nodemon — Auto-restart Dev Server

```bash
npm install --save-dev nodemon
```

> Add to `package.json` scripts:
```json
"scripts": {
  "dev": "nodemon index.js",
  "start": "node index.js"
}
```

### 🌐 Axios — HTTP Requests

```bash
npm install axios
```

### 🔐 dotenv — Environment Variables

```bash
npm install dotenv
```

> Usage in code:
```js
require('dotenv').config();
console.log(process.env.PORT);
```

### 🗄️ Mongoose — MongoDB ODM

```bash
npm install mongoose
```

### 🔑 jsonwebtoken — JWT Auth

```bash
npm install jsonwebtoken
```

### 🔒 bcrypt — Password Hashing

```bash
npm install bcrypt
```

### 🛡️ cors — Enable CORS

```bash
npm install cors
```

### ✅ express-validator — Input Validation

```bash
npm install express-validator
```

---

## ⚡ Minimal Express Server

```js
// index.js
const express = require('express');
const app = express();
const PORT = process.env.PORT || 3000;

app.use(express.json());

app.get('/', (req, res) => {
  res.send('Hello, World!');
});

app.listen(PORT, () => {
  console.log(`Server running at http://localhost:${PORT}`);
});
```

```bash
node index.js
# → Server running at http://localhost:3000
```

---

## 🗂️ Project Structure (Express REST API)

```
my-node-app/
├── 📁 controllers/         → Route handler logic
├── 📁 middleware/          → Auth, error handling, logging
├── 📁 models/              → Database schemas (Mongoose, etc.)
├── 📁 routes/              → Express route definitions
├── 📁 config/              → DB connection, env config
├── 📁 utils/               → Helper functions
├── 📄 index.js             → Entry point — starts the server
├── 📄 .env                 → Environment variables (never commit)
├── 📄 .env.example         → Template for env vars (safe to commit)
├── 📄 .gitignore           → Exclude node_modules, .env, dist
├── 📄 package.json         → Dependencies & scripts
└── 📄 package-lock.json    → Locked dependency tree
```

---

## 📋 npm Scripts — Common Patterns

```json
"scripts": {
  "start":    "node index.js",
  "dev":      "nodemon index.js",
  "test":     "jest",
  "lint":     "eslint .",
  "format":   "prettier --write ."
}
```

```bash
npm start          # Run production server
npm run dev        # Run dev server with auto-restart
npm test           # Run tests
npm run lint       # Lint the codebase
npm run format     # Format all files
```

---

## 📦 npm Package Management

```bash
npm install <pkg>               # Install & save to dependencies
npm install --save-dev <pkg>    # Install & save to devDependencies
npm install -g <pkg>            # Install globally
npm uninstall <pkg>             # Remove a package
npm update                      # Update all packages
npm outdated                    # List outdated packages
npm list                        # List installed packages (local)
npm list -g --depth=0           # List globally installed packages
npm audit                       # Check for vulnerabilities
npm audit fix                   # Auto-fix vulnerabilities
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
node -v                                        # Check Node version
npm -v                                         # Check npm version

mkdir my-node-app && cd my-node-app            # Create project folder
npm init -y                                    # Initialize package.json
node index.js                                  # Run a file
node --watch index.js                          # Run with auto-restart (Node 18+)

npm install express                            # Express web framework
npm install --save-dev nodemon                 # Nodemon (dev only)
npm install axios                              # HTTP client
npm install dotenv                             # Environment variables
npm install mongoose                           # MongoDB ODM
npm install jsonwebtoken bcrypt cors           # Auth + security essentials
npm install express-validator                  # Input validation

npm start                                      # Start production server
npm run dev                                    # Start dev server (nodemon)
npm test                                       # Run test suite

npm install <pkg>                              # Add dependency
npm install --save-dev <pkg>                   # Add dev dependency
npm uninstall <pkg>                            # Remove package
npm outdated                                   # Check for updates
npm audit fix                                  # Fix vulnerabilities

rm -rf node_modules package-lock.json          # Clean reinstall prep
npm install                                    # Reinstall all dependencies
```

---

## 💡 Tips

| Tip | Details |
|-----|---------|
| 🟢 `--watch` | Node 18+ has built-in file watching — use instead of nodemon for simple cases |
| 🌿 `.env` | Never commit `.env` — always add it to `.gitignore` |
| 📄 `.env.example` | Commit this with dummy values so teammates know what vars are needed |
| 🔒 `dependencies` vs `devDependencies` | Runtime packages go in `dependencies`; build/test tools go in `devDependencies` |
| 📦 `package-lock.json` | Always commit this — it locks exact versions for reproducible installs |
| 🛡️ `npm audit` | Run regularly to catch known vulnerabilities in your dependency tree |
| 🚫 Secrets | Never hardcode API keys or passwords — load them from `process.env` |
| 📁 `node_modules/` | Always in `.gitignore` — never commit it |

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

![Footer](https://img.shields.io/badge/Popup%20Core%20Technology-Gurgaon-0a0a0a?style=for-the-badge&logo=node.js&logoColor=339933)

</div>
