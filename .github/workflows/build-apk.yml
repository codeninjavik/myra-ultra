<div align="center">

<img src="docs/images/myra-logo.png" alt="MYRA logo" width="120" />

# MYRA ULTRA

**Your personal AI assistant: voice, vision, PC control and an AI website builder.**
*Speak to MYRA, she listens, acts, and can even build and deploy a website for you.*

[![License: MIT](https://img.shields.io/badge/License-MIT-red.svg)](LICENSE)
![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Platforms](https://img.shields.io/badge/Windows%20%7C%20Linux%20%7C%20Termux-supported-lightgrey)
![Powered by](https://img.shields.io/badge/AI-Google%20Gemini-4285F4)

<img src="docs/images/splash.jpg" alt="MYRA OS splash screen" width="860" />

</div>

---

## Screenshots

<div align="center">

<img src="docs/images/myra-ui.png" alt="MYRA ULTRA main window" width="900" />

*Main window: navigation, live system stats, quick tools, recent activity and the "Ask me anything" voice/chat bar.*

</div>

> The image above is the UI reference design that the app is built from. Real screenshots from your own setup are welcome. Add them to `docs/images/` and open a PR.

## Features

| Area | What MYRA can do |
|---|---|
| **Voice** | Hands-free conversation through Gemini Live in 148+ languages (Hindi, Hinglish, English and more) |
| **Chat** | Text chat with attachments and images |
| **PC control** | Open apps, screenshots, clipboard, volume, brightness, lock/shutdown, window management |
| **Vision** | Camera vision and screen sharing, so MYRA can see what you see |
| **Files and documents** | Work with PDF, Word, Excel and PowerPoint files, QR codes, OCR |
| **Web and media** | Google/YouTube search, Spotify control, WhatsApp messages, downloads |
| **System monitor** | Live CPU, RAM, storage and battery |
| **Floating orb and glow** | Always-on-top mini assistant and edge-glow listening indicator |
| **MYRA Coder** | AI website builder: say *"gaming website banao dark theme ke saath"* and MYRA builds it, then deploys it to GitHub/Vercel |
| **Face authentication** | Optional face unlock |

## Repository layout

```
MYRA_ULTRA/
├── MYRA_ULTRA_APP/        # Windows desktop app (PyQt5), the main project
│   ├── aria.py            # main window / entry point
│   ├── Main_normal.py     # normal boot flow
│   ├── aria_modules/      # face auth, activation, cloud DB, tools, assets
│   ├── myra_coder/        # Node.js + TypeScript AI coding agent
│   ├── website_builder/   # Python "WebForge" website pipeline + deploy
│   ├── myra/              # pip-installable CLI (myra, myra-reset, myra-upgrade)
│   ├── backend/           # FastAPI licensing server (server-side only)
│   └── admin_and_build_tools/  # developer-only tooling (keygen, EXE build)
├── myra-linux/            # Linux desktop build (same UI as Windows)
├── myra-termux/           # Android (Termux) and Linux CLI/web UI, zero dependencies
└── docs/images/           # README images
```

## Quick start (Windows, run from source)

### 1. Prerequisites

- **Windows 10/11**
- **Python 3.10 – 3.12** ([python.org](https://www.python.org/downloads/)), tick *Add Python to PATH*
- **Node.js 18+** ([nodejs.org](https://nodejs.org)), only needed for MYRA Coder
- A working **microphone** (and optionally a webcam)
- A free **Gemini API key**: <https://aistudio.google.com/apikey>
- Optional: [Tesseract OCR](https://github.com/UB-Mannheim/tesseract/wiki) for text-from-image

### 2. Clone and install

```powershell
git clone https://github.com/codeninjavik/myra-ultra.git
cd myra-ultra\MYRA_ULTRA_APP

python -m venv .venv
.venv\Scripts\activate

pip install --upgrade pip
pip install -r requirements.txt
```

> `pyaudio` sometimes fails to build on Windows. If it does, run `pip install pipwin && pipwin install pyaudio`, or install a prebuilt wheel for your Python version.

### 3. Configure your keys

Create a file named `.env` inside `MYRA_ULTRA_APP/` (it is git-ignored, never commit it):

```env
GEMINI_API_KEY=your-gemini-api-key

# Optional: only needed for the website builder's one-click deploy
GITHUB_TOKEN=your-github-token
GITHUB_USERNAME=your-github-username
VERCEL_TOKEN=your-vercel-token
```

A template is available at `MYRA_ULTRA_APP/website_builder/.env.example`. You can also paste the Gemini key into the app's API key dialog on first launch.

### 4. (Optional) Set up MYRA Coder, the AI website builder

```powershell
python setup_myra_coder.py
```

This runs `npm install` and compiles `myra_coder/` (TypeScript) and writes `~/.myra-coder/config.json`. To do it by hand:

```powershell
cd myra_coder
npm install
npm run build
```

### 5. Run MYRA

```powershell
python aria.py
```

Then try:

- *"Open Chrome"* / *"Search on Google"*
- *"Summarize this file"*
- *"Portfolio website bana mere liye"*
- *"Restaurant ka website create karo"*

The MYRA Coder panel opens automatically when you ask for a website.

### Install as a command (pip)

```powershell
cd MYRA_ULTRA_APP
pip install .
myra            # launch
myra-reset      # reset saved state
myra-upgrade    # upgrade
```

## Linux

The full desktop app with the same UI is packaged as `myra-linux`.

```bash
sudo apt install -y pipx libportaudio2 libxcb-cursor0 libxkbcommon-x11-0 libxcb-icccm4 libxcb-image0 \
  libxcb-keysyms1 libxcb-render-util0 libxcb-xinerama0 libgl1 libpulse0 libasound2-plugins \
  pulseaudio-utils tesseract-ocr scrot python3-tk xclip libnotify-bin playerctl brightnessctl \
  wmctrl xdotool network-manager
pipx ensurepath
pipx install myra-linux
myra-linux
```

| Command | What it does |
|---|---|
| `myra-linux` | Run MYRA (window + voice) |
| `myra-linux --background` | Run with only the floating orb |
| `myra-linux install` / `uninstall` | Turn autostart at login on / off |
| `myra-linux status` | Version, autostart, display and audio status |
| `myra-linux deps` | Install required system libraries |
| `myra-linux update` | Update to the newest version |

Needs an X11 or Wayland desktop session. Security mode and WhatsApp chat reading need Windows. To build from source see [`myra-linux/`](myra-linux/).

## Android (Termux) and Linux CLI

`myra-termux` is a zero-dependency Python package with a phone-friendly web UI (voice + chat) that opens in your browser.

```bash
pkg update && pkg install python termux-api
pip install myra-termux
myra-termux --setup        # paste your Gemini API key
myra-termux                # opens the phone UI
```

Install the **Termux:API** app (from F-Droid) for torch, SMS, calls, location and voice. SMS, calls and WhatsApp always ask for your permission first. More in [`myra-termux/README.md`](myra-termux/README.md).

## Build a Windows EXE

```powershell
pip install pyinstaller
python setup_myra_coder.py      # build the Node part first
pyinstaller MYRA_ULTRA.spec
```

The target PC needs Node.js 18+ if MYRA Coder is used.

## Licensing backend (optional, server-side only)

`MYRA_ULTRA_APP/backend/` is a FastAPI + Firebase licensing server used by the activation flow. **Never ship it to clients.**

```bash
cd MYRA_ULTRA_APP/backend
pip install -r requirements.txt
cp .env.example .env            # set GOOGLE_APPLICATION_CREDENTIALS and MYRA_ADMIN_SECRET
uvicorn main:app --host 0.0.0.0 --port 8000
```

If you fork the project you can skip the activation flow or point it at your own Firebase project (`aria_modules/firebase_connection.py`, `aria_modules/aria_login.py`).

## How the website builder works

```
Voice command
   ↓  Gemini Live speech recognition
_is_website_command() check
   ↓
MYRA Coder panel opens in the UI
   ↓
node dist/run.js --progress-file tmp.jsonl
   ↓
AI agent → tools → project files are created
   ↓  live JSON progress → Qt signals → UI updates
Done → deploy to GitHub / Vercel (WebForge)
```

`myra_coder/` is a provider-agnostic agent (Gemini, Anthropic, Ollama, OpenRouter, NVIDIA) forked from HunterCode (MIT).

## Troubleshooting

| Problem | Fix |
|---|---|
| `Node.js not found` | Install Node 18+ from <https://nodejs.org> and reopen the terminal |
| `MYRA Coder build not found` | `cd myra_coder && npm install && npm run build` |
| API key error | Check `GEMINI_API_KEY` in `.env` (no quotes or spaces) |
| `pyaudio` install fails | Use `pipwin install pyaudio` or a prebuilt wheel |
| No voice or mic input | Check Windows microphone privacy settings and the default input device |
| `ModuleNotFoundError` after `pip install .` | Reinstall with `pip install --force-reinstall .` |

## Contributing

Issues and pull requests are welcome.

1. Fork the repo and create a branch: `git checkout -b feature/my-change`
2. Match the surrounding code style (Python files mix English identifiers with Hinglish comments, which is fine)
3. Test by running the entry point you changed (`python aria.py`, `npm run build` in `myra_coder/`)
4. Open a pull request describing the change

**Never commit secrets.** `.env`, API keys and tokens must stay out of git.

## Security

If you find a vulnerability, please open a private security advisory on GitHub instead of a public issue. If you ever accidentally publish a key, revoke it immediately.

## License

Released under the [MIT License](LICENSE). MYRA Coder is based on HunterCode (MIT).

---

<div align="center">Made with ❤️ by <a href="https://github.com/codeninjavik">Vikash Kumar</a></div>
