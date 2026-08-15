# Gym HUD

A fullscreen heads-up display for gym use, hosted as a Progressive Web App (PWA) on GitHub Pages.

**Live:** https://GarryHorsnell.github.io/gym-hud/

---

## What it does

Split-screen display designed to be visible at a glance during a workout:

- **Left panel — Clock:** Large HH:MM time, seconds, and date
- **Right panel — Heart rate:** Live BPM, session average, and session max
- Connects to a **Polar H10** (or any Bluetooth heart rate strap) via Web Bluetooth
- Fullscreen, offline-capable, installable as a PWA

---

## Device compatibility

| Browser | Bluetooth | PWA install | Notes |
|---|---|---|---|
| Chrome Android | ✅ | ✅ | Recommended |
| Brave Android | ✅ | ✅ | Web Bluetooth flag must be enabled |
| Samsung Internet | ⚠️ | ✅ | Bluetooth off by default; colour rendering differs |
| Desktop Chrome | ⚠️ | — | Web Bluetooth experimental |

Tested on Samsung Galaxy S23 Ultra.

---

## Installation (Android)

1. Open the live URL in Chrome
2. Tap the three-dot menu → **Add to Home screen**
3. Launch from your home screen — opens fullscreen with no browser chrome

---

## Connecting the heart rate strap

1. Ensure your Polar H10 (or compatible strap) is powered on and advertising
2. Tap **[ CONNECT STRAP ]** in the app
3. Select your device from the Bluetooth picker
4. BPM, AVG, and MAX update live once connected

Web Bluetooth requires a user gesture to initiate — connection cannot be fully automated in a browser PWA.

---

## Files

| File | Purpose |
|---|---|
| `index.html` | Full application — layout, styles, clock, BT logic |
| `manifest.json` | PWA manifest — fullscreen display, icons, theme |
| `sw.js` | Service worker — offline caching |
| `icon-192.png` | PWA icon (standard) |
| `icon-512.png` | PWA icon (large / splash) |

---

## Known limitations

- **Nav bar flicker** — Android's gesture navigation bar briefly appears on swipe-up. This is a Chrome PWA limitation; a TWA (Trusted Web Activity) wrapper would eliminate it.
- **Auto-connect** — `getDevices()` API requires the experimental permissions backend flag and the strap to be actively advertising on launch. Manual connect tap is the reliable approach.
- **White bar (top)** — Under investigation; related to `viewport-fit` and Android status bar handling.

---

## Tech stack

Plain HTML/CSS/JS — no build tools, no frameworks, no dependencies.

- Web Bluetooth API
- Web Vitals — Screen Wake Lock API
- Service Worker for offline support
- CSS `clamp()` for responsive text scaling across screen sizes

---

## License

MIT
