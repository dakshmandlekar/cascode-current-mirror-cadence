# Cascode Current Mirror Design, Layout & Post-Layout Verification

**Analog VLSI · Cadence Virtuoso · CMOS Analog IC Design**

Design and verification of an NMOS cascode current mirror targeting **100 µA**, using MOSFET characterization and the **gm/Id sizing methodology**. The project covers schematic design, transistor sizing, physical layout, matching strategy, extracted-view simulation, and pre-layout/post-layout comparison.

> **Tool:** Cadence Virtuoso  
> **Target current:** 100 µA  
> **Nominal supply shown in the testbench:** 1.2 V  
> **Device sizing shown in the schematic:** W = 3.63 µm, L = 100 nm, m = 2 (verify width/finger interpretation against the PDK instance settings).

## Repository contents

```text
cascode-current-mirror-cadence/
├── README.md
├── docs/
│   ├── design-flow.md
│   └── simulation-results.md
└── images/
    ├── 01-pre-layout-simulation.png
    ├── 02-post-layout-simulation.png
    ├── 03-av-extracted-view.png
    ├── 04-layout-matching.png
    ├── 05-symbol.png
    ├── 06-schematic.png
    └── 07-gm-over-id.png
```

The image paths above are the intended filenames for the screenshots shared with this project. Add the corresponding files to the `images/` directory so they render below.

## Project overview

A current mirror is a fundamental analog building block used to generate bias currents and active loads. A cascode structure increases output resistance and can improve current stability against output-voltage changes, provided the transistors remain in their intended operating regions.

The design flow followed here:

1. **NMOS characterization** — examined device characteristics and the gm/Id relationship using an initial width of 1 µm.
2. **Transistor sizing** — used gm/Id as a design aid to select a device width for the target current.
3. **Schematic design** — implemented the cascode current mirror and ran a DC sweep before layout.
4. **Layout implementation** — arranged devices using a matching-oriented ABBA/common-centroid strategy and a multi-finger/multiplier configuration.
5. **Extracted-view verification** — simulated the extracted layout and compared its output current with the pre-layout result.

## 1. NMOS characterization and gm/Id

The ratio

\[
\frac{g_m}{I_D}
\]

is a measure of transconductance efficiency, where \(g_m\) is small-signal transconductance and \(I_D\) is drain current. It helps guide the trade-off among current, transconductance, operating region, and transistor dimensions.

![gm/Id characterization plot](images/07-gm-over-id.png)

*Figure 1 — NMOS characterization plots from Cadence Virtuoso. Refer to the plotted axes and operating point when documenting the final sizing choice.*

The characterization setup used an initial transistor width of **1 µm**. The design schematic shows a width of approximately **3.63 µm**, with **L = 100 nm** and **m = 2**. In Cadence, confirm whether the displayed width is per finger or total instance width and how the PDK applies the multiplier before comparing it with the physical layout.

## 2. Schematic and testbench

![Cascode current mirror schematic](images/06-schematic.png)

*Figure 2 — Cascode current mirror schematic in Cadence Virtuoso.*

![Current mirror symbol and testbench](images/05-symbol.png)

*Figure 3 — Symbol-level testbench used for the DC output-current sweep.*

The testbench sweeps the output voltage and observes the output current. The current should be evaluated over the intended operating range, rather than at only one output-voltage point, because the cascode devices need sufficient voltage headroom to remain in saturation.

## 3. Pre-layout simulation

![Pre-layout DC simulation](images/01-pre-layout-simulation.png)

*Figure 4 — Pre-layout DC response. The marker reads approximately **97.99958 µA at Vout = 0.6 V**.*

The pre-layout current is close to the 100 µA target at the marked operating point. The full sweep also helps show how the output current varies with output voltage.

## 4. Layout and matching strategy

![Cascode current mirror layout with matching arrangement](images/04-layout-matching.png)

*Figure 5 — Physical layout in Cadence Virtuoso, showing the device placement and routing.*

The layout uses a matching-oriented **ABBA/common-centroid arrangement** and a multi-finger/multiplier implementation. Such placement can help reduce systematic mismatch from spatial process gradients when the devices are partitioned into appropriate unit devices. Matching also depends on symmetric routing, orientation, surroundings, dummy devices where appropriate, and parasitic effects.

Review the actual layout to verify which devices form the A and B groups and whether the intended centroid and routing symmetry are achieved.

## 5. Extracted view and post-layout simulation

![Extracted layout view](images/03-av-extracted-view.png)

*Figure 6 — Extracted view used for post-layout verification.*

![Post-layout DC simulation](images/02-post-layout-simulation.png)

*Figure 7 — Post-layout DC response. The marker reads approximately **97.8203 µA at Vout = 0.6 V**.*

Post-layout simulation includes the parasitic effects represented by the extraction flow. A close pre-layout/post-layout result is useful evidence that the physical implementation preserves the circuit's behavior under the simulated conditions; it does not by itself establish performance across all corners or mismatch conditions.

## 6. Simulation results

At the marked operating point **Vout = 0.6 V**:

| Metric | Result |
|---|---:|
| Target current | 100 µA |
| Pre-layout current (marker) | 97.99958 µA |
| Post-layout current (marker) | 97.8203 µA |
| Absolute pre/post difference | 0.17928 µA |
| Relative pre/post change, referenced to pre-layout | ≈ 0.183% |
| Post-layout deviation from target | ≈ −2.18% |

The difference is calculated from the more precise values visible in the supplied screenshots:

\[
\Delta I = |97.99958 - 97.8203| = 0.17928\ \mu\text{A}
\]

\[
\text{Relative change} =
\frac{0.17928}{97.99958}\times100
\approx 0.183\%
\]

The pre-layout and post-layout currents differ by approximately **0.18%** at the marked point. The post-layout current is approximately **2.18% below the 100 µA target**, which is a separate metric from the pre/post difference.

## Key learnings

- MOSFET DC characterization and gm/Id interpretation.
- gm/Id-guided transistor sizing.
- Cascode current-mirror operation and output-voltage dependence.
- Multi-finger and multiplier-based transistor implementation.
- Matching-oriented layout placement and routing.
- Extracted-view and post-layout simulation.
- Quantitative comparison of pre-layout and post-layout results.

## Possible next steps

- Check current accuracy over the full output-voltage range and identify the compliance/headroom limit.
- Run DRC and LVS and document the results, if completed.
- Compare extracted parasitics and their impact on output current.
- Evaluate PVT corners and Monte Carlo mismatch.
- Measure output resistance and power consumption.

## Tools and technologies

Cadence Virtuoso · Spectre simulation · CMOS analog design · MOSFET characterization · gm/Id methodology · Analog layout · Parasitic extraction · Post-layout verification

## Notes on reproducibility

This repository documents the design process and selected simulation screenshots. It does **not** currently include a portable, independently runnable Cadence project or PDK. Proprietary PDK files, foundry models, license files, and restricted institutional design data should not be uploaded.

---

**Project:** Cascode Current Mirror Design, Layout & Post-Layout Verification  
**Focus:** Analog VLSI · CMOS Design · Current Mirrors · Cadence Virtuoso
