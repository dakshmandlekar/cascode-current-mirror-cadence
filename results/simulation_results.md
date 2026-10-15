# Simulation Results

The values below are read from the supplied Cadence DC-response screenshots at the marked operating point Vout = 0.6 V.

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

The pre-layout and post-layout values are close at this operating point. This comparison does not establish performance across all output voltages, process corners, supply conditions, or device mismatch.

## Planned screenshots
- `../schematic/pre_layout_simulation.png`
- `../verification/post_layout_simulation.png`
- `../verification/pre_vs_post_layout.png`

The screenshots must be added to the repository before these relative paths render.