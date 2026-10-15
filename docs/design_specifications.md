# Design Specifications

## Project
NMOS cascode current mirror designed in Cadence Virtuoso.

| Parameter | Value |
|---|---|
| Target mirrored current | 100 µA |
| Nominal supply shown in testbench | 1.2 V |
| Device width shown in schematic | 3.63 µm |
| Channel length shown in schematic | 100 nm |
| Multiplier shown in schematic | 2 |
| Initial characterization width | 1 µm |
| Sizing approach | gm/Id methodology |
| Layout approach | Matching-oriented ABBA/common-centroid arrangement |

## Important sizing note
Confirm from the PDK instance properties whether the displayed width is per finger or total effective width and how the multiplier is applied. Do not infer total device width from W, finger count, and multiplier without checking the PDK conventions.

## Operating point
The supplied pre-layout and post-layout DC-response screenshots mark Vout = 0.6 V. This is the operating point used for the current comparison documented in `../results/simulation_results.md`.

## Tools
- Cadence Virtuoso
- Spectre simulation flow (as configured in the design environment)
- PDK-provided NMOS device model

The repository documents screenshots and design notes; it does not distribute foundry PDK or licensed model files.