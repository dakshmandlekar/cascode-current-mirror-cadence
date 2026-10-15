# Cascode Current Mirror Design, Layout & Post-Layout Verification

**Analog VLSI · Cadence Virtuoso · CMOS Analog IC Design**

Design and verification of an NMOS cascode current mirror targeting **100 µA**, using MOSFET characterization and the **gm/Id sizing methodology**. The project documents transistor sizing, schematic design, matching-oriented layout, extracted-view simulation, and pre-layout/post-layout comparison.

> **Tool:** Cadence Virtuoso  
> **Target current:** 100 µA  
> **Nominal supply shown in testbench:** 1.2 V  
> **Device parameters shown in schematic:** W = 3.63 µm, L = 100 nm, m = 2

## Repository structure

```text
cascode-current-mirror-cadence/
├── README.md
├── LICENSE
├── docs/
│   ├── design_specifications.md
│   ├── design_notes.md
│   └── design-flow.md
├── characterization/
│   ├── gm_id_curve.png
│   └── transistor_sizing.md
├── schematic/
│   ├── cascode_schematic.png
│   └── pre_layout_simulation.png
├── layout/
│   ├── layout_view.png
│   └── matching_strategy.png
├── verification/
│   ├── post_layout_simulation.png
│   └── pre_vs_post_layout.png
└── results/
    └── simulation_results.md
```

**Image upload status:** The folders and documentation are present, but the seven PNG image files still need to be committed to the matching paths above. The README image links will render after those files are uploaded.

## Project overview

A current mirror is a fundamental analog building block used for bias currents and active loads. A cascode structure can increase output resistance and reduce output-current sensitivity to output voltage, provided the devices retain sufficient operating-region headroom.

### Design flow

1. **NMOS characterization** — studied device behavior and gm/Id using an initial transistor width of 1 µm.
2. **Transistor sizing** — used the gm/Id methodology to guide sizing toward a 100 µA target.
3. **Schematic design** — implemented the cascode current mirror and ran a pre-layout DC sweep.
4. **Physical layout** — used a matching-oriented ABBA/common-centroid arrangement and multi-finger/multiplier implementation.
5. **Extracted-view verification** — compared pre-layout and post-layout output current at the same marked output voltage.

## 1. NMOS characterization and gm/Id

The ratio \(g_m/I_D\) describes transconductance efficiency, where \(g_m\) is small-signal transconductance and \(I_D\) is drain current. It helps guide the trade-off between current, transconductance, operating region, and transistor sizing.

![NMOS gm/Id characterization](characterization/gm_id_curve.png)

See [transistor sizing notes](characterization/transistor_sizing.md) and [design specifications](docs/design_specifications.md).

## 2. Cascode current mirror schematic

![Cascode current mirror schematic](schematic/cascode_schematic.png)

The schematic shows approximately W = 3.63 µm, L = 100 nm, and multiplier m = 2. Confirm whether the width is per finger or total effective width and how the PDK applies the multiplier before interpreting the final geometry.

## 3. Pre-layout simulation

![Pre-layout DC simulation](schematic/pre_layout_simulation.png)

At the marked operating point **Vout = 0.6 V**, the pre-layout output current is approximately **97.99958 µA**.

## 4. Layout and matching strategy

![Current mirror layout](layout/layout_view.png)

![Matching arrangement](layout/matching_strategy.png)

The layout uses a matching-oriented **ABBA/common-centroid arrangement**. Such placement can help reduce systematic mismatch from spatial process gradients when devices are appropriately partitioned into matched unit devices. Matching also depends on routing symmetry, device orientation, surrounding structures, dummy devices where appropriate, and parasitic effects.

## 5. Extracted view and post-layout verification

![Post-layout simulation](verification/post_layout_simulation.png)

![Pre-layout versus post-layout comparison](verification/pre_vs_post_layout.png)

Post-layout simulation includes the parasitic effects represented by the extraction flow. A close pre/post result indicates good agreement at the tested operating point; it does not by itself prove performance across all process corners, supply conditions, output voltages, or mismatch cases.

## 6. Simulation results

At **Vout = 0.6 V**:

| Metric | Result |
|---|---:|
| Target current | 100 µA |
| Pre-layout current | 97.99958 µA |
| Post-layout current | 97.8203 µA |
| Absolute pre/post difference | 0.17928 µA |
| Relative change referenced to pre-layout | ≈ 0.183% |
| Post-layout deviation from target | ≈ −2.18% |

The absolute difference is:

\[
\Delta I = |97.99958 - 97.8203| = 0.17928\ \mu\text{A}
\]

The relative pre/post change is:

\[
\frac{0.17928}{97.99958}\times100 \approx 0.183\%
\]

The post-layout current is approximately **2.18% below the target**. This is distinct from the 0.183% change between pre-layout and post-layout results. More details are available in [simulation results](results/simulation_results.md).

## Key learnings

- MOSFET DC characterization and gm/Id interpretation.
- gm/Id-guided transistor sizing.
- Cascode current-mirror operation and output-voltage dependence.
- Multi-finger and multiplier-based transistor implementation.
- Matching-oriented layout placement and routing.
- Extracted-view and post-layout simulation.
- Quantitative pre-layout/post-layout comparison.

## Future improvements

- Evaluate current accuracy across the full output-voltage range and determine the compliance/headroom limit.
- Document DRC and LVS reports, if completed.
- Investigate extracted parasitics and output resistance.
- Run PVT corner and Monte Carlo mismatch simulations.
- Measure power consumption and robustness.

## Tools and technologies

Cadence Virtuoso · Spectre simulation · CMOS analog design · MOSFET characterization · gm/Id methodology · Analog layout · Parasitic extraction · Post-layout verification

## Reproducibility and PDK note

This repository documents the design flow and selected results. It does not currently contain a portable, independently runnable Cadence project or PDK. Do not upload proprietary PDK files, foundry models, license files, or restricted institutional design data.

See [design flow](docs/design-flow.md), [design notes](docs/design_notes.md), and [design specifications](docs/design_specifications.md).

---
**Project focus:** Analog VLSI · CMOS Design · Current Mirrors · Cadence Virtuoso
