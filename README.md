# Gyrobot — driving simulator

A browser simulation of **Gyrobot**, a small spherical ground drone whose wheels
expand to drive. When the wheels retract the body is a compact ball; expanded, the
tread segments form a larger rolling circle and the robot moves.

**Live:** this repository is published with GitHub Pages — open the repository's
Pages URL and press *Start driving*.

## What is in here

```
index.html        landing page
sim/house.html    the simulator: a 15 x 11 m bungalow and garden to drive around
sim/room.html     an earlier single-room scene
sim/viewer.html   the assembly on a grid, with pose sliders and a part legend
sim/vendor/       three.js r147 (MIT), pinned, no CDN
sim/data/rig.json the rig: 64 objects, 14 poses, drivetrain ratios, checks
sim/meshes/       286 STL files, one per pose set, in millimetres
```

Everything is static: no build step, no server-side code, no tracking.

## Controls

| Key | Action |
|---|---|
| `W` `A` `S` `D` | drive and steer |
| `E` | expand or retract the wheels (one press, about three seconds) |
| `Space` | toggle boost, 1.8x speed |
| `Q` | open both panels |
| `C` | camera: chase, close, orbit |

There is also an on-screen pad and buttons, so it works on a touchscreen.

## The behaviour being simulated

The measured geometry says the chassis hangs **9.2 mm below the closed tread
circle**. The scene uses that directly:

- closed wheels: the chassis rests on the floor, the tread spins clear of it, and
  the robot cannot drive;
- expanding: ride height is the larger of the tread radius and the chassis drop,
  so the body lifts and the tread comes down;
- past about 3 mm of coupler stroke the tread is below the chassis and it rolls.

Ride height is read from the same pose table as the mesh data, so the changeover
happens where the real geometry changes over.

## Limits

Physics is collision rectangles only: no slopes, tipping, carpet drag or motor
dynamics. Lighting is flat. Furniture is composed from primitives and reads at
robot scale rather than in close-up. This is a mechanism visualisation you can
drive, not an engineering simulation.

## Running locally

Meshes are fetched, so it needs a web server rather than `file://`:

```sh
python -m http.server 8080
# http://127.0.0.1:8080/
```

## Licence

The viewer code in this repository is released under the MIT licence. The robot
design itself is a prototype; the CAD is not part of this repository.
