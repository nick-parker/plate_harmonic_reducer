# Plate Harmonic Reducer (PHR) Project

## Core Concept

A plate harmonic reducer is a strain wave gear that uses a **flat plate** flex spline instead of the conventional cup/hat-shaped flex spline. The reducing mechanism is topologically identical to a conventional harmonic drive, but deformation is **axial** (out-of-plane bending of a plate) rather than **radial** (squeezing a cylinder into an ellipse).

### Three Main Components (same as conventional HR)
1. **Wave Generator (WG)** — input, rotates at motor speed. Uses profiled CAM grooves + steel balls (like a thrust bearing with a sinusoidal groove) to push the flex spline axially at contact points.
2. **Flex Spline (FS)** — thin plate with face-gear-style teeth on one side. Elastically deforms axially so teeth engage the circular spline only at the contact points. Transmits output torque.
3. **Circular Spline (CS)** — fixed ring with matching teeth. Has fewer teeth than the FS (by 2 for 2-point contact, by 3 for 3-point contact).

### Reduction Ratio
R = Zf / (Zf - Zc), same formula as conventional harmonic drives.

- **2-point contact (original PHR, Paper 1):** tooth difference = 2, high ratios (e.g. 50:1 with 100/98 teeth)
- **3-point contact (Tri-c PHR, Paper 2):** tooth difference = 3, enables low ratios (e.g. 16:1 with 48/45 teeth). Three engagement zones at 120 deg intervals.

### Key Advantages over Conventional HR
- **Much lower deformation force** — bending a plate is far easier than radially compressing a cylinder (10 N vs 75 N in FEA for 3-point case)
- **Higher torsional stiffness** — scales as D^4 vs (Do^4 - Di^4) for cup
- **Thinner axially** — deformation is radial-limited not axial-limited
- **Easier manufacturing** — planar geometry amenable to stamping/cold forging; tolerance stack-up simpler (shim-adjustable)
- **Enables low ratios (10:1-30:1)** where conventional HRs struggle

### Wave Generator Groove Profile
The WG has a sinusoidal-ish groove machined into it. Balls ride in this groove. The groove depth varies around the circumference — highest points (where balls push FS into engagement) at 0 and 180 deg (2-point) or 0/120/240 deg (3-point), lowest points halfway between. The depth difference must satisfy: d2 - d1 >= h (tooth height).

Profile options:
- Linear ramp (simple, fixed contact ratio)
- Cubic spline (adjustable curvature, can augment contact ratio at engagement zones)

### Tooth Profile (from papers)
- Paper 1 prototype: module 0.5, tooth height ~0.517 mm (dfa=50mm, dfr=48.966mm), FS thickness 0.3mm, FS inner diameter 48.2mm
- Paper 2 prototype (Tri-c): 48/45 teeth, simple **trapezoidal** teeth with **35 deg transfer angle** (pressure angle), tooth height 0.7mm, FS thickness 0.4mm, Al 7075-T6, pitch radius 37.5mm, 5mm steel balls, groove depth difference 0.8mm

### Force Transmission (Paper 2, eq. 7)
Foutput = sin(psi) * [cos(psi) - mu*sin(psi)] * Finput
Peak transmission at psi ~ 35 deg.

## Current Task
Generate an approximately correct tooth profile suitable for SolidWorks equation-driven curves (or other feasible CAD approach). The teeth are face-gear style (axial engagement on a flat plate), trapezoidal profile with 35 deg transfer/pressure angle.
