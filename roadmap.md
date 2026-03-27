# Infinite Sky — Roadmap & Project Scope

*Vibe Jam 2026 entry. Single-file HTML5 canvas game.*
*Last updated: Session 3 (2026-03-27)*

---

## What Has Been Built

### Core Game Loop
- **Canvas-based game** (a drawing surface in the browser where the game is rendered, 480×760px) — tap/click to fly upward, drift back down under gravity
- **5 Worlds** stacked vertically, each unlocked by altitude (height climbed):
  - 🌿 **Grassland** (0–2500m) — sunny, rain events, bees and boulders
  - 🏔 **Mountains** (2500–5000m) — misty, boulders and wind gusts
  - ☁️ **Clouds** (5000–8000m) — pale sky, lightning and wind
  - 🌌 **Atmosphere** (8000–11000m) — purple/magenta, meteors and lightning
  - 🚀 **Space** (11000m+) — black void, meteors and cosmic hazards
- **Health bar** drains continuously (faster at higher altitude) and from hazard hits
- **Altitude counter** tracks progress; displayed live on screen
- **Parallax backgrounds** (layered scrolling at different speeds to give depth) for all 5 worlds, using custom AI-generated background images

### Collectibles (items the player can pick up mid-flight)
| Item | Effect |
|------|--------|
| 🍲 Soup | Restores 30% health; warm glow effect on character |
| 💊 Medicine | Restores 13% health; happy face reaction |
| 🍎 Apple | Restores 15% health; head-bob animation |
| 🍌 Banana | Restores 20% health; body sway animation |
| 🍊 Orange | Restores 18% health; shiver animation |
| 🫐 Berries | Restores 25% health; joy animation + pink particle burst |
| 🧥 Jacket | Halves damage from cold-world hazards (Worlds 0–2) |
| 😷 Oxygen Mask | Required for Atmosphere world survival |
| 🚀 Space Suit | Required for Space world survival |
| 🎒 Backpack | Temporary 15s health drain reduction; red X-strap design on chest |
| 🧤 Gloves | Halves damage from hazards in Worlds 0–2; both-hands-raised reaction |
| 🥽 Goggles | Halves damage from hazards in Worlds 3–4; blink animation |
| 🎿 Shoes | Reduces bee and boulder damage by 40%; foot-tap animation |
| 👒 Beanie | Cosmetic; wobble head reaction |
| 🌂 Umbrella | Spawns during Grassland rain events; blocks rain health drain |

### Hazards (obstacles that damage the player)
- 🐝 **Bee** — fast horizontal enemy
- 🪨 **Boulder** — large falling rock
- ⚡ **Lightning** — sudden vertical strike
- 💨 **Wind** — horizontal push hazard
- ☄️ **Meteor** — high-altitude fast projectile

### Weather System
- **Grassland rain** — triggered every 30–60 seconds; 80 visible raindrop lines, heavier opacity when active; dark blue overlay during storm
- **Rain event** — spawns a collectible umbrella at screen top; drains health if caught without umbrella; ends after 10–15 seconds
- **Lightning in Clouds** — periodic flashes illuminating the whole screen + bolt visuals
- **Ambient sounds** per world — wind, rain, thunder

### Audio (Web Audio API — sound generated in code, no audio files)
- **Procedural music** (notes scheduled in advance using a synthesiser built in code) — different scale (major, minor, diminished, chromatic) and tempo per world
- **Heartbeat effect** — plays when health is critically low
- **World transition stings** — short musical flourish when entering a new world
- **Dramatic silence** — music fades out at very high altitude before the ending
- **SFX for every collectible** — unique sound for each item

### Character & Animations
- **Drawn entirely in code** (no sprite images) — body, head, hair, face expressions
- **Reaction system** — collect an item → character plays a unique animation for ~0.8s
  - Medicine: raised brows + big smile
  - Goggles: eyes squeeze shut (blink)
  - Berries: joy closed-eyes expression
  - Apple: head bobs forward and back
  - Banana: whole body sways side to side
  - Orange: rapid shiver
  - Beanie: head wobble
  - Gloves: both hands raise up
  - Shoes: rapid foot tap
- **Backpack** — drawn behind torso as a red pack; two X-crossing straps drawn over the front of the chest
- **Umbrella** — right arm raises to hold stick; dome canopy drawn above head with ribs and tip; disappears when rain ends

### Ending Sequence
- At maximum altitude: dramatic slowdown, music silence
- **Twist ending** — reveals the whole journey was a child dreaming; illustrated ending screen
- Restart button to play again

### Difficulty Scaling
- **Spawn rate** (how often hazards appear) increases +10% per 1000m altitude
- **Hazard speed** increases +10% per 2000m altitude
- **New hazard types unlock** every 3000m — each world gains access to additional enemy types progressively

### Mobile Support
- On-screen left/right arrow buttons for touch devices
- Touch events wired to match keyboard controls

---

## Known Outstanding Issues
1. **Umbrella persists across worlds** — umbrella item can appear in Mountains if rain started in Grassland and world transition occurs before rain ends
2. **Rain visibility** — improved but may need further tuning depending on display brightness

---

## Possible Future Work (Not Committed)
- Power-up combining (e.g. gloves + jacket = extra bonus)
- Leaderboard / score sharing
- Additional world (Nebula / deep space)
- Animated parallax clouds reacting to wind hazards
