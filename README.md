# 🛰️ MST — Macan Satellite Tracker

**Real-time satellite tracking, offline-first TLE catalog, pass prediction, and a 2D sky radar — all in your pocket.**

MST is an Android app that shows where satellites are right now, predicts when they will fly over your location, and helps you point your phone at the sky to find them. It ships with a built-in catalog so it works out of the box, even without an internet connection.

> Part of the **Macan Angkasa** family.

---

## 📸 Screenshot

<img width="1444" height="1600" alt="mst-01" src="https://github.com/user-attachments/assets/e09dab0a-83a3-4660-9561-5f4837e80821" />

<img width="1444" height="1600" alt="mst-02" src="https://github.com/user-attachments/assets/424dd20f-51c0-4e72-9319-e0fce27e1547" />

---


## ✨ Features

### 🌍 Live Orbit Map
- Real-time satellite position, updated every second
- Ground track for the next 90 minutes
- Satellite footprint (coverage circle) on the map
- Your observer location pinned on the map
- Pinch to zoom and drag to pan
- Quick-switch bar to jump between satellites
- Telemetry sheet: latitude/longitude, altitude, velocity, orbital period, azimuth/elevation, and range to observer

### 📚 Satellite Catalog (Offline Ready)
- Built-in catalog with Indonesian satellites (SATRIA-1, Telkom 3S, Telkom 4, BRISAT, Nusantara Satu, LAPAN-A2, LAPAN-A3), ISS, Tiangong, NOAA, Meteor-M2, Starlink, and Hubble
- Search by name or NORAD ID
- Filter by category: All, Favorites, Indonesia, Stations, Weather, Starlink, Geostationary
- Mark favorites for quick access

### 🔄 CelesTrak Sync
- Download fresh TLE data from [CelesTrak](https://celestrak.org) for Space Stations, Weather satellites, Starlink, and Geostationary satellites
- Data is stored locally, so it stays available offline after syncing
- Your favorites are preserved when syncing

### ⏱️ Pass Prediction
- Predicts passes for the next 48 hours
- Shows AOS (appear), peak elevation, and LOS (disappear) with azimuths
- Pass quality rating based on peak elevation (Low / Fairly High / Excellent)
- Only passes with a peak elevation of 10° or higher are listed

### 📍 Observer Location
- Detect your location with GPS
- Pick from Indonesian city presets (Jakarta, Surabaya, Bandung, Medan, Makassar, Denpasar, IKN Nusantara)
- Or enter coordinates manually

### 📡 Sky Radar 2D
- Polar radar view showing the satellite's azimuth and elevation
- AR compass mode: the radar rotates with your phone's heading using the rotation vector sensor
- Steering hints ("turn left/right") and a target-lock indicator when the satellite is right in front of you
- Switch to fixed North-Up mode at any time

---

## 📲 Installation

1. Download the latest `MST.apk` from the release page.
2. On your Android device, allow installation from unknown sources for your browser or file manager (Settings → Security / Apps → Install unknown apps).
3. Open the APK and tap **Install**.
4. Launch **MST**.

### Requirements
- Android 7.0 (API 24) or higher
- Internet connection for CelesTrak sync (optional — the built-in catalog works offline)
- Location permission for GPS detection (optional — you can choose a preset or enter coordinates manually)
- A rotation vector sensor for the AR compass mode in Sky Radar (found on most modern phones)

---

## 🚀 Quick Start

1. Open the app — the **Orbit Map** shows the default satellite live.
2. Go to **Catalog** to pick another satellite, or tap **CelesTrak** to sync fresh data.
3. Open **Prediction** and set your location (GPS, preset, or manual) to see upcoming passes.
4. When a pass is about to begin, open **Sky Radar** and follow the on-screen hints to find the satellite in the sky.

> 💡 **Tip:** For the most accurate results, sync with CelesTrak first. Orbital data (TLE) gets outdated over time, especially for low Earth orbit satellites.

---

## 🔬 How It Works

MST uses a pure Kotlin orbit propagation engine that includes:
- TLE parsing
- Keplerian orbit solving
- J2 secular perturbations (Earth oblateness)
- ECI → ECEF conversion using Greenwich Mean Sidereal Time
- Topocentric azimuth/elevation/range calculation
- Ground track generation and pass prediction

Orbital data comes from TLE (Two-Line Element) sets, either bundled in the app or downloaded from CelesTrak.

### ⚠️ Accuracy Notes
- The propagator is a simplified model, not a full SGP4 implementation. It does not model atmospheric drag or deep-space perturbations, so errors grow as the TLE gets older.
- The bundled catalog is a static snapshot. Sync with CelesTrak for current data.
- Pass times are calculated in 30-second steps, so expect roughly ±30 seconds of resolution.
- The world map uses simplified outlines for orientation only.

---

## 🔐 Permissions

| Permission | Purpose |
|---|---|
| `INTERNET` | Download TLE data from CelesTrak |
| `ACCESS_NETWORK_STATE` | Check connectivity |
| `ACCESS_FINE_LOCATION` / `ACCESS_COARSE_LOCATION` | Detect your observer location (optional) |

Your location is used only on your device to calculate satellite visibility. It is never sent anywhere.

---

## 🧰 Built With

- Kotlin
- Jetpack Compose + Material 3
- Room (local database)
- OkHttp
- Google Play Services Location
- Android Sensor Framework

---

## 🙏 Credits

- Orbital data courtesy of [CelesTrak](https://celestrak.org)

---

## 📬 Feedback

Found a bug or have a feature idea? Let me know — feedback is always welcome.

**Made with ❤️ in Indonesia by Danx — Macan Angkasa**
