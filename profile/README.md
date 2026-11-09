<img src="https://avatars.githubusercontent.com/digimax-mu" width="72" align="right" alt="Digimax">

# Digimax

**Every format. One studio.** · [digimax.mu](https://digimax.mu) · info@digimax.mu

Digimax Ltd takes an idea from screen to paper, photo or solid object: print, photography, 3D printing, and websites with interactive 3D. When the software we needed didn't exist, we wrote it. This is where the open-source parts live.

### Work

<img src="img/gg-class.jpg" alt="Live indoor cycling class on the studio TV: eight riders' power dials beside a race through the Stellenbosch vineyards">

**Grannygear: a complete indoor cycling studio, Cape Town.** Every bike gets a tablet showing power, cadence and heart-rate zones, and the whole class rides together on the big screen with an instructor clock everyone follows. Behind it: a ride app that runs on tablets as old as Chrome 81, a Windows app, a TV app, an Android bridge that talks ANT+ and Bluetooth to trainers, power meters, heart-rate straps and handlebar controllers, and a staff portal for bikes, riders and workouts. Built and run on Cloudflare.

<img src="img/gg-ride.jpg" width="49%" alt="Bike tablet during a free ride: time, power, cadence and heart-rate zones"> <img src="img/stl-splitter.jpg" width="49%" alt="STL Splitter cutting a terrain model into 25 printable tiles, shown on 25 printer beds">

**STL Splitter.** Born on a museum job: a terrain model far too big for any printer, and the splitter we tried left open edges. Ours cuts it into tiles that fit the bed and checks every tile is a sealed solid before you can download it, with print time and filament per tile. Free, in the browser, nothing uploaded. [Open it](https://digimaxstlsplitter.pages.dev)

<img src="img/oriental-spa.jpg" alt="Oriental Spa website home page for the Brackenfell branch">

**Oriental Spa: two branches on one system.** Website, online booking, gift vouchers with QR redemption at reception, staff and therapist apps, menu QR cards and printed brand pieces. Every staff app has a one-tap "Fix it" button, and a watchdog checks the system every 15 minutes and tells us before the spa notices.

<img src="img/qsys-main.jpg" alt="Q-SYS control page: Play and Stop overrides, start and stop countdowns, projector power, six media players and sixteen audio tracks">

**Museum show control, Iziko Museums of South Africa.** Six BrightSign video players, five projectors and sixteen audio tracks run one synchronised show that starts and stops itself every day. We wrote the Q-SYS Lua controllers that run on the audio core: countdown timers for the daily start and stop, a sync receiver that keeps audio locked to the video's loop marker, a master that broadcasts start and stop to every player, and a gate that keeps projectors in step with the show. The manual Play and Stop buttons stay as an override.

<img src="img/qsys-sync.jpg" height="340" alt="Q-SYS Lua components: sync receiver, bridge master and startup timer"> <img src="img/qsys-timers.jpg" height="340" alt="Q-SYS Lua components: shutdown timer, master player and start launcher"> <img src="img/qsys-player.jpg" height="340" alt="Q-SYS Lua bridge component for one media player">

Each controller documents itself in its header, so the operator can change the show without a developer:

```lua
--[[ startup_timer.lua: countdown to the daily show start
  Pair with shutdown_timer.lua:
     startup_timer  StartShow ──► show_button.Play     @ 09:55
     shutdown_timer StopShow  ──► show_button.Reset    @ 16:40
  Both read their time from a Text input pin, so changing the
  schedule means editing the StartTime / StopTime field. No rebuild.

  Behaviour, armed automatically on load:
    - Inside the show window: start now (a mid-day reload recovers the show)
    - Otherwise: count down to the next StartTime and fire at zero
  The Core has no NTP, so the clock is synced from the bridge and every
  tick recomputes time-left from the wall clock: it never drifts.
]]
```

<img src="img/wall-dashboard.jpg" alt="BrightSign Wall: live thumbnails from each media player with uptime, playhead and one-click repair">

The BrightSign Wall app shows a live thumbnail from every player, its uptime and playhead, and one-click repair. Server upstairs, players downstairs: no walking.

### Open source

| Tool | What it does |
|---|---|
| [digimaxstlsplitter](https://github.com/digimax-mu/digimaxstlsplitter) | Splits a model too big for any printer into tiles that fit the bed, and checks every tile is a sealed solid before you download it. Runs in your browser, nothing is uploaded. [Open it](https://digimaxstlsplitter.pages.dev) |
| [digimax-transcriber-android](https://github.com/digimax-mu/digimax-transcriber-android) | Records with the screen locked and transcribes on the phone. No network permission. |

Both are MIT licensed. The Digimax name, logo and artwork are not.

Mauritius · [digimax.mu](https://digimax.mu)
