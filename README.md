# 🦆 N3WB WiFi Ducky

<p align="center">
    <img alt="WiFi Duck (n3wb edition)" src="content/n3wb_main_evil.png" width="400">
</p>
<p align="center">
    <img alt="WiFi Duck (n3wb edition)" src="content/Under-Construction.png" width="300">
</p>

A powerful HID injection platform built for the **ESP32-S2/S3**, designed for hackers, red teamers, and tinkerers. Inspired by the original Hak5 USB Rubber Ducky, this project extends the functionality with modern features like **DuckyScript v3**, **BLE HID**, **web UI control**, and **GPIO-triggered payloads** — all in an open, self-hosted platform.

> ⚠️ This is a **tool for learning, research, automation, and security testing**. Use responsibly and only on devices you own or have explicit permission to test.

---

## 🔥 Supported Features

- ✅ A majority of the DuckyScript v1/v2/v3 interpreter funcionality (including `IF`, `WHILE`, `VAR`, etc.)
- ✅ Web-based interface for script management and configuration
- ✅ USB HID injection (keyboard + mouse)
- ✅ BLE HID support (Bluetooth attacks on compatible targets)
- ✅ USB Mass Storage mode (mount drive with payloads)
- ✅ GPIO-triggered payload execution
- ✅ LED and optional TFT screen for real-time feedback
- ✅ Wi-Fi and mDNS access point with fallback captive portal

---

## 🎯 Legitimate Use Cases

This tool can be used for a wide range of non-malicious purposes:

- Penetration testing in controlled environments
- Red teaming engagements with proper authorization
- Automating kiosk input, form entry, or developer tools
- Accessibility or usability testing of input interfaces
- Educational purposes — learn scripting, USB, BLE, and embedded development

---

## ⚠️ Ethical Use Reminder

**This project is for educational and ethical hacking purposes only.** Unauthorized use against devices, networks, or systems without consent may be illegal and unethical. Always get permission before deploying this tool in the field.

---

## 🧨 Example Builds

<p align="center">
    <img alt="WiFi Duck (n3wb edition)" src="content/IMG_8255.jpg" width="400">
    <img alt="WiFi Duck (n3wb edition)" src="content/IMG_8254.jpg" width="400">
</p>

---

## 🚀 Attack Modes

Switch USB functionality dynamically from DuckyScript:

```ducky
ATTACKMODE HID             # Emulates keyboard/mouse
ATTACKMODE STORAGE         # Emulates USB Mass Storage
ATTACKMODE HID STORAGE     # Combines HID and storage
```

Define a payload for the physical button:

```ducky
BUTTON_DEF payloads/my_script.txt
```

Example: `payloads/Examples/attackmode_demo.txt`

---

## 🌐 Web Interface & WiFi

If no Wi-Fi is configured, the device launches an AP:

- **SSID**: `iPh0ne12`
- **Password**: `12345678`
- **Web UI**: [http://192.168.4.1](http://192.168.4.1) or [http://n3wbswifiduck.local](http://n3wbswifiduck.local)

Use the interface to:

- Upload/edit/run DuckyScript payloads
- Configure Wi-Fi, locale, autorun, GPIO, and more

---

## 🛠 Flashing via Web Serial

To flash your ESP32-S2/S3 device:

1. Visit [https://esptool.spacehuhn.com/](https://esptool.spacehuhn.com/)
2. Connect your board via USB and select the serial port
3. Download the `.zip` firmware from [Releases](https://github.com/x0SiN0x/n3wbWiFiDucky/releases)
4. Extract and flash the `.bin` files:

| File           | Offset     |
|----------------|------------|
| `bootloader.bin` | `0x1000`   |
| `partitions.bin` | `0x8000`   |
| `firmware.bin`   | `0x10000`  |
| `littlefs.bin`   | `0x290000` *(LilyGO only)* |

Works in modern browsers (Chrome, Edge) with no drivers required.

---

## 📝 DuckyScript Feature Matrix

| Feature                                  | Supported     |
|------------------------------------------|---------------|
| `STRING`, `ENTER`, `TAB`, etc.           | ✅             |
| `DELAY`, `DEFAULT_DELAY`, `REPEAT`       | ✅             |
| `REM` (comments)                         | ✅             |
| `IF`, `ELSE`, `ENDIF`                    | ✅             |
| `DEFINE`, `VAR`                          | ✅             |
| `WHILE`, `ENDWHILE`, `BREAK`             | ✅             |
| `ATTACKMODE`, `BUTTON_DEF`               | ✅             |
| `MOUSEMOVE`, `CLICK`, `SCROLL`           | ✅             |
| `MEDIA_*`, `VOLUMEUP`, `MUTE`, etc.      | ✅             |
| Locale switching (`LOCALE US`, etc.)     | ✅             |
| Script chaining (`INCLUDE`)              | ❌ (planned)   |

---

## 🔧 Advanced Features

- BLE HID via `BleComboKeyboard` (experimental)
- USB MSC + FFat integration for drag-and-drop scripts
- Dynamic GPIO trigger configuration
- Optional TFT display support
- Persistent user settings with `Preferences`

---

## 🧪 Development Notes

- Expect bugs — this is a work in progress!
- Originally forked from an older ESP32-based DuckyScript repo
- Goals: modernize, extend, and learn along the way
- Will be fully open source once stabilized and cleaned up

---

## 🙏 Credits & Inspiration

This project builds upon amazing work by:

- [spacehuhn/WiFiDuck](https://github.com/spacehuhn/WiFiDuck)
- [Hak5 Rubber Ducky](https://docs.hak5.org/hak5-usb-rubber-ducky) — original creators of DuckyScript
- Various other similar tools out there picking and choosind ideas that just made sense

Maintained and enhanced by **@x0SiN0x** and **@x0jac0bx**.

---
