# Prototype demo — 3-minute run order

**File:** `index.html` — double-click it. Works with Wi-Fi **off**. Test that once, out loud, before the round.

Presenter: **Speaker 2** (the one sharing the screen). Share the **browser window**, not the whole
screen. Browser zoom 100%. Close other tabs. Silence notifications.

---

## The run (≈3 min)

| # | You do | You say |
|---|---|---|
| 0 | Console already open, nothing clicked | "This is TransitMitra running live. Watch the phone in the middle — it has no data yet." |
| 1 | Click **Sync to guest phone** (or press <kbd>1</kbd>) | "The guest checks in. The hotel kiosk pushes the whole valley — maps, 34 verified fares, the emergency directory — over Wi-Fi Direct. **Zero megabytes of mobile data.**" |
| 2 | Click **Go offline ✈** (or press <kbd>2</kbd>) | "Now I'm killing the network completely. No SIM, no signal — this is the valley." |
| 3 | Stay on **Transit & Fares** | "Still fully usable. Shared jeep to Manali: verified fare ₹120. A driver would quote ₹350. **That's ₹230 back in the tourist's pocket, offline.**" |
| 4 | Tap **Phrases**, tap a speaker button | "And they can actually talk to locals — on-device speech, no internet." |
| 5 | Tap **SOS** tab (or press <kbd>3</kbd>), press the red **SOS** | "Now the emergency. Watch the right panel." |
| 6 | *Say nothing for ~4 s — let it animate* | *(silence — the animation is doing the work)* |
| 7 | As the bus lights up | "The beacon hops to a nearby phone, then **boards a scheduled bus** — our Mitra Carrier. The signal is now physically driving out of the dead zone." |
| 8 | On the green result card | "Two minutes thirty-six. Authorities alerted with GPS. **No satellite. No new towers.** Just the buses that were driving down anyway." |
| 9 | Press **↻ Replay demo** (or <kbd>0</kbd>) | "Happy to run it again during questions." |

---

## Rules for a demo that doesn't die

- **Rehearse it three times.** Muscle memory beats confidence.
- **Do not narrate over the animation** at step 6. Silence makes it land.
- **Press Replay before you start**, so you always begin from a clean state.
- If anything freezes: press <kbd>0</kbd>, or just switch to the fallback video. Do not debug live.

## Fallback video (do this tonight, not tomorrow)
Record a 90-second screen capture of the full run — Windows: <kbd>Win</kbd>+<kbd>Alt</kbd>+<kbd>R</kbd>
(Xbox Game Bar), or OBS. Save it to the Desktop as `transitmitra-demo.mp4` and have it **already open
in a media player, paused**, on demo day. If the live demo misbehaves, play it and keep talking.
Judges accept a recorded demo; they do not accept two minutes of silent debugging.

## If a judge asks "is this the real app?"
Answer honestly and confidently — this is a strength, not a weakness:

> "This is our working prototype of the full user flow and the relay logic. The radio layer —
> BLE, Wi-Fi Direct, LoRa — is simulated here so it runs reliably on a call. The production build
> uses Google Nearby Connections and Wi-Fi Aware on Android, which is exactly what our 0–3 month
> pilot phase implements."

Never claim the radios are live. Over-claiming is what loses marks in Q&A.
