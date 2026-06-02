<div align="center">

# 🐍 Snake Game

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)
[![Live Demo](https://img.shields.io/badge/Live%20Demo-Available-brightgreen?style=flat-square)](https://yeabtsega-tesfaye.github.io/snake-game)

A browser-based implementation of the classic Snake game — built from scratch using vanilla HTML, CSS, and JavaScript, with no frameworks or libraries. Focus was on understanding core web fundamentals: DOM manipulation, the game loop pattern, event-driven input handling, and collision detection logic.

[Play Now →](https://yeabtsega-tesfaye.github.io/snake-game)

</div>

---

## Preview

[ assets/gameplay.gif ]

---

## Live Demo

The game is playable directly in the browser — no setup required.

🔗 **[https://yeabtsega-tesfaye.github.io/snake-game](https://yeabtsega-tesfaye.github.io/snake-game)**

> If the link is not yet live, follow the [local setup instructions](#installation) below.

---

## Overview

This project is a clean, self-contained implementation of Snake built with pure front-end technologies. The game renders onto a CSS grid-based board using dynamic DOM element creation and manipulation. All game state — including the snake's position, food placement, movement direction, and score — is managed entirely in JavaScript.

The primary goal was to practice and demonstrate core JavaScript concepts in a real, interactive context rather than a contrived exercise.

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Markup | HTML5 |
| Styling | CSS3 |
| Logic | Vanilla JavaScript (ES6+) |
| Icons | Font Awesome 6 |
| Persistence | `localStorage` (high score) |

No build tools. No bundlers. No frameworks. Just the platform.

---

## Features

- **DOM-based rendering** — the game board is a grid of dynamically created and updated HTML elements, not a Canvas
- **Persistent high score** — saved to `localStorage` and displayed across sessions
- **Touch controls** — on-screen directional buttons using Font Awesome icons with `data-key` attributes, enabling mobile play
- **Keyboard controls** — full arrow key support for desktop play
- **Real-time score tracking** — score updates immediately on food consumption
- **Collision detection** — wall boundaries and self-collision both trigger game over
- **Clean responsive layout** — centered, playable across screen sizes

---

## Controls

| Input | Action |
|-------|--------|
| `↑` Arrow Key | Move Up |
| `↓` Arrow Key | Move Down |
| `←` Arrow Key | Move Left |
| `→` Arrow Key | Move Right |
| On-screen buttons | Same directions (touch/mobile) |

> **Note:** Reversing direction into the snake's own body is not permitted — the input is ignored.

---

## Project Structure

```
snake-game/
├── index.html      # Game layout: board, score display, touch controls
├── style.css       # Visual styling, grid layout, responsive design
└── script.js       # All game logic: loop, movement, collision, scoring
```

The project intentionally uses a flat, minimal structure — appropriate for a single-page vanilla JS application of this scope.

---

## Game Logic

<details>
<summary><strong>How the core systems work</strong></summary>

### Game Loop

The game runs on a `setInterval`-based loop. Each tick, the snake's position is recalculated, the DOM is updated to reflect the new state, and collision checks are evaluated. The interval speed determines the difficulty.

```js
// Conceptual structure
setInterval(() => {
  updateSnakePosition();
  checkCollisions();
  renderBoard();
}, GAME_SPEED);
```

### DOM Rendering

Rather than using the HTML5 Canvas API, the board is built from individual `div` elements inside a `.play-board` container. Each tick, the board is re-rendered by adding and removing CSS classes (e.g. `snake-head`, `food`) on the relevant cells.

### Collision Detection

Two types of collisions are checked on every tick:

1. **Wall collision** — if the snake's head position exceeds the grid boundaries, the game ends.
2. **Self collision** — the snake's head position is compared against all existing body segment positions. A match triggers game over.

### Food Placement

Food is placed at a randomly generated grid coordinate. The coordinate is recalculated whenever the snake consumes the current food item.

### Score & High Score

The current score increments by 1 each time food is consumed. After game over, the score is compared to the value stored in `localStorage`. If it's higher, the stored value is updated — persisting the high score across page reloads.

### Input Handling

A `keydown` event listener captures arrow key presses and updates the current movement direction. The on-screen touch buttons use `click` event listeners with `data-key` attributes that mirror the same key values, routing through the same direction-update logic.

</details>

---

## Challenges & Lessons Learned

<details>
<summary><strong>Expand</strong></summary>

**DOM updates vs. Canvas rendering**
Choosing DOM manipulation over Canvas meant thinking carefully about how to efficiently re-render the board state each tick without causing unnecessary reflows.

**Input buffering**
Handling rapid key presses — particularly when the player changes direction faster than one tick — required guarding against invalid direction reversals (e.g. going left when currently moving right).

**Coordinate system**
Managing the snake as an array of `{x, y}` positions and keeping that in sync with what's rendered on screen required careful thinking about state — what's the source of truth, and when does the DOM get updated to reflect it.

**High score persistence**
Introducing `localStorage` for the first time highlighted the separation between in-memory session state and persistent state.

</details>

---

## Future Improvements

- [ ] **Difficulty levels** — expose game speed as Easy / Medium / Hard selection
- [ ] **Pause / Resume** — toggle game loop with a key press (`Space` or `P`)
- [ ] **Animated transitions** — CSS transitions on snake growth and food spawn
- [ ] **Sound effects** — audio feedback on food consumption and game over
- [ ] **Wrap-around mode** — walls become portals instead of collision zones
- [ ] **Mobile swipe detection** — replace on-screen buttons with swipe gesture recognition
- [ ] **Score multiplier** — consecutive food items without changing direction award bonus points

---

## Installation

No dependencies, no build step.

```bash
# Clone the repository
git clone https://github.com/Yeabtsega-Tesfaye/snake-game.git

# Navigate into the project directory
cd snake-game

# Open in browser
open index.html
```

Or simply open `index.html` directly in any modern browser.

> Tested in Chrome, Firefox, and Edge. Requires a browser with ES6 support.

---

## Author

**Yeabtsega Tesfaye**

[![GitHub](https://img.shields.io/badge/GitHub-Yeabtsega--Tesfaye-181717?style=flat-square&logo=github)](https://github.com/Yeabtsega-Tesfaye)

---

<div align="center">

If this project was useful or interesting to you, consider leaving a ⭐

</div>
