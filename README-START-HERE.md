# How to move this into Claude Code

## 1. Make a project folder on your laptop
```
~/safarmitra-prototype/
```
Put these three files inside it:
- `CLAUDE.md`  ← all the project context (Claude Code loads this automatically)
- `PROTOTYPE-SPEC.md`  ← the build task
- `README-START-HERE.md`  ← this file

Optionally also drop in `TransitMitra_SIH2026.pdf` and `TransitMitra_Pitch_Script.pdf`
so the deck and script live alongside the code.

## 2. Install Claude Code (skip if you already have it)
```bash
npm install -g @anthropic-ai/claude-code
```
Requires Node.js 18+. Verify with `node --version`.

## 3. Open a terminal **inside that folder** and start it
```bash
cd ~/safarmitra-prototype
claude
```
Sign in when prompted (first run only).

`CLAUDE.md` is picked up automatically as context — that is the whole trick. You do not
need to paste the project background again; it is already in the file.

## 4. Send the first prompt
Copy the block at the bottom of `PROTOTYPE-SPEC.md` (under
*"Paste this as your first message to Claude Code"*) and send it.

## 5. Useful things to know while building
| What | How |
|---|---|
| See the result | Ask Claude Code to open it, or just double-click `index.html` |
| Ask for a change | Describe it plainly: *"make the SOS button bigger and the relay animation slower"* |
| Undo / retry | `Esc` interrupts; ask it to revert a change |
| Keep context tidy | `/clear` starts a fresh conversation (CLAUDE.md is still loaded) |
| Save learnings | Ask it to append decisions to `CLAUDE.md` as you go |

## 6. Order of work for tomorrow (suggested)
1. **Skeleton first** — all three panels wired end-to-end, ugly but working.
2. **Replay button** — you need this to rehearse. Build it early, not last.
3. **Polish the relay visualiser** — it is the moment judges remember.
4. **Record the 90-second fallback video.** Do this the moment it works, not at 3 PM.
5. Rehearse the 3-minute run-order twice with all three speakers on a real Meet call.

## 7. Demo-day checklist
- [ ] `index.html` opens with no internet connected (test with Wi-Fi off)
- [ ] Replay resets cleanly
- [ ] Fallback screen-recording saved on the desktop
- [ ] Screen-share tested on Google Meet (share the **window**, not the whole screen)
- [ ] Notifications silenced, browser zoom at 100%, other tabs closed
- [ ] One person owns the share for the whole session
