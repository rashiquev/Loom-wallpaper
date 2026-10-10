<div align="center">

# Loomview

**A live wallpaper engine for Android that renders interactive HTML directly on your home screen.**

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![Android](https://img.shields.io/badge/Android-8.0%2B-brightgreen.svg)](https://developer.android.com/about/versions/oreo)
[![Kotlin](https://img.shields.io/badge/Kotlin-1.9-purple.svg)](https://kotlinlang.org/)

</div>

---

## What is Loomview?

Loomview is an open-source Android live wallpaper app that lets you set **any HTML file** as your home screen wallpaper. If it runs in a browser, it runs on your wallpaper.

- **Particles, WebGL shaders, canvas animations** — anything web-based works.
- **Touch-reactive** — your wallpaper can receive and respond to finger touches.
- **Fully offline** — files are loaded directly from your device via the Storage Access Framework. No cloud, no tracking.

## Screenshots

<div align="center">
  <video src="https://github.com/user-attachments/assets/2c8be4f6-bcc0-4c2d-98bf-ebed70d5b130" width="200" autoplay loop muted playsinline></video>
</div>

If you're interested in the live wallpaper effect shown in the screenshots, it was created using another project of mine. Feel free to check it out: https://bokehdepthstudio.com

## Features

- 🌐 Renders HTML/CSS/JavaScript via the system WebView (Chromium)
- 🎨 Built-in file browser with grid/list view, favorites, and recents
- ⚙️ Render quality settings (Native / Standard / Saver) and FPS cap
- 🔋 Auto-downgrade on low battery
- 🌙 Light / Dark / System theme
- 🌍 Multilingual (English, Traditional Chinese)
- 🖼️ Gradient thumbnail previews in the system wallpaper picker

## Requirements

- Android 8.0 (API 26) or higher
- Android Studio Hedgehog or newer (to build from source)

## Building from Source

1. Clone the repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/loomview.git
   cd loomview
   ```

2. Open the project in **Android Studio**.

3. Let Gradle sync automatically.

4. Click **Run ▶** to build and install on your device or emulator.

> **Note:** The app uses the **Storage Access Framework (SAF)** — no `READ_EXTERNAL_STORAGE` permission is required. HTML files are picked via the system file picker.

## Architecture

Loomview is a **100% native Android** app built with modern Android best practices:

| Layer | Technology |
|---|---|
| UI | Jetpack Compose + Material 3 |
| Live Wallpaper Engine | `WallpaperService` + `WebView` + `VirtualDisplay` |
| Data Persistence | Room (file records) + DataStore (settings) |
| Dependency Injection | Hilt |
| Image Loading | Coil |
| File Access | Storage Access Framework (SAF) |

## How the Wallpaper Engine Works

The core challenge is rendering a hardware-accelerated `WebView` (with WebGL support) inside a `WallpaperService`, which normally does not provide a window for hardware acceleration.

Loomview solves this using the **`Presentation` + `VirtualDisplay` pattern**:
1. A `VirtualDisplay` is created mirroring the physical screen dimensions.
2. A `Presentation` window is attached to it, providing a proper hardware-accelerated `Window`.
3. The `WebView` is hosted inside this `Presentation`, enabling full WebGL support.
4. The rendered output flows from the `VirtualDisplay` to the wallpaper surface.

## Contributing

Contributions, issues, and feature requests are welcome! Feel free to open an issue or submit a pull request.

## License

```
Copyright 2026 Loomview Contributors

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0
```
