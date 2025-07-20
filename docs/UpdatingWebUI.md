# 🌐 Advanced Guide: Updating the Web UI for n3wbsWiFiDucky

The firmware hosts a self-contained web interface served directly from flash memory. This interface provides control over payloads, settings, and interactive command execution — all styled and delivered using embedded HTML, CSS, and JavaScript.

This guide is intended for developers and advanced users who want to modify or extend the UI with deeper control, logic, and styling.

---

## 📁 Web UI Source and Build Structure

| Directory    | Purpose                                                      |
| ------------ | ------------------------------------------------------------ |
| `web_files/` | Source HTML/CSS/JS assets (editable)                         |
| `src/web/`   | Auto-generated `.h` files from web\_files (used in firmware) |
| `tools/`     | Scripts to convert files to/from headers                     |

---

## 🧠 JavaScript Runtime API

The web interface communicates with the firmware over HTTP endpoints such as `/run` and `/cmd`. These endpoints expose runtime device info, command execution, and script control.

When using `script.js`, the following variables are commonly available or dynamically injected:

### 🔸 Runtime Variables (injected by backend or script logic)

* `currentPayload` – currently loaded payload content (string)
* `payloadList` – array of payload file names
* `settings` – key-value pairs from firmware (JSON)
* `deviceInfo` – firmware version, build date, board type
* `keyboardLocale` – currently selected keyboard layout (e.g. `US`, `FR`)
* `statusLog` – array of recent log lines from the device
* `connected` – boolean flag for WebSocket or connection status

### 🔹 Available Endpoints

| Endpoint    | Method   | Description                    |
| ----------- | -------- | ------------------------------ |
| `/run`      | POST     | Executes DuckyScript payload   |
| `/cmd`      | POST     | Executes command (e.g. reboot) |
| `/upload`   | POST     | Uploads new script to flash    |
| `/list`     | GET      | Lists stored payloads          |
| `/settings` | GET/POST | Reads/writes persistent config |

---

## 🎨 Styling the Interface with CSS

The interface is styled via `web_files/style.css`. This file supports:

* Layout grids for script selection and editors
* Custom button themes using `.btn`, `.btn-danger`, `.btn-primary`
* Light/dark mode toggles (if added)
* Console log styling via `.console-output`, `.log-line`
* Active/inactive state feedback via `.status-indicator`, `.badge`

You can customize or extend styles as needed:

```css
/* Example: highlight active script */
.active-script {
    background-color: #2525a0;
    color: white;
    font-weight: bold;
}

/* Example: custom button */
button.upload-btn {
    background-color: #0099cc;
    border: none;
    padding: 10px;
    border-radius: 5px;
    color: white;
    cursor: pointer;
}
```

Changes here will affect all elements once converted and flashed into the device.

---

## 🛠 Full Update Workflow

### 1. Edit HTML, CSS, or JS in `web_files/`

```bash
web_files/index.html
web_files/script.js
web_files/style.css
```

You may add new pages or components if needed.

---

### 2. Convert Web Files to Headers

After edits, run:

```bash
python3 tools/convert_web_to_header.py
```

This converts:

* `web_files/index.html` → `src/web/html_index_html.h`
* `web_files/style.css` → `src/web/html_style_css.h`
* `web_files/script.js` → `src/web/html_script_js.h`

You may also convert one file at a time:

```bash
python3 tools/convert_web_to_header.py web_files/index.html
```

---

### 3. Rebuild and Flash

```bash
pio run -e esp32-s3-devkitc-8MB-OTA
pio run -e esp32-s3-devkitc-8MB-OTA -t upload
```

---

## 🧪 Optional: Reverse Conversion

To preview or restore a `.h` file back to raw HTML/JS/CSS:

```bash
python3 tools/convert_header_to_web.py src/web/html_index_html.h
```

---

## 🚀 Tips for Advanced Customization

* Use `console.log()` in `script.js` to debug live output.
* Insert WebSocket/long-polling logic for dynamic updates (if desired).
* Combine UI changes with runtime variables from `/settings` for interactivity.
* Use `DOMContentLoaded` or `window.onload` to initialize interface logic safely.

---

## 📎 Summary Table

| Step | Description                     |
| ---- | ------------------------------- |
| 1    | Edit files in `web_files/`      |
| 2    | Run `convert_web_to_header.py`  |
| 3    | Rebuild and flash firmware      |
| 4    | Use `/cmd`, `/run`, `/settings` |

Take full control of the device’s interface with powerful embedded logic and a fully customizable web UI.
