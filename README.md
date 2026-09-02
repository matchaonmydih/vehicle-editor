# Matcha's Vehicle Editor 🍵

A script that drops a gui onto most Roblox vehicles, letting you mess with its physics in real time; weight, suspension, body force, wheels, the works. Built around a persistent sidebar app instead of a floating panel, so it feels more like a tool than a script menu.

### Script
```lua
loadstring(game:HttpGet("https://raw.githubusercontent.com/matchaonmydih/vehicle-editor/refs/heads/main/main.lua"))()
```

## Features

### Vehicle Detection
- Auto-detects when you sit in a vehicle and pulls up the relevant controls
- Handles streaming lag by retrying vehicle resolution a few times before giving up, so the UI doesn't show blank/stale info right after you enter a seat
- Works with weird nested vehicle setups — climbs up through Model ancestors until it finds the one that actually has the vehicle's parts (springs, hinges, body force, weight parts) instead of grabbing the wrong container

### Vehicle (Weight) Tab
- Change the weight part's shape: Block, Ball, Wedge, Cylinder, Corner Wedge
- Full physical properties editor, density, friction, elasticity, friction weight, elasticity weight, each with its own tab, slider, and manual input box
- Apply all at once or reset back to the vehicle's original values
- **Massless toggle** — strips all mass from the weight part(s). Gated behind a confirmation warning since it can make the car fly/flip/go insane, with a "don't show again" option that actually persists

### Maybach Mode
- Smoothly oscillates the car's weight density over time for that bounce/hop effect
- Adjustable speed and intensity sliders, tuned live
- Auto-calculates a sane default intensity based on the vehicle's actual density instead of just guessing
- One-click reset back to defaults

### Suspension
- **Jump** — spikes the wheel springs' FreeLength for a quick hop, with adjustable height
- **Bunnyhop** — repeats the jump on a loop at a configurable speed, toggle on/off
- Per-wheel tabs (FL/FR/RL/RR etc.) with individual FreeLength, Damping, Stiffness, and Limit sliders
- Group tabs to edit front/rear/all wheels together instead of one at a time
- Per-wheel spring enable/disable switch, plus reset back to the vehicle's original spring values

### Body Force
- Edit the vehicle's BodyForce directly on X/Y/Z axes
- Type shorthand values like `50k`, `2.5m`, `1b` and it'll parse them
- Apply or remove the force with one click
- Warns you before letting absurdly high forces (100m+) through, with a skippable confirmation

### Wheels
- Detach/reattach individual wheel hinges
- "Detach all" / "reattach all" for the whole car at once

### Settings
- Toggle notifications on/off (including just the minimized-UI
