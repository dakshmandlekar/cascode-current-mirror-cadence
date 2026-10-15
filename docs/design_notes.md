# Design Notes

## gm/Id sizing
The ratio gm/Id is a transconductance-efficiency metric. It is used with characterized device curves to guide operating-point selection and transistor sizing. Record the chosen gm/Id value and corresponding current density/width calculation here if those exact values are available from the original sizing work.

## Cascode behavior
A cascode device can increase output resistance and reduce the dependence of mirrored current on output voltage, provided the transistors remain in their intended operating regions. This benefit comes with increased voltage-headroom requirements.

## Layout matching
The layout uses a matching-oriented ABBA/common-centroid arrangement. Its effectiveness depends on the actual unit-device partitioning, symmetric routing, device orientation, surrounding environment, and parasitic effects. Confirm A/B device identities in the layout before making more specific claims.

## Multi-finger and multiplier settings
The schematic shows W = 3.63 µm, L = 100 nm, and m = 2. Confirm the PDK's interpretation of width, finger count, and multiplier.

## Verification notes
Document DRC, LVS, extraction settings, process corner, temperature, supply, and simulator configuration only when the corresponding results are available. Do not claim checks passed unless you have the run reports.

## Image locations
See the folders `characterization/`, `schematic/`, `layout/`, and `verification/` for the planned screenshots.