<h1 align="center">BEACON</h1>
<h3 align="center">Basic Emergency Acoustic Communication &amp; Offline Navigation</h3>

<p align="center">
  Send text, position, photos and images over plain radio audio - no internet, no cell network.<br>
  Android app and Windows desktop app - Civilian Edition.
</p>

<p align="center">
  <img alt="Version" src="https://img.shields.io/badge/version-1.0-orange?style=for-the-badge">
  <img alt="Build" src="https://img.shields.io/badge/build-release%201.0-brightgreen?style=for-the-badge&logo=cmake&logoColor=white">
  <img alt="Edition" src="https://img.shields.io/badge/edition-civilian-blue?style=for-the-badge">
</p>
<p align="center">
  <img alt="Android" src="https://img.shields.io/badge/Android-8.1%2B%20(API%2027)-3DDC84?logo=android&logoColor=white">
  <img alt="Windows" src="https://img.shields.io/badge/Windows-10%20%2F%2011%20x64-0078D6?logo=windows&logoColor=white">
  <img alt="C++17" src="https://img.shields.io/badge/C%2B%2B-17-00599C?logo=cplusplus&logoColor=white">
  <img alt="Dear ImGui" src="https://img.shields.io/badge/UI-Dear%20ImGui%201.93-4F8FBA">
  <img alt="Offline" src="https://img.shields.io/badge/works-offline-success">
  <img alt="Languages" src="https://img.shields.io/badge/UI-EN%20%7C%20ID%20%7C%20JA-lightgrey">
</p>

---

## About

BEACON is a communication and navigation tool for situations where the usual networks are gone. It converts text messages, GPS positions, small photos and full-colour pictures into audio tones, so they can travel over any radio, a wired audio link, or simply through a phone speaker and microphone - with no internet and no cell coverage. The receiving device decodes the sound back into messages, shows nodes on a radar, a 3D map and an AR camera view, and keeps everything in a local inbox. The Android app and the Windows desktop app share the same modes, so a phone in the field and a PC at a base station can exchange messages, positions and pictures directly.

---

## Download

| Platform | File | Size | SHA-256 |
|---|---|---|---|
| Android 8.1+ | [`BEACON.apk`](https://github.com/YD1RUH/BEACON/releases/download/Beta-V1.0.0/BEACON.apk) | ~36 MB | `e4e7e7cba3abe68aa8a36018ce6781d75b341905d22b3808474198d207916a45` |
| Windows 10/11 (x64) | [`BEACON.exe`](https://github.com/YD1RUH/BEACON/releases/download/Beta-V1.0.0/BEACON.exe) | ~3 MB | `abdace789fa97eff6a08eeb0d793aa7bdefdf328ec994856b08078a8cda6b781` |

* **Android:** enable *Install unknown apps* for your browser/file manager, open `BEACON.apk`, allow Microphone (required), Location and Camera (optional).
* **Windows:** single portable file - no installer, no extra DLLs. Double-click `BEACON.exe`. Settings are kept in `%APPDATA%\MfskMessenger`.
* The APK is signed with a debug key (not from Google Play). Verify the SHA-256 above before installing.

> The build badges above are static. This repository contains binaries only (no source code), so no CI workflow is attached.

---

## How it works

BEACON turns data into sound. Connect the phone / PC audio to any radio (VOX or manual PTT) or just let two devices talk through their speaker and microphone.

| Mode | Purpose |
|---|---|
| **MFSK8 / 16 / 32 / 64** | Text messages and position beacons, robust on weak signals |
| **AFSK300 / AFSK1200** | APRS-style modulation (HF / VHF), this app's own frame format |
| **CW (Morse)** | `TO DE FROM text <AR>`, adjustable pitch and WPM |
| **Rattlegram (OFDM)** | Fast bursts - text and small JPEG photos (up to 320 x 320, 6 KB) |
| **SSTV** | Robot36, Scottie S1 / S2 / DX, PD50, PD120 - full colour pictures |

RX starts automatically when the app opens. The mode you choose is shared by Compose, Monitor RX and Photo, so there is never any doubt which mode is in use.

---

## Features (Android)

### Messaging

| Screenshot | Description |
|---|---|
| <img src="images/android_01_compose.png" width="220"> | **Compose.** Write a message, pick *From / To* (a callsign or `ALL`), choose the mode. A status bar above the text area shows the live state: **TX**, **RX DATA**, **RX SYNC**, **STANDBY** or **RX OFF**, plus the active mode. *Loopback to RX* lets you test everything without a radio. |
| <img src="images/android_02_inbox.png" width="220"> | **Inbox.** Received messages with sender and time. Unread messages are marked with `*` and counted next to your callsign. |
| <img src="images/android_03_message.png" width="220"> | **Message details.** Full text, sender, destination, time and mode. Delete messages you no longer need. |
| <img src="images/android_07_landscape_compose.png" width="320"> | **Landscape layout.** Form on the left, a full-height message area on the right. |

### Receiving

| Screenshot | Description |
|---|---|
| <img src="images/android_04_monitor_mfsk.png" width="220"> | **Monitor RX (MFSK).** Live spectrum of the 16 tones with the detected peak, RX state, frequency/clock correction (AFC), microphone AGC with input level, address filter and a real-time decoding log. RX is already running when you open the page. |
| <img src="images/android_05_monitor_rattlegram.png" width="220"> | **Monitor RX (Rattlegram).** DQPSK constellation view for the OFDM mode. AFSK modes show an eye diagram. |
| <img src="images/android_06_landscape_monitor.png" width="320"> | **Landscape Monitor.** Controls and spectrum on the left, the decoding log uses the full height on the right. |

### Photos and pictures

| Screenshot | Description |
|---|---|
| <img src="images/android_08_photo_modes.png" width="220"> | **Photo page and format picker.** Choose *Rattlegram (small JPEG)* or one of six SSTV modes. The estimated transmit time is shown for every option. |
| <img src="images/android_09_photo_camera.png" width="220"> | **Take photo (camera).** Opens the system camera, so you shoot the picture on the spot - no file picker. |
| <img src="images/android_10_photo_ready.png" width="220"> | **Photo ready.** The image is resized and compressed for the selected mode. Tap the preview to enlarge it. The mode selector at the top is the same one used in Compose and Monitor RX. |
| <img src="images/android_11_photo_sending.png" width="220"> | **Sending.** The transmit progress and the queue are shown, and RX pauses while transmitting (half-duplex). |
| <img src="images/android_12_photo_received.png" width="220"> | **Photo received.** Each photo keeps its sender, mode, heading and time. A photo that fails to decode is never added to the Inbox or chat. Coordinates are hidden in this screenshot. |
| <img src="images/android_13_photo_viewer.png" width="220"> | **Full-screen viewer.** Tap any photo to open it large. |
| <img src="images/android_14_photo_zoom.png" width="220"> | **Zoom in / out.** `-` / `+` buttons, *Fit* and *1:1*; drag to pan. |
| <img src="images/android_15_photo_sstv.png" width="220"> | **SSTV.** Position header first (in the current TX mode), then the analog SSTV picture. Sent and received pictures appear in one list. |

### Position, map and AR

| Screenshot | Description |
|---|---|
| <img src="images/android_16_position.png" width="220"> | **Position.** Send a position beacon at a fixed interval, pick a node (215 world capitals are built in) and see distance and bearing on the radar. *Start Tracking* uses GPS and the compass. |
| <img src="images/android_17_map3d.png" width="220"> | **3D Beacon Map.** Tilted 3D map with beacon nodes and capitals, node details (distance, bearing, last messages), 2D / compass / north-up buttons. Tiles you have viewed are cached for offline use. |
| <img src="images/android_18_ar.png" width="220"> | **AR Tracking.** Point the rear camera at the horizon: compass tape, camera attitude and floating labels for nodes and received photos. |

### Settings

| Screenshot | Description |
|---|---|
| <img src="images/android_19_station.png" width="220"> | **Station / Callsign.** Your callsign is the *From* of every message and the beacon ID. Optionally accept only messages addressed to you (`ALL`, `CQ`, `QST`, `*` always pass). |
| <img src="images/android_20_setting_menu.png" width="220"> | **Setting menu.** Station, language, theme, VOX tone, SSTV receive time limit and font size. |
| <img src="images/android_21_language_menu.png" width="220"> | **Language.** Indonesia, English and Japanese. |
| <img src="images/android_23_japanese.png" width="220"> | **Japanese UI.** The same screens in 日本語 (coordinates hidden). |
| <img src="images/android_22_theme_menu.png" width="220"> | **Themes.** Default, Dark, Dracula, Amber, Green Military and Black & White. |
| <img src="images/android_24_about.png" width="220"> | **About.** Version, full name and a short description of the frame formats. |

---

## Features (Windows desktop)

| Screenshot | Description |
|---|---|
| <img src="images/desktop_01_compose.png" width="420"> | **Compose.** Same two-column layout and the same status bar as on Android. |
| <img src="images/desktop_02_sending.png" width="420"> | **Transmitting.** The red **TX** label, a progress bar and a *Stop* button. |
| <img src="images/desktop_03_monitor.png" width="420"> | **Monitor RX.** Spectrum, signal state, AGC and a full-height live decoding log. A collapsible **Audio devices** section lets you pick the sound card or radio interface. |
| <img src="images/desktop_04_inbox.png" width="420"> | **Inbox.** Message list on the left, the selected message on the right. |
| <img src="images/desktop_05_position.png" width="420"> | **Position.** Beacon sender, node list and radar. There is no GPS on a PC, so the station location is typed in manually. |
| <img src="images/desktop_06_photo.png" width="420"> | **Photo.** Rattlegram or SSTV pictures. *Take photo* opens the Windows Camera app and picks up the new picture automatically; click a photo to open the zoomable viewer (mouse wheel to zoom). |
| <img src="images/desktop_07_map.png" width="420"> | **Beacon Map.** Offline-capable map with nodes and capitals, **3D** toggle, zoom, *Lock Me* and *All* buttons. |
| <img src="images/desktop_08_language.png" width="420"> | **Language and theme** in the *Setting* menu (Indonesia / English / 日本語). |
| <img src="images/desktop_09_about_menu.png" width="420"> | **About.** Same information as on Android. |

---

## Android vs Desktop

| Feature | Android | Windows desktop |
|---|:---:|:---:|
| MFSK8/16/32/64, AFSK300/1200, CW, Rattlegram | Yes | Yes |
| SSTV (Robot36, Scottie S1/S2/DX, PD50, PD120) | Yes | Yes |
| RX starts automatically on launch | Yes | Yes |
| Status bar (TX / RX DATA / RX SYNC / STANDBY) | Yes | Yes |
| One shared mode for Compose, Monitor RX and Photo | Yes | Yes |
| Inbox, address filter, loopback test | Yes | Yes |
| Photo send / receive with zoomable viewer | Yes | Yes |
| Take photo | System camera (in-app) | Windows Camera app |
| GPS position and compass | Yes | No (manual position) |
| AR Tracking (camera overlay) | Yes | No |
| Map | 3D tilted map (vector tiles) | 2D map with 3D toggle |
| Audio device selection | Phone audio / USB audio | Any Windows sound card or interface |
| Landscape / portrait layouts | Both | Resizable window |
| Languages (EN / ID / JA) and 6 themes | Yes | Yes |
| Install | APK (about 36 MB) | One portable `.exe` (about 3 MB) |
| Minimum system | Android 8.1 (API 27) | Windows 10 x64 |

---

## Good to know

* **Not an AX.25 / APRS packet radio.** AFSK modes use APRS-style modulation but the app's own frame, so ordinary APRS stations will not decode it. The MFSK modes are a simple implementation and are not compatible with fldigi.
* **Amateur radio.** If you transmit over a radio, follow your local regulations and use your own callsign.
* **Android map screen** is currently shown in Indonesian only; the rest of the app follows the selected language.
* Screenshots use a demo callsign (`YB0DEM`); real positions and personal photos were removed.

---

<p align="center"><sub>BEACON - Basic Emergency Acoustic Communication &amp; Offline Navigation - Civilian Edition 1.0</sub></p>
