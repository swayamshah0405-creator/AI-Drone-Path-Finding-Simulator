# Aero-Wumpus: AI Drone Dynamic Pathfinding Simulator

Browser-based drone pathfinding simulator on a Wumpus-World-style grid. Compare manual control, an
A* risk-aware planner and a Q-Learning agent as they dodge moving mines and grab power-ups.

**Live demo:** https://swayamshah0405-creator.github.io/AI-Drone-Path-Finding-Simulator/
*(available once GitHub Pages is enabled for this repo)*

## Overview

A drone has to reach a landing pad on a grid while a mine and flanking obstacles move to cut it off. You can
fly it yourself, let an **A\* planner** with risk-aware heuristics replan around threats every step,
or train a **Q-Learning agent** from scratch and watch it improve episode by episode.

Power-ups spawn on the map. The landing pad can move away from the drone, and a live telemetry panel
shows rewards, goal distance, the Q-values of the current state and a win-rate chart.

It is a single HTML file with no build step and no install.

## Controller modes

| Mode | How it works |
|---|---|
| **Manual Control** | Fly the drone with WASD / arrow keys or the on-screen thrust buttons |
| **A\* Risk & Power AI** | A\* search with a Manhattan-distance heuristic and danger-weighted step costs around the mine and moving obstacles. A one-step lookahead keeps the drone off any tile a hazard can reach next turn, and it detours for power-ups when threatened. Replans every step |
| **Q-Learning RL Agent** | Model-free tabular Q-Learning with an ε-greedy policy. Includes a **Fast Train (300 episodes)** button and tunable α, γ and ε-decay |

## Power-ups

| Power-up | Effect |
|---|---|
| **Freeze** | Hazards stop moving for 3 steps |
| **Blink** | The drone moves up to 2 tiles per step for 3 steps |
| **Shockwave** | Pushes the mine 3 tiles away and destroys adjacent obstacles |

## Reward matrix

| Event | Reward |
|---|---|
| Landing on the goal | +500 |
| Collision with the mine or an obstacle | −500 |
| Picking up a power-up | +50 |
| Moving closer to / away from the goal | +2 / −2 |

## Configurable environment

- Grid size: 8×8 to 20×20
- Number of obstacles: 1 to 10
- Hazard move interval: every 1 to 4 steps
- Power-up spawn count: 0 to 6
- Simulation speed: 1 to 30 steps/second
- Evasive goal pad: on or off

## Running it

Open `index.html` in any modern browser. An internet connection is needed to load Tailwind CSS,
Chart.js, Font Awesome and Google Fonts from their CDNs.

## Tech stack

HTML5 Canvas · JavaScript · Tailwind CSS · Chart.js · Font Awesome
