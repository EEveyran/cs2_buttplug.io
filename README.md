# cs2_buttplug.io
a simple light weight program made for intergrating pleasure with cs2
that uses node js
![alt text](https://cdn.discordapp.com/attachments/1478382277951098891/1507351706340692120/IMG_20260522_145512.jpg?ex=6a11962c&is=6a1044ac&hm=cc9def9831d5c6be1d8672929ab6f759d27f77f8b0f0c2c7ab726ab64060d957&)
# CS2 × buttplug

Control your buttplugbased on CS2 game events via Intiface Central.

## Events

| Event           | Behavior                                          |
|-----------------|---------------------------------------------------|
| 💣 Bomb planted  | Short pulse, then intensity ramps up as timer counts down |
| 💥 Bomb explodes | Max intensity burst                               |
| 🔵 Bomb defused  | Strong celebratory pulse                         |
| 🔫 Kill          | Medium pulse                                      |
| 💀 Death         | Full intensity burst                              |
| 🏆 Round win     | Strong sustained pulse                            |
| 😞 Round loss    | Soft short pulse                                  |
| 🌟 Ace           | Max intensity for 3 seconds                       |
| ⭐ MVP           | Strong pulse for 2.5 seconds                      |

---

## Prerequisites

- **Node.js** v18 or higher
- **Intiface Central** — download from https://intiface.com/central/
- **BLE buttplug** paired via Intiface
- **CS2** installed via Steam

---

## Setup

### 1. Install Intiface Central
1. Download and install from https://intiface.com/central/
2. Open it, go to **Settings** and make sure the WebSocket server port is `12345`
3. Click **Start Server**
4. Turn on your buttplug and click **Scan for Devices** — it should appear

### 2. Install this project
```bash
# Clone or copy this folder somewhere on your PC, then:
cd cs2-buttplug
npm install
```

### 3. Add the CS2 GSI config file
Copy `config/gamestate_integration_buttplug.cfg` to:
```
C:\Program Files (x86)\Steam\steamapps\common\Counter-Strike Global Offensive\game\csgo\cfg\
```

### 4. Run the server
```bash
npm start
```
You should see:
```
🎮 CS2 buttplug Integration
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📡 GSI server listening on port 3000
🔗 Connecting to Intiface at ws://127.0.0.1:12345...

✅ Device connected: to buttplug :D
```

### 5. Launch CS2 and play!

---

## Customizing Vibration Intensities

Edit the `CONFIG.vibration` block at the top of `src/index.js`:

```js
kill:        { intensity: 0.6, duration: 600  },  // 0.0–1.0, milliseconds
death:       { intensity: 1.0, duration: 1200 },
ace:         { intensity: 1.0, duration: 3000 },
// ...
```

## Status Page

While running, visit http://localhost:3000 to see connected devices and current game state.

---

## Troubleshooting

**"Could not connect to Intiface Central"**
→ Make sure Intiface Central is open and the server is **started** (green button), not just installed.

**Device not found**
→ Turn on silly buttplug :D first, then click Scan in Intiface. Make sure Bluetooth is on.

**No events firing in CS2**
→ Double-check the `.cfg` file is in the right CS2 folder. The path changed in CS2 vs CSGO.
→ Restart CS2 after adding the file.

**Vibration doesn't stop**
→ Restart the Node server (`Ctrl+C`, then `npm start`). The device will stop when disconnected.

