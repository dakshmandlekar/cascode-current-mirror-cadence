# NMOS Characterization and Transistor Sizing

The NMOS device was characterized in Cadence Virtuoso using an initial width of 1 µm. The gm/Id methodology was used to guide sizing for the current-mirror design.

The schematic shows approximately:
- W = 3.63 µm
- L = 100 nm
- Multiplier m = 2

Confirm whether W is the per-finger width or the total instance width according to the PDK's parameter conventions.

## Characterization screenshot
Place the gm/Id graph at `gm_id_curve.png`.

## Sizing calculation
Add the actual selected gm/Id operating point, drain-current density, and width calculation when these values are available from the original characterization. Avoid inferring missing values from the plotted curve alone.