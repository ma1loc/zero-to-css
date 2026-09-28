# Nokia Lumia UI Grid

A replica of the iconic **Windows Phone / Nokia Lumia "Metro" live tile interface**, built from scratch using **pure HTML & CSS Grid** as part of the **Zero to CSS** learning journey (Day 2).

<p align="center">
  <img src="./nokia-ui.png" alt="Nokia Lumia UI Grid with CSS Grid DevTools Overlay" width="100%">
</p>

---

## Project Overview

The goal of this project was to master **CSS Grid** fundamentals by translating a complex, multi-sized grid interface into clean, precise code without external frameworks or libraries.

### Key Concepts Practiced:
- **CSS Grid Layout**: Building a fixed 8-column by 16-row layout (`repeat(8, 50px)` / `repeat(16, 50px)`).
- **Coordinate Mapping**: Positioning different tile sizes using `grid-area: row-start / col-start / row-end / col-end`.
- **CSS Box Model**: Resetting margins, padding, and mastering `box-sizing: border-box`.
- **CSS Variables (`:root`)**: Centralizing color themes (background, tile borders, text).
- **Layer Overlays with `z-index`**: Stacking notification badges directly on top of app tiles within the grid.

---

## Grid Layout Architecture

The container is structured on an **8 × 16** grid (each unit is 50px × 50px with a 2px gap):

| Element | Grid Area (`row-start / col-start / row-end / col-end`) | Dimensions (Tiles) |
| :--- | :--- | :--- |
| **Phone** (`.item1`) | `1 / 1 / 5 / 5` | Large (4 × 4) |
| **Chat** (`.item2`) | `1 / 5 / 3 / 7` | Medium (2 × 2) |
| **Office** (`.item7`) | `1 / 7 / 3 / 9` | Medium (2 × 2) |
| **People** (`.item6`) | `3 / 5 / 5 / 7` | Medium (2 × 2) |
| **Mail** (`.item4`) | `3 / 7 / 5 / 9` | Medium (2 × 2) |
| **Browser** (`.item5`)| `5 / 1 / 8 / 4` | Square (3 × 3) |
| **Studio** (`.item8`) | `5 / 4 / 6 / 5` | Small (1 × 1) |
| **Compass** (`.item9`)| `6 / 4 / 7 / 5` | Small (1 × 1) |
| **Car** (`.item10`) | `7 / 4 / 8 / 5` | Small (1 × 1) |
| **Camera** (`.item12`)| `8 / 1 / 9 / 3` | Wide (2 × 1) |
| **Music** (`.item11`) | `8 / 3 / 9 / 5` | Wide (2 × 1) |
| **Store** (`.item3`) | `5 / 5 / 9 / 9` | Large (4 × 4) |
| **Empty Space** (`.empty-space`) | `9 / 1 / 17 / 9` | Section (8 × 8) |

### Badges & Overlays
- **Phone Notification Badge**: Placed at `grid-area: 2 / 3 / 3 / 4` with `z-index: 1` to overlap the Phone tile.
- **Store Warning Badge**: Placed at `grid-area: 6 / 7 / 7 / 8` with `z-index: 1` to overlay the Store tile.

---

## Project Structure

```text
nokia-ui-grid/
├── index.html        # HTML structure & tile elements
├── style1.css        # Base styles, CSS variables, reset & container styling
├── style2.css        # CSS Grid definitions and explicit tile coordinates
├── nokia-ui.png      # Screenshot with Firefox/Chrome Grid DevTools overlay
├── Public/           # Visual assets
│   ├── app-icons/         # Metro app tile SVG icons
│   └── background-icons/  # Notification & warning badge SVGs
└── README.md         # Project documentation
```

---

## Key Learnings & Takeaways

1. **CSS Grid Placement Syntaxes**:
   - Longhand: `grid-row-start`, `grid-row-end`, `grid-column-start`, `grid-column-end`
   - Shorthand: `grid-row: 1 / 5;` and `grid-column: 1 / 5;`
   - Compact shorthand: `grid-area: row-start / col-start / row-end / col-end;`
2. **Shorthand Property Caveats**:
   - Writing `border: solid ...` after `border-width: 10px` overwrites the width with the default `medium`. Combining into `border: 10px solid var(--blackColor);` keeps the rule intact.
3. **Explicit Placement vs. Auto-flow**:
   - While `grid-auto-flow: row` can automatically place items in remaining gaps, explicitly declaring `grid-area` prevents the layout from shifting unexpectedly if HTML order changes.

---

## Note

> [!NOTE]
> This project was built for educational purposes to master fixed grid geometry and tile positioning. Responsive design (using `fr` units, `minmax()`, and media queries) will be explored in upcoming projects.
