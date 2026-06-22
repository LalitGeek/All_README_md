<div align="center">

```
███╗   ██╗███████╗██╗  ██╗████████╗   ██╗███████╗
████╗  ██║██╔════╝╚██╗██╔╝╚══██╔══╝   ██║██╔════╝
██╔██╗ ██║█████╗   ╚███╔╝    ██║      ██║███████╗
██║╚██╗██║██╔══╝   ██╔██╗    ██║      ██║╚════██║
██║ ╚████║███████╗██╔╝ ██╗   ██║   ██╗██║███████║
╚═╝  ╚═══╝╚══════╝╚═╝  ╚═╝   ╚═╝   ╚═╝╚═╝╚══════╝
```

### ▲ Next.js — Quick Command Reference

![Node.js](https://img.shields.io/badge/Node.js-LTS-339933?style=flat-square&logo=node.js&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-15+-000000?style=flat-square&logo=next.js&logoColor=white)
![React](https://img.shields.io/badge/React-19+-61DAFB?style=flat-square&logo=react&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)
![Made by](https://img.shields.io/badge/Made%20by-Lalit%20Tomer-blueviolet?style=flat-square)

</div>

---

## 🖥️ Environment Check

> Before anything else — verify your tools are ready.

```bash
# Check Node.js version (Next.js 15 requires Node 18.18+)
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

## 🚀 Create a New Next.js App

### ⚡ Option 1 — Automatic Setup (Recommended)

> Interactive CLI. Picks App Router, Tailwind, TypeScript — all in one step.

```bash
# Step 1 — Scaffold the project
npx create-next-app@latest my-next-app

# Step 2 — Enter the project directory
cd my-next-app

# Step 3 — Launch dev server
npm run dev
```

**CLI Prompts:**
```
✔ Would you like to use TypeScript? › Yes
✔ Would you like to use ESLint? › Yes
✔ Would you like to use Tailwind CSS? › Yes
✔ Would you like your code inside a `src/` directory? › No
✔ Would you like to use App Router? (recommended) › Yes
✔ Would you like to use Turbopack for `next dev`? › Yes
✔ Would you like to customize the import alias? › No
```

**Dev server output:**
```
  ▲ Next.js 15.x.x (Turbopack)
  - Local:        http://localhost:3000
  - Environments: .env.local
```

---

### 🐢 Option 2 — Manual / Non-Interactive

> Skip prompts. Scaffold with all defaults in one shot.

```bash
npx create-next-app@latest my-next-app --typescript --tailwind --eslint --app --no-src-dir --no-import-alias
cd my-next-app
npm run dev
```

---

## 📦 Install Popular Packages

### 🔀 Next.js Navigation — Built-in (App Router)

> No extra install needed. Use `next/link` and `next/navigation` directly.

```bash
# Already included — import directly in your components
# import Link from 'next/link'
# import { useRouter } from 'next/navigation'
```

### 🌐 Axios — HTTP Requests

```bash
npm install axios
```

### 🗄️ Prisma — Database ORM

```bash
npm install prisma @prisma/client
npx prisma init
```

### 🔐 NextAuth.js — Authentication

```bash
npm install next-auth
```

### 💨 Tailwind CSS — Utility-first CSS (if not added during setup)

```bash
npm install tailwindcss @tailwindcss/postcss postcss
```

### 🎨 shadcn/ui — Component Library

```bash
npx shadcn@latest init
npx shadcn@latest add button
```

---

## 🏗️ Build & Preview

### 📦 Production Build

```bash
npm run build
```

```
▲ Next.js 15.x.x

   Creating an optimized production build ...
 ✓ Compiled successfully
 ✓ Linting and checking validity of types
 ✓ Collecting page data
 ✓ Generating static pages (5/5)
 ✓ Collecting build traces
 ✓ Finalizing page optimization

Route (app)                              Size     First Load JS
┌ ○ /                                    5.2 kB        92.1 kB
└ ○ /favicon.ico                         0 B                0 B
```

> Output goes to the `.next/` folder — ready to deploy.

### 👁️ Start Production Server Locally

```bash
npm start
```

```
  ▲ Next.js 15.x.x
  - Local:        http://localhost:3000
```

---

## 🧹 Troubleshooting — Clean Reinstall

> When things break, nuke and reinstall.

```bash
# Remove build cache, modules, and lock file
rm -rf .next node_modules package-lock.json

# Fresh install
npm install
```

---

## ⚡ All Commands at a Glance

```bash
node -v                                                              # Check Node version
npm -v                                                               # Check npm version

npx create-next-app@latest my-next-app                               # Create Next.js app (interactive)
cd my-next-app                                                       # Enter project folder
npm run dev                                                          # Start dev server (Turbopack)

npm install axios                                                    # Axios HTTP client
npm install prisma @prisma/client && npx prisma init                 # Prisma ORM + DB setup
npm install next-auth                                                # NextAuth.js authentication
npm install tailwindcss @tailwindcss/postcss postcss                 # Tailwind CSS (manual)
npx shadcn@latest init                                               # shadcn/ui component library

npm run build                                                        # Production build
npm start                                                            # Start production server

rm -rf .next node_modules package-lock.json && npm install           # Clean reinstall

npx create-next-app@latest my-next-app --typescript --tailwind \
  --eslint --app --no-src-dir --no-import-alias                      # Non-interactive scaffold
```

---

## 🗂️ Project Structure (Next.js App Router)

```
my-next-app/
├── 📁 public/              → Static assets (favicon, images, fonts)
├── 📁 app/
│   ├── 📄 layout.tsx        → Root layout (wraps all pages)
│   ├── 📄 page.tsx          → Home route  (/  →  app/page.tsx)
│   ├── 📄 globals.css       → Global styles
│   ├── 📁 about/
│   │   └── 📄 page.tsx      → /about route
│   └── 📁 api/
│       └── 📁 hello/
│           └── 📄 route.ts  → API endpoint  /api/hello
├── 📁 components/           → Reusable UI components
├── 📁 lib/                  → Utilities, DB clients, helpers
├── 📄 next.config.ts        → Next.js configuration
├── 📄 package.json          → Dependencies & scripts
├── 📄 tailwind.config.ts    → Tailwind configuration
├── 📄 tsconfig.json         → TypeScript configuration
└── 📄 .gitignore
```

---

## 🧠 App Router — Key Conventions

| File | Purpose |
|------|---------|
| `page.tsx` | Defines a route — only this file is publicly accessible |
| `layout.tsx` | Wraps children; persists across navigations |
| `loading.tsx` | Automatic loading UI (Suspense boundary) |
| `error.tsx` | Error boundary for the segment |
| `not-found.tsx` | Rendered when `notFound()` is called |
| `route.ts` | API endpoint — handles `GET`, `POST`, etc. |

---

## 🖥️ Server vs Client Components

```tsx
// ✅ Server Component (default — no directive needed)
// Runs on the server. Can fetch data, access DB, read env vars.
export default async function Page() {
  const data = await fetch('https://api.example.com/data');
  return <main>{/* render */}</main>;
}

// ✅ Client Component (add directive at top)
// Runs in the browser. Can use useState, useEffect, event handlers.
"use client";
import { useState } from "react";
export default function Counter() {
  const [count, setCount] = useState(0);
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

---

## 💡 Tips

| Tip | Details |
|-----|---------|
| ⚡ Turbopack | Default dev bundler in Next.js 15 — significantly faster than Webpack |
| 🌿 `.env.local` | Prefix with `NEXT_PUBLIC_` to expose vars to the browser |
| 📦 `.next/` | Build output folder — never commit this to Git |
| 🖥️ Server First | Default to Server Components; add `"use client"` only when needed |
| 🔗 `next/image` | Always use `<Image>` over `<img>` — auto-optimizes and lazy-loads |
| 🚫 Secrets | Never expose secret keys — only `NEXT_PUBLIC_` vars reach the client |
| 📁 Colocation | Keep components, tests, and styles next to the routes that use them |

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

![Footer](https://img.shields.io/badge/Popup%20Core%20Technology-Gurgaon-0a0a0a?style=for-the-badge&logo=next.js&logoColor=white)

</div>
