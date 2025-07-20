# N3WB WiFi Ducky

<p align="center">
    <img alt="WiFi Duck (n3wb edition)" src="content/n3wb_main_evil.png" width="400">
</p>
<p align="center">
    <img alt="WiFi Duck (n3wb edition)" src="content/Under-Construction.png" width="300">
</p>

An advanced HID injection platform for the ESP32-S3 featuring:

* Full support for Hak5 DuckyScript v1/v2/v3 (including IF/ELSE/WHILE/DEFINE/VAR/REPEAT)
* Web interface for payload management
* BLE + USB HID keyboard/mouse
* USB Mass Storage mode
* GPIO-triggered payload execution
* LED/TFT feedback

---

## 📂 Source Structure

| Directory      | Purpose                             |
| -------------- | ----------------------------------- |
| `src/`         | Core firmware logic (keyboard, USB) |
| `src/web/`     | Embedded web UI files (`html_*.h`)  |
| `src/Devices/` | Hardware drivers (TFT, GPIO)        |
| `payloads/`    | Example and feature scripts         |

---

## 🧨 Attack Modes

Use `ATTACKMODE` in payloads to change the USB behavior:

```ducky
ATTACKMODE HID        # USB keyboard/mouse
ATTACKMODE STORAGE    # USB Mass Storage
ATTACKMODE HID STORAGE # Combined mode
```

Use `BUTTON_DEF <filename>` to define the script executed when the physical button is pressed.

Example: `payloads/Examples/attackmode_demo.txt`

---

## 🛠 Building and Flashing

This project uses [PlatformIO](https://platformio.org/).

```bash
# Clone and enter the repo
git clone https://github.com/x0SiN0x/n3wbsWiFiDucky.git
cd n3wbsWiFiDucky

# Build for your target board
pio run -e esp32-s3-devkitc-8MB-OTA

# Flash firmware over USB
pio run -e esp32-s3-devkitc-8MB-OTA -t upload
```

---

## 🌐 Web Interface & WiFi

If no known Wi-Fi is available, the device creates a fallback AP:

* **SSID**: `iPh0ne12`
* **Password**: `12345678`

Access the interface at:

* `http://192.168.4.1`
* Or `http://n3wbswifiduck.local` (via mDNS)

From here, you can:

* Upload/edit/run DuckyScript payloads
* Set Wi-Fi, locale, autorun, button behavior

---

## 📝 Supported DuckyScript Features

| Feature                               | Supported     |
| ------------------------------------- | ------------- |
| `STRING`, `ENTER`, `TAB`, `ESC`, etc. | ✅             |
| `DELAY`, `DEFAULT_DELAY`, `REPEAT`    | ✅             |
| `REM` (comments)                      | ✅             |
| `IF`, `ELSE`, `ENDIF`                 | ✅             |
| `DEFINE`, `VAR`                       | ✅             |
| `WHILE`, `ENDWHILE`, `BREAK`          | ✅             |
| `ATTACKMODE`, `BUTTON_DEF`            | ✅             |
| `MOUSEMOVE`, `CLICK`, `SCROLL`        | ✅             |
| `MEDIA_*`, `VOLUMEUP`, `MUTE`, etc.   | ✅             |
| Locale switching (`LOCALE US`, etc.)  | ✅             |
| Script chaining (`INCLUDE`)           | ❌ (not yet)   |
| `CONTINUE`                            | ❌ (not found) |

---

## 🧪 Additional Features

* ✅ BLE HID injection via `BleComboKeyboard`
* ✅ USB Mass Storage mode (FFat + USB MSC)
* ✅ LED status feedback
* ✅ GPIO trigger configuration
* ✅ TFT screen support (optional)

---

## 🧠 Credits

Based on work from:

* [spacehuhn/WiFiDuck](https://github.com/spacehuhn/WiFiDuck)
* [Hak5 DuckyScript](https://docs.hak5.org/hak5-usb-rubber-ducky)

Fork maintained and extended by **x0SiN0x**.

---

## 📎 License

MIT License (see `LICENSE` file).
