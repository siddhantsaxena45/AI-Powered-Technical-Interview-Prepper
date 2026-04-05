# Downloadable Desktop & PWA Transformation Plan

To satisfy the requirement of making this an "industry-grade downloadable app" without requiring users to manually set up Node, MongoDB, or Ollama, I will implement a dual-layer distribution strategy.

## 1. Electron.js Desktop Wrapper
I will wrap the React frontend and Node.js backend into an **Electron Desktop Application** (`.exe` for Windows, `.app` for Mac).

### **Smarter AI Handling (Cloud vs. Local)**
- **Problem:** Bundling Ollama and 4GB models into a download is impractical (~5GB installer).
- **Solution:** I will implement an **API Switching Logic**. 
    - The desktop app will default to a **Cloud API** (Optional) so it's a small download.
    - If the user *has* Ollama locally, the app will automatically detect and use it for privacy.

## 2. PWA (Progressive Web App) Support
I will add a `manifest.json` and a Service Worker to the React frontend.
- **Result:** Users can visit the website and click **"Install App"** in their browser address bar. 
- **Effect:** The app lives in their Dock/Start Menu and runs in its own window, feeling like a native application without any download.

## 3. Implementation Steps

### **Phase 1: Electron Configuration**
- Install `electron` and `electron-builder`.
- Create `main.js` to manage the app windows and lifecycle.
- Update `package.json` with build scripts for various OS targets.

### **Phase 2: PWA Integration**
- Generate professional icons for all devices.
- Create `manifest.json` (defines app name, theme color, icons).
- Implement a basic Service Worker for offline "Waiting Room" support.

### **Phase 4: Configuration Refactor**
- Update `.env` handling so the app can easily switch between the local developer stack and a production-ready Cloud API.

## User Review Required
> [!IMPORTANT]
> **AI Connectivity:** To keep the installer "light" (~80MB), do you want the downloadable app to connect to a **Central Cloud API** for the AI (Mistral/Whisper), or do you want me to provide a "Full Offline" version (which will be a very large multi-gigabyte download)?

## Open Questions
- Do you want an automated "One-Click Installer" specifically for Windows?
- Should the app launch automatically on system startup? (Common for professional proctoring tools).
