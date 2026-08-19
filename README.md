<div align="center">

# 🐧 K Terminal — KNI Linux 1.0

**A lightweight, pure-black browser Linux terminal running a real x86 Linux kernel in WebAssembly.**

![License](https://img.shields.io/badge/License-MIT-brightgreen.svg)
![Kernel](https://img.shields.io/badge/Linux_Kernel-4.15.7-blue.svg)
![Architecture](https://img.shields.io/badge/Architecture-x86_i686-orange.svg)
![Runtime](https://img.shields.io/badge/Runtime-WebAssembly-purple.svg)

---

</div>

## 🌟 Overview

**K Terminal** is a custom web-based operating system shell authored by **Niranjan Kumar K**. Powered by the **v86** x86 emulator and **xterm.js**, K Terminal runs a genuine **Linux 4.15.7 kernel** inside the browser's WebAssembly memory runtime.

It features a customized userspace presentation—**KNI Linux 1.0**—stripping away standard distribution branding while preserving 100% real Linux kernel execution, process tree management, virtual hardware emulation, and 9P filesystem integration.

---

## ✨ Features

- **🚀 Real Linux Kernel**: Operates an authentic 32-bit x86 Linux kernel (`4.15.7`) inside WebAssembly.
- **🎨 Minimalist Pure Black UI**: Clean full-screen (`100vw` × `100vh`) terminal styled with pure black background (`#000000`) and bright green (`#39FF14`) / cyan accents.
- **🐧 KNI Linux Identity**: Custom system release profiles configured in `/etc/os-release`, `/etc/issue`, and `/etc/hostname`.
- **💻 Dynamic Shell Prompt**: Multi-colored dynamic prompt format:
  - **Regular User:** `[[ k : /path ]] $`
  - **Root User:** `[[ k : /path ]] #`
- **📁 9P Filesystem Mounts**: Integrated browser Virtual Filesystem mounted at `/mnt`.
- **👤 Standard Linux User Management**: Create and switch user accounts inside Linux natively using standard commands (`adduser`).
- **📱 Responsive Auto-Fit**: Dynamically resizes the xterm viewport upon browser window updates.

---

## 🛠️ System Requirements & Architecture

- **Emulator Engine**: `v86` (Virtual x86 in Wasm/JS)
- **BIOS**: SeaBIOS + VGABIOS
- **Terminal Emulator**: xterm.js v3
- **Virtual Memory**: 32MB RAM
- **Console Interface**: Serial TTY (`ttyS0`)

---

## 🚀 Quick Start

### 1. Clone the Repository
```bash
git clone https://github.com/hacker1514/linux.git
cd linux
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Download VM Binaries
```bash
npm run download-binaries
```

### 4. Build the Web Distribution
```bash
npm run build:pages
```

### 5. Launch Local Web Server
```bash
npx serve dist
```
Open `http://localhost:3000` in your web browser.

---

## 🧪 Real Linux Verification Commands

Inside K Terminal, test standard Linux guest commands:

| Command | Description | Example Output |
| :--- | :--- | :--- |
| `uname -a` | Print kernel details | `Linux kni-linux 4.15.7 #2 i686 GNU/Linux` |
| `cat /etc/os-release` | View KNI Linux identity | `NAME="KNI Linux"`, `VERSION="1.0"` |
| `whoami` | Print active user | `root` (or created user) |
| `id` | Show UID/GID numbers | `uid=0(root) gid=0(root)` |
| `pwd` | Show working directory | `/` (or `/home/user`) |
| `ps` | Display process tree | Active Linux PID processes |
| `mount` | Show mounted filesystems | Root `/` and `/mnt` 9P mounts |

---

## 🌐 Publishing / Deployment

### Deploy to Netlify / Vercel
1. Run `npm run build:pages`.
2. Upload the generated `dist/` directory or connect your git repository with:
   - **Build Command:** `npm run build:pages`
   - **Publish Directory:** `dist`

### Deploy to GitHub Pages
1. Build for static host:
   ```bash
   npm run build:pages
   ```
2. Push `dist/` branch to `gh-pages`:
   ```bash
   git add dist -f
   git commit -m "Deploy K Terminal v1.0"
   git subtree push --prefix dist origin gh-pages
   ```
3. Enable GitHub Pages in your repository settings (**Settings -> Pages -> gh-pages branch**).

---

## 📜 Available NPM Scripts

| Script | Description |
| :--- | :--- |
| `npm run build` | Build development bundle into `dist/` |
| `npm run build:pages` | Build production bundle for static hosting |
| `npm run download-binaries` | Fetch `v86-linux.iso`, `seabios.bin`, `vgabios.bin` into `dist/bin/` |
| `npm test` | Run ESLint syntax and code quality checks |

---

## 📄 License

Distributed under the **MIT License**.

Developed by **Niranjan Kumar K**.
