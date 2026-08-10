# Crazy Pong

**The classic Pong arcade game — with a twist.**

> ⚠️ This game is currently in active development and subject to change.

Play it live at **[crazypong.org](https://crazypong.org)**

---

## Overview

Crazy Pong is a browser-based Pong game built entirely in HTML, CSS, and JavaScript — no frameworks, no dependencies beyond PeerJS for online multiplayer. It takes the classic two-paddle concept and layers on power-ups, obstacles, multiple game modes, an account system with persistent stats, and full mobile/touch support.

---

## Game Modes

### VS Computer
Play against an AI opponent across three difficulty levels:

- **Easy** — slow reaction time, gets confused by power-ups, occasional misses
- **Medium** — moderate reaction time, partially affected by power-ups
- **Hard** — instant reaction with full ball trajectory prediction, fully compensates for power-ups after a brief hesitation

### 2 Players (Local)
Two players on the same device. On touch screens, a second set of arrow buttons appears above the canvas for Player 2 so both players can use touch controls simultaneously.

### Multiplayer (Online)
Real-time online play via PeerJS/WebRTC — no server required. One player hosts and shares a room code, the other joins. Features include:
- In-game chat (press T)
- Host pause control
- Automatic reconnect detection
- Stat recording for logged-in players

### Lab Mode
A sandbox environment for testing power-ups. Toggle any combination of effects on or off for either player and watch them interact in real time. AI difficulty can be changed mid-session from Easy, Medium, or Hard.

---

## Power-Ups

Power-ups appear on the field after the first asteroid spawns and are collected by hitting them with the ball. Up to 3 power-ups can be on the field at a time.

| Power-Up | Effect |
|----------|--------|
| **WIDE** | Increases the collecting player's paddle width |
| **CURVE** | Shots curve based on where the ball hits the paddle — edge hits curve more than center hits |
| **POWER** | Boosts ball speed on hit; combines with CURVE for 65% stronger curve |
| **SPLIT** | Spawns a ghost decoy ball. On spawn there is a 50/50 chance the real ball and ghost ball swap trajectories |
| **SHRINK** | Shrinks the opponent's paddle |
| **REVERSE** | Flips the opponent's movement controls. The AI hesitates before reacting and again when the effect wears off |

All power-ups can be individually toggled on or off in the Settings menu. Settings are saved to your account if logged in.

---

## Obstacles (Asteroids)

Asteroids spawn into the field every 6 paddle hits, up to a maximum of 4 at a time. Each asteroid is procedurally generated with:

- A randomized polygon shape (6–9 vertices)
- A base radius between 15–26 units
- Random direction and fixed movement speed
- A dynamic trail that follows the actual trajectory including wall bounces

The ball physically collides with asteroids using SAT (Separating Axis Theorem) collision detection, deflecting the ball and pushing the asteroid on impact.

---

## Visual Effects

All visual effects can be toggled on or off individually in Settings:

- **Ball Trail** — smooth tapered trail behind the ball that curves through direction changes
- **Screen Shake** — brief camera shake on asteroid collisions
- **Particle Burst** — particle explosion when a power-up is collected

---

## Account System

Create a free account to save your settings and track your stats across devices and sessions.

### Creating an Account
Click **LOGIN** on the main menu. Username must be 3+ characters. Passwords are hashed client-side with SHA-256 before being sent — plain text passwords are never transmitted or stored.

### Remember Me
Check **Remember Me** on login to stay signed in across browser sessions using localStorage. Logging out clears the stored credentials immediately.

### Saved Settings
The following settings sync automatically to your account whenever changed:
- Volume level
- Win score / point limit
- Individual power-up toggles (Wide, Curve, Power, Split, Shrink, Reverse)
- Visual toggles (Ball Trail, Screen Shake, Particle Burst)

### Stats
Click **STATS** on the main menu to view your record. Stats are tracked separately per difficulty and game mode:

**VS Computer:**
- Wins, losses, and win rate per difficulty (Easy / Medium / Hard)

**Multiplayer:**
- Overall wins, losses, and win rate
- Recent opponent history (opponent username and match result) — only recorded if the opponent was also logged in

---

## Controls

### Keyboard
| Action | Player 1 (Top) | Player 2 (Bottom) |
|--------|---------------|-------------------|
| Move Left | A | ← |
| Move Right | D | → |
| Pause | Space | Space |
| Quit | Escape | Escape |
| Chat (MP) | T | T |

### Touch / Mobile
Arrow buttons appear below the canvas (and above in 2P mode for Player 2). Touch mode activates automatically when the screen is tapped; keyboard mode restores when any key is pressed. On touchscreen laptops both modes are available and switch dynamically.

### Fullscreen
A fullscreen button is available in the top-left corner of the game area during gameplay.

---

## Settings

Accessible from the main menu via the **SETTINGS** button.

- **Volume** — master volume slider for all sound effects
- **Win Score** — points needed to win a game (3–11), separately configurable for VS Computer, 2 Players, and Multiplayer
- **Power-Up Toggles** — enable or disable individual power-ups from appearing in games
- **Visual Toggles** — enable or disable Ball Trail, Screen Shake, and Particle Burst

---

## Technical Notes

- Built with vanilla HTML5 Canvas, CSS, and JavaScript — no build tools or frameworks
- Online multiplayer uses [PeerJS](https://peerjs.com/) (WebRTC) for peer-to-peer connections
- Account data and feedback are stored in Google Sheets via Google Apps Script web apps
- Fully compatible with sandboxed iframe environments (Google Sites) as well as standalone hosting
- Google Analytics (G-6G72V1D95D) is used for traffic monitoring

---

## Feedback

Have a suggestion or found a bug? Visit **[crazypong.org/feedback.html](https://crazypong.org/feedback.html)** to leave a rating and comment.

---

*Developed by [ivanpowell0606](https://github.com/ivanpowell0606) · Built via Vibe Coding (AI-assisted development driven by human prompts)*
