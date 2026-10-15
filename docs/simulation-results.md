# Simulation Results

The following values are read from the supplied Cadence DC-response screenshots at the marker setting Vout = 0.6 V.

| Metric | Result |
|---|---:|
| Target current | 100 µA |
| Pre-layout current | 97.99958 µA |
| Post-layout current | 97.8203 µA |
| Absolute pre/post difference | 0.17928 µA |
| Relative change vs. pre-layout | ≈ 0.183% |
| Post-layout deviation from target | ≈ −2.18% |

## Calculations

Absolute difference:

```
|97.99958 - 97.8203| = 0.17928 µA
```

Relative pre/post change:

```
(0.17928 / 97.99958) × 100 ≈ 0.183%
```

Post-layout deviation from target:

```
((97.8203 - 100) / 100) × 100 ≈ -2.18%
```

The pre-layout and post-layout values are close at this operating point. This comparison alone does not establish accuracy across all output voltages, process corners, supply conditions, or device mismatch.

## Image status

Add the seven screenshots listed in the repository README under `images/`. The documentation assumes the following filenames:

- `01-pre-layout-simulation.png`
- `02-post-layout-simulation.png`
- `03-av-extracted-view.png`
- `04-layout-matching.png`
- `05-symbol.png`
- `06-schematic.png`
- `07-gm-over-id.png`
