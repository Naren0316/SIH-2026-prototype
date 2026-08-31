# SafarMitra — TransitMitra (SIH 2026)

> Auto-loaded by Claude Code as project context. Read `DEMO-RUN-ORDER.md` for how the demo is run.

---

## ⚑ CURRENT STATUS (read this first)

**The prototype is BUILT and working.** It lives in `index.html` in this folder.

- Self-contained single file — **no CDN, no npm, no build step, no internet required**
- Opens by double-clicking `index.html`
- Verified: runs offline, no console errors
- Has a Replay button + keyboard shortcuts (`1` sync, `2` toggle network, `3` SOS tab, `0` reset)

**Do not rebuild it from scratch.** Read `index.html` first, then make targeted changes.

### Files in this project
| File | What it is |
|---|---|
| `index.html` | ✅ The working demo prototype (3-panel demo console) |
| `DEMO-RUN-ORDER.md` | ✅ 3-minute click-by-click demo script + fallback plan |
| `CLAUDE.md` | This file — project context |
| `PROTOTYPE-SPEC.md` | Original build spec (historical; the build is done) |

### What is still open
1. Record a 90-second fallback screen-capture of the demo (Win+Alt+R) — **do before demo day**
2. Rehearse the run-order 3× with all three speakers on a real Google Meet
3. Optional polish only if time allows — do not destabilise a working demo

---

## Competition context

- **Event:** Smart India Hackathon 2026, Round 1
- **When:** Monday 31 August 2026, 4:00–6:00 PM, online (Google Meet)
- **Format:** 15 min per team — **10 min presentation + prototype demo**, then 5 min Q&A
- **Team Name:** SafarMitra
- **Problem Statement ID:** SIH26204 (Student Innovation · AICTE)
- **Presented as:** Theme Travel & Tourism · PS Category Software
- **Presenters:** 3 members

### Round 1 evaluation criteria (50 marks — 10 each)
1. **Problem Understanding & Relevance**
2. **Innovation & Creativity**
3. **Solution Approach & Technical Feasibility**
4. **Impact & Potential** (incl. scalability)
5. **Execution Plan & Presentation** (roadmap realism, clarity of delivery)

> The prototype earns marks mainly on **#3** and **#5**. Optimise for *demonstrability*, not features.

---

## The product — TransitMitra

An **offline-first travel companion** for remote/off-grid tourism in India. Works with
**zero internet, no SIM, no new telecom infrastructure**.

### The problem — three pains in one moment
A tourist in a remote valley hits a "connectivity blackout":
1. **No network** → no maps, no way to call for help
2. **Unknown routes & unfair fares** → overcharged by informal jeeps/autos/buses
3. **Language barrier** → cannot ask locals for help

Hurts tourists *and* the rural hotels, homestays and jeep operators who lose the income.

### Four features
1. **Hotel "Mitra Kiosk" sync** — on check-in the hotel device pushes the regional transit map,
   verified fares and emergency directory to the guest phone over Wi-Fi Direct / BLE.
2. **Verified transit & fares** — hotel-verified routes, timings and fixed fares for buses,
   shared jeeps and autos. Ends tourist overcharging.
3. **Store-and-forward SOS** — in dead zones a beacon hops phone-to-phone; a passing bus/jeep
   (**"Mitra Carrier"**) physically carries it down-valley until it reaches network, then
   auto-alerts authorities with GPS + tourist ID.
4. **Offline language help** — regional phrasebook + on-device text-to-speech.

### Signature innovation — "Mitra Carrier"
Registered buses and shared jeeps act as **scheduled data mules**, so an SOS rides out of the
dead zone on a predictable backbone rather than by luck. One mechanism, three jobs: SOS carrier,
live fare/timing source, and moving mesh relay.

Research lineage: **Delay-Tolerant Networking (RFC 5050)**, **MIT Media Lab DakNet**, **KioskNet**.

### SOS relay flow (implemented in the prototype's right-hand panel)
```
Tourist phone  →  Peer phone  →  Mitra Carrier  →  Cellular edge  →  Authorities
(beacon created   (BLE hop)      (bus carries      (first bar of     (auto-alert with
 offline)                         down-valley)      network)          GPS + tourist ID)
```

---

## Production tech stack (what the real app would use)
- **Languages:** Dart, Kotlin, Java, Python, C/C++, SQL
- **Mobile:** Flutter / Android native
- **P2P transport:** Google Nearby Connections, Wi-Fi Aware / Wi-Fi Direct, BLE advertising
- **Long range:** LoRa / Meshtastic relays (₹300–500 per node, km range)
- **Data:** SQLite, CRDT conflict-free offline merge, DTN store-and-forward
- **AI/voice:** TensorFlow Lite, on-device TTS
- **Security:** AES-signed, rate-limited SOS beacons

## Implementation roadmap (as pitched)
| Phase | What |
|---|---|
| **NOW** | Working prototype — offline sync, SOS relay, fare lookup |
| **0–3 mo** | Pilot on 1 tourist circuit · 5–10 hotel kiosks · fare database |
| **3–6 mo** | LoRa relays, Mitra-Carrier onboarding, offline language packs |
| **6–12 mo** | Scale across states via State Tourism-department partnerships |

## National mission alignment
Digital India · Vibrant Villages Programme · Dekho Apna Desh · **Atmanirbhar Bharat**

---

## ⚠ Honesty rules — do NOT violate (judges will probe in Q&A)
- SOS is a **best-effort augmentation, NOT a replacement** for official emergency services.
- The prototype **simulates** the radio layer (BLE / Wi-Fi Direct / LoRa). The UI must keep its
  visible "SIMULATED RADIO LAYER" label. Never imply real radios are running.
- Transit/fare data in the demo is **sample data** — keep it labelled as such.
- Never fabricate statistics, user numbers, partnerships or government endorsements.

## Demo-safety constraints (these drove the architecture — keep them)
- **No external dependencies.** No CDN, no npm install, no API calls, no web fonts.
  The demo is *about* working offline; it must survive the venue Wi-Fi dying.
- Plain HTML + CSS + vanilla JS in one file. No framework, no build step.
- Any change must keep: offline operation, zero console errors, working Replay reset.

## Brand palette (matches the pitch deck)
```
INDIGO  #16264F    INDIGO2 #22346B    TEAL  #0E7C86    TEALD #0A5F66
MINT    #10B8A0    INK     #1B2A3A    MUTE  #5C6B7A    TINT  #F2F6F8
TEALT   #E7F2F2    AMBER   #D98324    GREEN #2C8A5B
```
Clean sans typography, rounded cards, soft shadows, icons in filled circles.
Professional product look — not a toy demo.
