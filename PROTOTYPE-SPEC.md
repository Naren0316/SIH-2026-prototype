# Prototype Build Spec — what Claude Code should build

## Hard constraints (read first)

- **Deadline:** demo is Monday 31 Aug, 4–6 PM. Build time ≈ 1 day. Scope accordingly.
- **Demo medium:** Google Meet screen-share, on a laptop. Not a physical phone.
- **CRITICAL — no internet dependency.** The demo is *about* working offline. It must run
  from a local file with **no CDN, no npm install at demo time, no API calls**. If the
  venue Wi-Fi dies mid-demo, the prototype must still work. This is also a great line to
  say out loud: *"our demo itself runs fully offline."*
- **Therefore: plain HTML + CSS + vanilla JS, no build step, no external dependencies.**
  A single `index.html` (plus local assets) that opens by double-click. No React CDN,
  no Tailwind CDN, no Google Fonts.
- Simulate the radio layer. Label it as simulated in the UI.

## What to build — 3 panels on one screen

A single page laid out as a **demo console** so all three parts are visible at once during
screen-share (no tab-switching mid-demo, which is where live demos die).

### Panel A — Hotel "Mitra Kiosk" (left)
- Card styled as a hotel desk device: *"Mitra Kiosk · Hotel Devgiri Homestay, Kasol"*
- Shows payload contents: regional offline map, **12 routes**, **34 verified fares**,
  emergency directory (sample data — label as sample)
- Big primary button: **"Sync to guest phone"**
- On click: animated Wi-Fi Direct transfer to Panel B with a progress bar, finishing in
  ~2 s, then a green "Synced · 0 MB data used · no internet" confirmation.

### Panel B — Tourist phone (centre, drawn in a phone frame)
Top status bar with a **toggle: `ONLINE` ⇄ `NO SERVICE`** — the presenter flips this to
"NO SERVICE" to prove everything still works. Make this toggle prominent; it is the spine
of the whole demo.

Three tabs:
1. **Transit & Fares** — pick from/to (e.g. Kasol → Manali). Shows shared jeep / bus / auto
   options with **departure times** and a **VERIFIED FIXED FARE** badge, plus a muted line
   *"typical tourist quote: ₹X"* to make the overcharging saving visible at a glance.
2. **SOS** — a large red hold-to-trigger button. When pressed while `NO SERVICE`:
   creates a beacon (show beacon ID, GPS coords, timestamp, "AES-signed"), then hands off
   to Panel C. Show a calm, honest status line: *"Best-effort relay — not a replacement for
   emergency services."*
3. **Phrasebook** — 6–8 useful phrases (English ⇄ Hindi + a local language), each with a
   speaker button. Use the browser's built-in **Web Speech API (`speechSynthesis`)** —
   it is offline-capable and needs no key. If a voice is unavailable, fall back gracefully
   to showing the phonetic text (never crash).

### Panel C — Mesh Relay Visualiser (right) — THE MONEY SHOT
An animated schematic (inline SVG or canvas) of the valley showing the SOS travelling:

```
[Tourist phone] --BLE hop--> [Nearby trekker phone] --carried--> [Mitra Carrier bus]
      --moves down valley--> [Cellular edge ▲] --alert--> [Authorities dashboard]
```

- Animate a glowing packet moving along the path, node by node, over ~10–12 seconds.
- Below it, a **live event log** with timestamps, e.g.:
  ```
  16:04:02  Beacon created offline · ID 7F2A · GPS 32.0998, 77.1892
  16:04:05  Hop 1 → peer device (BLE, RSSI -72 dBm)
  16:04:19  Boarded Mitra Carrier · HP-01-4517 (Kasol→Bhuntar, scheduled)
  16:06:41  Network acquired · 1 bar · alert transmitted
  16:06:42  ✅ Authorities notified · ETA dispatch 14 min
  ```
- End state: a green "Authorities notified" card showing total relay time.
- Add a small **"Simulated radio layer"** label so it is honest on screen.

## Nice-to-have (only if time remains)
- A "Replay demo" reset button (essential for rehearsal, cheap to build — arguably do this first).
- Keyboard shortcuts (1/2/3) to jump the demo to each stage in case of time pressure.
- A tiny "architecture" toggle that overlays the real tech names (Nearby Connections, LoRa,
  CRDT) on the visualiser — good for answering technical Q&A live.

## Definition of done
1. Opens offline by double-clicking `index.html`, no console errors.
2. The full story runs end-to-end in **under 3 minutes**: sync → go offline → check fare →
   trigger SOS → watch it relay → authorities notified.
3. A "Replay" control resets cleanly so it can be rehearsed repeatedly.
4. Visual style matches the deck palette in `CLAUDE.md`.
5. Nothing on screen claims to be real radio hardware or a real emergency service.

## Fallback plan (do this before the demo)
Record a **60–90 second screen capture** of the working prototype and keep it on the
desktop. If anything misbehaves live on Meet, play the recording instead. Judges accept a
recorded demo; they do not accept two minutes of silent debugging.

---

# Paste this as your first message to Claude Code

> Read CLAUDE.md and PROTOTYPE-SPEC.md in this folder first.
>
> Build the TransitMitra demo prototype exactly as specified: a single self-contained
> `index.html` (plus local CSS/JS files if you prefer, but NO external dependencies, no CDN,
> no build step) that runs offline by double-click.
>
> Start with a working end-to-end skeleton of all three panels — hotel sync, phone with the
> ONLINE/NO SERVICE toggle, and the mesh relay visualiser with its event log — including the
> Replay button. Get the whole flow working before polishing any single panel.
>
> Use the colour palette from CLAUDE.md. Keep the code readable and commented, because I may
> need to explain the architecture to judges.
>
> When it runs, tell me how to open it and give me a 3-minute demo run-order I can rehearse.
