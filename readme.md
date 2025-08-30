# Video Call App (PeerJS + Express + Socket.IO)

A simple one-to-one / group video calling app built with **Express**, **Socket.IO**, and **PeerJS** for WebRTC peer connections. Views are rendered with **EJS**.

---

## ✨ Features
- WebRTC video/audio via **PeerJS**
- Real-time signaling with **Socket.IO**
- Room-based calls (join via URL / room id)
- Minimal server with **Express**
- EJS templates, simple styling
- Nodemon for local dev

---

## ✅ Prerequisites

- **Node.js** ≥ 18 and **npm** ≥ 9
- **PeerJS Server (global CLI)**

Install the PeerJS server CLI globally:
```bash
npm i -g peer
```

Then run a local PeerJS server (recommended port **3001**):
```bash
peerjs --port 3001
```

> **Note:**
> The global package name is `peer` (which provides the `peerjs` CLI).
> The **client** library used by your app is `peerjs` and is installed **locally** in the project.

---

## 🚀 Getting Started

### 1) Clone and install
```bash
git clone https://github.com/ragini-pandey/video-call-app-peerjs.git
cd video-call-app-peerjs
npm install
```

### 2) Start PeerJS server (in a separate terminal)
```bash
peerjs --port 3001
```
Optional flags you may find handy:
```bash
peerjs --port 3001 --path /peerjs --key peerjs
```

### 3) Start the app
Development (auto-reload):
```bash
npm run dev
```
Production:
```bash
npm start
```

By default the app will run on **http://localhost:3000** (unless your `server.js` specifies a different port).

---

## 🔧 Project Scripts

Your `package.json` already includes:
```json
"scripts": {
  "dev": "nodemon server.js",
  "start": "node server.js"
}
```

---

## 🧩 Tech Stack

- **Server:** Node.js, Express 5, Socket.IO
- **WebRTC:** PeerJS (client) + PeerJS Server (CLI)
- **Views:** EJS
- **Dev tools:** Nodemon

Dependencies snapshot:
```json
"dependencies": {
  "ejs": "^3.1.10",
  "express": "^5.1.0",
  "socket.io": "^4.8.1",
  "uuid": "^11.1.0"
},
"devDependencies": {
  "nodemon": "^3.1.10"
}
```

---

## 🧪 How to Test Locally

1. Open **two terminals**:
   - **Terminal A:** `peerjs --port 3001`
   - **Terminal B:** `npm run dev`
2. Open **http://localhost:3000** in **two browser windows** (or share the room URL).
3. Allow camera/mic permissions.

---

## 🛠️ Troubleshooting

- **“Peer connection fails / no video appears”**
  - Ensure the PeerJS server is running and reachable at the configured `host:port/path`.
  - Check that your client PeerJS init uses the same `port`/`path`.

- **Running on a different machine / network**
  - Start PeerJS server with a host that’s reachable (e.g., `0.0.0.0`) and configure firewall rules.
  - Update the client PeerJS options to point to your machine IP/domain.

- **HTTPS required (production)**
  - Browsers often require HTTPS for getUserMedia/WebRTC.
  - Use a reverse proxy (Nginx/Caddy) or a hosting provider that terminates TLS.
  - Consider TURN servers for NAT traversal in production.

---

## 📦 Deployment Notes

- Run PeerJS server as a **separate process** (or container) alongside your Node app.
- Expose the PeerJS port (e.g., **3001**) and update client config accordingly.
- Use a process manager (PM2, systemd, Docker) to keep both services running.
