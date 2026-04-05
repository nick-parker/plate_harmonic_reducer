# Sheet Metal Plate Harmonic Reducer

A 15:1 plate harmonic reducer where every non-turned part is formed sheet metal, designed to be fabricated with a manual lathe and 3D-printed forming dies.

![Exploded view](Color%20coded%20explode.png)

![Cross section](color%20coded%20cross.png)

![Wave plates](formed%20wave%20plates.png)

**Red** = fixed housing + fixed tooth plate (flex spline, 32 teeth). **Blue** = wave generator (input, rides on the motor). **Green** = output gear (30 teeth).

## What is a plate harmonic reducer?

A [plate harmonic reducer](https://doi.org/10.1109/IROS47612.2022.9981317) flattens the conventional cup-shaped flex spline into a thin plate and deforms it axially instead of radially. Same reduction principle (R = Zf/(Zf - Zc)), dramatically lower deformation forces, and — critically for this project — the flex spline is now a flat disc that can be stamped from sheet metal.

The [tri-contact variant](https://doi.org/10.1109/TMECH.2025.3628311) from the same Seoul National University group showed these can operate at low reduction ratios (10:1–30:1) where conventional harmonic drives struggle, with competitive efficiency and backlash. Our design uses a two-contact (two-lobe) wave generator at 32/30 teeth for a 15:1 ratio.

## Why sheet metal everything?

This is inspired by [Peter Holderith](https://twitter.com/_baldtires), who has been developing quick-turn sheet metal forming with 3D-printed dies as a service. The design constraint is: **the only precision operations are rotationally symmetric turning and sheet metal forming with printed tooling.** No surface milling, no wire EDM, no gear cutting. If you have a manual lathe, a 3D printer, and a press, you can make this reducer.

Both the fixed tooth plate (flex spline) and the output tooth plate are formed sheet metal. This is admittedly silly for the output gear — if you own a 3-axis mill, just machine it. But the point is to explore how far sheet metal forming can go as a fabrication strategy for mechanism components.

## Design choices

**Wave generator: roller bearings, not a profiled groove.** The original PHR papers use steel balls riding in a sinusoidal CAM groove to generate the wave. This gives excellent contact ratio but requires precision machining of the groove. Our wave generator instead uses three 623ZZ bearings per lobe — two ride on top of the flex plate to push ~2.5 teeth into engagement, and one transfers that load down onto a running surface on the housing back bell. The original authors avoided rollers because they only engage a narrow arc of teeth and consume axial space. I think wrapping the mechanism around an outrunner motor (eg RO6000 KV115 in CAD now) makes the axial packaging acceptable — the flex plate reducer demands a larger diameter than the motors that match its torque capacity, leaving an annulus of free space around the motor that accommodates tall rollers without growing the overall stack. The rollers should also have better load capacity and easier manufacturing than a precision wavy bearing race.

**Roller supports are sheet metal (and shouldn't be).** The housing is ~6mm wider than necessary because the roller support arms are doubly supported by sheet metal brackets instead of cantilevered features on a machined rotor body. This is a concession to the "sheet metal everything" constraint. A machined rotor with integral roller posts would be the obvious improvement, and could arguably be a manual lathe part if you're brave enough.

**One fastener.** The entire assembly uses a single screw specification: M2.5x6 Torx pan head. The 8x M2.5 holes on the output flange are left empty — use longer bolts to attach your payload.

**Tooth profile.** Trapezoidal teeth with a 35-degree transfer angle (optimized for force transmission per [You et al.](https://doi.org/10.1109/TMECH.2025.3628311)), 1mm tooth height, 4mm radial tooth width, 0.5mm web connecting each tooth to the plate body. 50% duty cycle at mid-tooth-height for balanced root/tip proportions and easier forming.

## Parameters

| Parameter | Value |
|-----------|-------|
| Reduction ratio | 15:1 |
| Fixed tooth plate (flex spline) | 32 teeth |
| Output tooth plate | 30 teeth |
| Pitch diameter | 42mm |
| Tooth height | 1mm |
| Transfer angle | 35 deg |
| Web thickness | 0.5mm |
| Motor | RO6000 KV115 (or similar outrunner) |
| Bearing | CRBT8050 (Chinese thin cross roller) |

## References

1. S. You, J. Jung, E. Sung, and J. Park, "Plate Harmonic Reducer with a Profiled Groove Wave Generator," *IEEE/RSJ IROS*, 2022. [DOI: 10.1109/IROS47612.2022.9981317](https://doi.org/10.1109/IROS47612.2022.9981317) | [pdf](http://dyros.snu.ac.kr/wp-content/uploads/2022/11/76347-3462.pdf?ckattempt=1)

2. S. You, E. Sung, D. Kim, J. Kim, and J. Park, "Semidirect Drive Based on Tri-Contacted Plate Harmonic Reducer," *IEEE/ASME Trans. Mechatronics*, 2025. [DOI: 10.1109/TMECH.2025.3628311](https://doi.org/10.1109/TMECH.2025.3628311)
