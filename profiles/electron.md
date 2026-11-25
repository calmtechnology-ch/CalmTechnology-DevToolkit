# Technical Profile: Desktop Electron Applications

## 1. Security Architecture & Process Isolation (MANDATORY)
Electron combines Node.js and Chromium. If misconfigured, remote code execution (RCE) vulnerabilities can arise from untrusted content. The following security settings are **non-negotiable** for all Electron applications:

```javascript
// BrowserWindow configuration
const mainWindow = new BrowserWindow({
    width: 1200,
    height: 800,
    webPreferences: {
        nodeIntegration: false,        // MANDATORY: Never grant renderer access to Node.js APIs
        contextIsolation: true,         // MANDATORY: Isolate context between preload and webpage
        sandbox: true,                  // MANDATORY: Enable Chromium OS-level sandboxing
        enableRemoteModule: false,      // MANDATORY: Disable deprecated remote module
        preload: path.join(__dirname, 'preload.js')
    }
});
```

---

## 2. Process Separation & Responsibilities

```mermaid
flowchart TD
    MAIN[Main Process (Node.js)] -->|IPC Bridge (contextBridge)| PRELOAD[Preload Script]
    PRELOAD -->|Exposed Safe API| RENDERER[Renderer Process (Chromium UI)]
    RENDERER -->|ipcRenderer.invoke| PRELOAD
    PRELOAD -->|ipcRenderer.send| MAIN
```

### Main Process
- Manages native OS windows, application lifecycle, file system access, and native menus.
- Executes privileged operations (e.g., spawning child processes, file system I/O, hardware communication).
- Validates all incoming arguments from IPC requests before execution.

### Preload Script
- Bridges the Main and Renderer processes using `contextBridge.exposeInMainWorld()`.
- Exposes only explicit, typed, minimal functions to the renderer window.
- Never exposes raw `ipcRenderer` or EventEmitter primitives directly to `window`.

```javascript
// preload.js
const { contextBridge, ipcRenderer } = require('electron');

contextBridge.exposeInMainWorld('electronAPI', {
    loadProjectState: () => ipcRenderer.invoke('project:load-state'),
    saveProjectState: (state) => ipcRenderer.invoke('project:save-state', state),
    onHardwareStatus: (callback) => ipcRenderer.on('hardware:status', (_event, value) => callback(value))
});
```

### Renderer Process
- Pure UI view layer (HTML, CSS, React, Vue, or Vanilla JS).
- Interacts with system services strictly through `window.electronAPI`.

---

## 3. Safe IPC Protocols
- Use `ipcMain.handle` and `ipcRenderer.invoke` for bidirectional request-response patterns.
- Validate types, boundaries, and paths in Main before touching the filesystem.
- Guard against Path Traversal: never allow renderer to pass raw file paths that navigate outside the designated workspace.

---

## 4. Packaging & Multi-Platform Delivery
- Standard packaging tool: `electron-builder`.
- Code signing configured for Windows (Authenticode), macOS (Developer ID + Notarization), and Linux.
- Automatic updates handled via verified cryptographic signatures (`electron-updater`).
