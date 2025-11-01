# FlHideAndSeek (CounterStrikeSharp)

A **Hide & Seek** plugin for **CS2 (CounterStrikeSharp)**.  
This repository publishes **binary releases (DLL/ZIP)** — **no source code**.

## Downloads
See the repository **Releases**. Each release includes:
- `FlHideAndSeek.dll`
- `README.txt` (server installation)
- `example.config.json`

## Features
- **Dynamic number of Seekers**:  
  `< 10 players` → 1 seeker, `≥ 10` → 2 seekers, `≥ 15` → 4 seekers.  
  The **last CTs found** this round become the **seekers** next round.
- **Round randomizer** (fair, no instant repeats):  
  - **Speed Boost** (+25% movement speed for seekers)  
  - **Deagle** (4 shots; auto-removes when empty)  
  - **2× Bloodsucker Grenades** (Decoys)  
  - **2× Freeze Bombs** (Smokes, T side only)  
- **Clean round flow**: when the last CT is found → **5s delay**, then `mp_restartgame 1`.
- **Lifecycle safety**: all delayed timers are guarded to avoid map-change crashes.

## Gameplay details

### Bloodsucker Grenade (Decoy)
- Treated as a decoy entity but thematically a **Bloodsucker**.  
- When active, it **damages CTs** that are close to it over time (DoT).  
- Given to **Seekers (T)** by the randomizer as a **pair (×2)**.  
- (CTs can be configured to receive one decoy on spawn depending on server rules.)

### Freeze Bomb (Smoke, T side)
- Implemented via smoke grenades but functions as a **Freeze Bomb**.  
- On activation, it **slows/freezes** CTs that enter the cloud (server-side effect).  
- Given to **Seekers (T)** by the randomizer as a **pair (×2)**.  
- Not issued to CTs by default.

### Deagle (4 shots)
- Seekers may receive a Deagle with **4 total shots**.  
- After the 4th shot, the weapon is removed automatically.

### Speed Boost (+25%)
- Seekers may receive a **+25% speed** boost for the round.  
- The speed is re-applied periodically to resist overwrites from other plugins/maps.

## Installation
1. Copy the DLL to:
csgo/addons/counterstrikesharp/plugins/
2. Restart your server.

## Configuration
Create a plugin JSON (example path):
addons/counterstrikesharp/configs/plugins/FlHideAndSeek.json
Use the `example.config.json` from the release ZIP as a starting point.  
Important keys:
- `hns_powerups_enabled`: enable/disable the randomizer  
- `hns_speedboost_percent`: e.g. `0.25` for +25% speed  
- `hns_randomizer_ms` / `hns_randomizer_steps`: animation timing  
- `hns_hard_restart_on_round_end`: keep inventory clean between rounds

## Support
- Open an issue in this repository (tab **Issues**).
- Author profile: https://github.com/JumperBhop

## License
MIT — see `LICENSE`.


