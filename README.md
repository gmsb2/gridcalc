# GridCalc 🧮

**A drawer grid layout calculator and bin planner for Gridfinity and custom foam inserts.**

Paste in your drawer dimensions, pick your grid size, and GridCalc figures out how many full grids fit — handling edge gaps and trim strips automatically. Then hop to the Bin Planner to lay out numbered bins on your grid.

---

## ✨ Features

### 🧮 Calculator (Page 1)
- Enter drawer **width** and **depth** in mm (or inches — auto-converted)
- Enter your **grid cell size** (e.g. 42 mm for Gridfinity)
- **Symmetric grid** checkbox mirrors X→Y automatically
- Calculates full grid count + leftover for each axis:
  - **Gap** — remainder < ½ grid → even gaps on each side
  - **Trim** — remainder > ½ grid → rounds up, trims outer cells
- **Visual canvas** with color-coded zones:
  - 🟢 Center (dark green) — full-size grid cells inside the zone boundary
  - 🔵 Side Trim (blue) — edge strips or trimmed outer cells
  - 🟠 Rear Trim (amber) — rear gap filler or trimmed rear row
  - 🟡 Yellow dashed line — zone boundary encompassing all grid pieces
- **Print Pieces** table — section dimensions, wide × high counts, and total piece count

### 📦 Bin Planner (Page 2)
- Imports grid layout from the Calculator automatically
- Click or arrow-key ghost bins into position
- **Half-unit positioning** (0.5 grid increments)
- Bins can start in the rear ½-row and extend forward
- Overlap detection — red ghost = can't place
- **Bin log** with coverage bar showing % of grid used
- Remove individual bins or clear all
- Keyboard: **↑↓←→** move ghost · **Enter** place · **Esc** cancel

---

## 🚀 Usage

GridCalc is a **single-file app** — no install, no server, no dependencies.

1. [Download `index.html`](https://github.com/gmsb2/gridcalc/raw/main/index.html)
2. Open it in your browser
3. That's it

Or open it directly:  
👉 **[https://gmsb2.github.io/gridcalc/](https://gmsb2.github.io/gridcalc/)**

---

## 📐 How It Works

### Grid math
For each axis (width / depth):

```
exactFit  = drawerDimension / gridSize
fullGrids = floor(exactFit)
remainder = drawerDimension - fullGrids × gridSize

if remainder > gridSize / 2:
    fullGrids += 1          ← round up
    trimPerSide = excess / 2   ← trim outer pieces
else:
    gapPerSide = remainder / 2 ← even gap each side
```

### Piece types
| Type | When | Dimensions |
|------|------|------------|
| **Center** | Always | full `W × H` cells |
| **Rear Trim** | Any rear remainder | strip or trimmed rear row |
| **Side Trim (×2)** | Any side remainder | strip or trimmed outer columns |

---

## 📸 Screenshot

![GridCalc screenshot](https://raw.githubusercontent.com/gmsb2/gridcalc/main/screenshot.png)

*(Add your own screenshot as `screenshot.png` if you'd like!)*

---

## 🛠 Built With

- Vanilla HTML + CSS + Canvas — zero dependencies
- Single `index.html` file, works offline

---

## 📄 License

MIT — free to use, share, and modify.
