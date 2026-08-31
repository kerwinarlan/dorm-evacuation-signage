# Sampaguita Dormitory Floorplan Coordinate Template

Use this Markdown template to define rooms, zones, and spatial layouts for Canva or web map rendering.

---

## Canvas Calibration & Scale
* **Base Resolution:** `1000px` (Width) x `700px` (Height)
* **Coordinate Origin:** Top-Left `(0, 0)`
* **Direction Standard:** Counter-Clockwise (CCW) starting from Top-Left Corner

---

## 1. Room / Zone Definitions

### Zone 1: Main Lobby / Entrance
* **Zone ID:** `LOBBY_01`
* **Label:** Main Lobby & Registration Desk
* **Corners (CCW):**
  * Corner 1 (Top-Left): `(100, 100)`
  * Corner 2 (Bottom-Left): `(100, 300)`
  * Corner 3 (Bottom-Right): `(400, 300)`
  * Corner 4 (Top-Right): `(400, 100)`
* **Notes:** Location for GA Registration Table & Candy Station.

---

### Zone 2: Main Social Hall / GA Stage
* **Zone ID:** `STAGE_01`
* **Label:** General Assembly Main Hall
* **Corners (CCW):**
  * Corner 1 (Top-Left): `(450, 100)`
  * Corner 2 (Bottom-Left): `(450, 500)`
  * Corner 3 (Bottom-Right): `(900, 500)`
  * Corner 4 (Top-Right): `(900, 100)`
* **Notes:** Main venue for Spider-Man Akwe party, performance stage, and games.

---

### Zone 3: Interactive Bulletin Board Area
* **Zone ID:** `BOARD_01`
* **Label:** Spider-Man Interactive Wall
* **Corners (CCW):**
  * Corner 1 (Top-Left): `(100, 350)`
  * Corner 2 (Bottom-Left): `(100, 450)`
  * Corner 3 (Bottom-Right): `(350, 450)`
  * Corner 4 (Top-Right): `(350, 350)`
* **Notes:** Location for red/blue paper square station & prompt wall (*"If you were forgotten..."*).

---

### Zone X: [Insert Room Name]
* **Zone ID:** `ROOM_X`
* **Label:** [Insert Description]
* **Corners (CCW):**
  * Corner 1: `(x1, y1)`
  * Corner 2: `(x2, y2)`
  * Corner 3: `(x3, y3)`
  * Corner 4: `(x4, y4)`
* **Notes:** [Add operational details]

---

## 2. Quick JSON Format (Optional for Web/Canvas Scripts)

```json
[
  {
    "zone": "LOBBY_01",
    "name": "Main Lobby",
    "points": [{"x": 100, "y": 100}, {"x": 100, "y": 300}, {"x": 400, "y": 300}, {"x": 400, "y": 100}]
  },
  {
    "zone": "STAGE_01",
    "name": "GA Main Hall",
    "points": [{"x": 450, "y": 100}, {"x": 450, "y": 500}, {"x": 900, "y": 500}, {"x": 900, "y": 100}]
  }
]
```
