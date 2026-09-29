🌿 VERDANT — A Growing Journey

A 2D arcade game where you guide a living vine to bloom in every 
---

📖 About

VERDANT is a browser game where you control a living vine. Unlike most arcade games, there is no shooting, no jumping, and no attack button. Your only tool is mouse movement — and the vine chases the cursor's light with a momentum-based physics chain.

The goal is simple but demanding:
Collect every dew droplet, avoid the thorns, and reach the golden blossom — before your vitality runs dry.

---

✨ Features

· 🌱 Physics chain mechanic — the vine's body is a dynamic chain of hundreds of segments using follow-the-leader motion
· 💧 Dual resource — the vine's length is its life; it constantly drains and refills with dew
· 🌪️ Dynamic wind — later levels push the vine off course with wind currents
· 🌵 Thorns — not just obstacles; they damage you and knock the head backward
· 🎨 Organic visual style — warm parchment palette, no neon, no space
· 🎵 Soft synthesized audio — no audio files; everything is generated via Web Audio API
· 💾 Auto-save — best times and unlocked levels stored in localStorage
· 📱 Fully responsive — plays the same on mobile and desktop
· 🚀 Single file, no build — just one index.html

---

🎮 Controls

Input Action
🖱️ Mouse move / Touch Guide the vine's head
Space Start game / continue
P or Esc Pause / resume
R Restart level

Note: The vine has momentum. You can't turn instantly — plan your path ahead.

---

🧠 Core Mechanics

1. Momentum Steering

The vine's head turns toward the cursor at a maximum turn rate (MAX_TURN = 5.2 rad/s). It handles like a vehicle, not a point — you must commit to turns early.

2. Vitality

The vine's body length is its health. It drains constantly (DRAIN_RATE = 48 px/s). Each dew droplet (DROPLET_VALUE = 300) restores roughly a third of max vitality.

3. The Vine Chain

The body is made of up to 220 segments (MAX_SEGMENTS) spaced 5px apart. Each segment follows the one before it, producing natural wave-like motion.

4. Collisions & Feedback

· Dew → gain vitality + blue particle burst
· Thorn → lose vitality + head pushed outward + screen shake
· Flower → only blooms once every droplet is collected, ending the level

---

🗺️ Levels

The game ships with 6 gardens (Sectors) of increasing difficulty:

# Name Par Feature
01 First Sprout 15s Basics — no thorns, no wind
02 Thirsty 20s Long, winding path
03 Thornfield 22s First encounter with thorns
04 Crosswind 24s Vertical wind that shifts your path
05 The Long Way 28s Horizontal wind + dense thorns
06 Bloom 32s Final challenge — wind, thorns, complex route

Each level awards up to three stars:

· ⭐⭐⭐ if time ≤ par
· ⭐⭐ if ≤ 1.7 × par
· ⭐ otherwise

---

🛠️ Install & Run

Easiest way: download the file and open it in your browser.

```bash
git clone https://github.com/your-username/verdant.git
cd verdant
open index.html        # macOS
# or:  start index.html   (Windows)
# or:  xdg-open index.html (Linux)
```

No npm install, no build step, no server, no dependencies.

Optional local server

```bash
python -m http.server 8000
# then visit http://localhost:8000
```

---

📁 Project Structure

```
verdant/
├── index.html      ← the entire game: HTML + CSS + JS in one file
└── README.md
```

Main sections inside the file

Section Purpose
<style> All CSS — palette, UI, animations
LEVELS Array of level data (droplets, thorns, flower, wind)
updateVine() Vine physics and steering
checkCollisions() Dew, thorn, and flower collision handling
render() Draws the whole scene
drawVine() Renders the body, leaves, and head
loop() Main loop using requestAnimationFrame

---

⚙️ Customization

All key parameters live at the top of the <script> tag:

```javascript
const SEG_SPACING   = 5;      // spacing between vine segments
const MAX_SEGMENTS  = 220;    // max number of segments
const HEAD_SPEED    = 275;    // head speed (px/s)
const MAX_TURN      = 5.2;    // turn rate (rad/s) — main difficulty knob
const MAX_LENGTH    = 1000;   // max vitality
const DRAIN_RATE    = 48;     // vitality drain (px/s)
const DROPLET_VALUE = 300;    // value of each dew droplet
const THORN_DAMAGE  = 380;    // damage per thorn
```

Adding a new level

Just append an object to LEVELS:

```javascript
{
  name: 'MY GARDEN', par: 20,
  start:  { x: 200, y: 450 },
  flower: { x: 1400, y: 450 },
  droplets: [ {x:500,y:450}, {x:800,y:300}, {x:1100,y:450} ],
  thorns: [ {x:700,y:600,r:60} ],
  wind: {x:0, y:60}
}
```

Changing the visual style

The palette lives inside drawBackground() and the draw functions. For example:

· Watercolor: paper-white background + translucent washes
· Paper cutout: flat colors + hard shadows
· Night: deep indigo background + glowing vine

---

🌐 Browser Support

Browser Status
Chrome / Edge ✅ Full
Firefox ✅ Full
Safari ✅ Full
Safari iOS ✅ (touch)
Chrome Android ✅ (touch)

Uses Web Audio API and localStorage, both supported in all modern browsers.

---

🚧 Roadmap Ideas

If you want to extend the game:

☐ Branching mechanic — vine can split into two branches
☐ Bothering insects — moving enemies you must avoid
☐ Bouncing mushrooms — teleport to another spot on the map
☐ Endless mode — infinite garden with progressive difficulty
☐ Dynamic background music — intensity based on vitality
☐ Online leaderboard — compete with friends
☐ Level editor — build your own gardens

---

🤝 Contributing

If you have an idea, found a bug, or built a new level:

1. Fork the repo
2. Create a branch (git checkout -b feature/my-idea)
3. Commit (git commit -m 'Add my idea')
4. Push (git push origin feature/my-idea)
5. Open a Pull Request

---

📜 License

MIT License — free to use, modify, and distribute. Just keep the original name.

---

🙏 Credits

Made with ❤️ and zero libraries.
If you enjoyed it, drop a ⭐ on the repo!

"The vine has grown through every garden. It has earned its rest." 🌿
