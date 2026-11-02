# Gyrobot — driving simulator

A browser simulation of **Gyrobot**, a small spherical ground drone whose wheels
expand to drive. Closed, the body is a compact ball; opened, the tread segments
form a larger rolling circle and it moves.

Open `index.html` (or the Pages URL) and press **Play**.

## Controls

| Key | Action |
|---|---|
| `W` `A` `S` `D` | drive and steer |
| `E` | expand or retract the wheels (about three seconds) |
| `Space` | toggle boost, 1.8x |
| `Q` | open both panels |
| `C` | camera: chase, close, orbit |

## The behaviour being simulated

The measured geometry says the chassis hangs 9.2 mm below the closed tread
circle. With the wheels closed the chassis rests on the floor, the tread spins
clear of it and the robot cannot drive. Ride height is the larger of the tread
radius and the chassis drop, so expanding the wheels lifts the body and brings
the tread down; past about 3 mm of stroke it rolls. Ride height is read from the
same pose table as the mesh data.

## Files

```
index.html      landing panel over the live scene, then the simulator
room.html       the earlier single-room scene
viewer.html     the assembly on a grid, with pose sliders
vendor/         three.js r147 (MIT), pinned locally
data/rig.json   61 objects, 14 poses, drivetrain ratios, checks
meshes/         283 STL files in millimetres
```

## Limits

Collision is rectangles only: no slopes, tipping, carpet drag or motor dynamics.
Lighting is flat, and the furniture is built from primitives. This is a mechanism
visualisation you can drive, not an engineering simulation.

## Licence

Viewer code MIT. The robot design is a prototype; the CAD is not in this
repository.
