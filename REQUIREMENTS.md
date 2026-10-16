# Requirements: Gas in a Box (PoC)

## Goal
A graphical analogy of a gas in a box. Molecules are drawn as circles and move according to simple 2D physics. Heat input at the bottom and cooling at the top create an energy flow.

## Functional Requirements

### Box
- FR-1: A square 2D box is displayed.
- FR-1a: A slider controls the box side length; changes take effect live and molecules outside the new bounds are moved inside.
- FR-2: The box is empty at start (no molecules).

### Molecules
- FR-3: Each molecule is a circle with its own radius, position and velocity vector.
- FR-4: A molecule's radius equals the size slider value at creation time; different sizes come from changing the slider between molecules.
- FR-5: Mass is proportional to the circle area (r²).
- FR-6: A new molecule appears at a random free position (no overlap) with a random direction and an initial speed matching the mean temperature.

### Collisions
- FR-7: Collisions between two circles are elastic (momentum and energy conserved, taking masses into account).
- FR-8: Collisions with the side walls (left, right) are elastic (reflection).
- FR-9: Collisions with the top and bottom walls also reflect, plus the wall temperature effect applies (see Thermostats).
- FR-10: Overlaps are resolved after a collision (position correction).

### Thermostats
- FR-11: The bottom wall has a temperature T_bottom (hot), the top wall a temperature T_top (cold).
- FR-12: When a molecule hits a wall, its speed is adjusted towards that wall's temperature: at a high wall temperature it gains kinetic energy, at a low one it loses energy.
- FR-13: The left and right walls are insulating (purely elastic, no energy exchange).
- FR-14: If both temperatures are equal, the system reaches equilibrium on average.

### Controls
- FR-15: A "New Molecule" button adds one molecule.
- FR-16: A slider controls molecule size (radius range or scale) for newly created molecules.
- FR-17: A slider controls T_bottom.
- FR-18: A slider controls T_top.
- FR-18a: A slider controls gravity strength (0 = off).
- FR-18b: Temperatures use a relative scale of 0-100 (no physical units).
- FR-19: Slider changes take effect immediately (live).
- FR-20: Current slider values are shown numerically.

### Display
- FR-21: The animation runs continuously (e.g. requestAnimationFrame) using a time-step based simulation.
- FR-22: Optional: molecules are colored by kinetic energy (cold = blue, hot = red).
- FR-23: Optional: display molecule count and mean kinetic energy.

## Non-Functional Requirements
- NFR-1: Delivered as a single HTML file with embedded JavaScript and Canvas; no backend, no build step, no external dependencies.
- NFR-2: Smooth rendering (~60 FPS) with at least 200 molecules.
- NFR-3: Simulation is independent of the frame rate (fixed or capped time steps).
- NFR-4: Gravity is off by default (slider at 0).

## Out of Scope (PoC)
- Removing molecules, reset button, save/load.
- 3D, circle rotation, inelastic collisions.
- Entropy calculation and display (future extension).

## Open Questions
None.
