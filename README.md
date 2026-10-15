
# Cascode Current Mirror Design, Layout & Post-Layout Verification

**Analog VLSI Design | Cadence Virtuoso | CMOS Analog IC Design**

A 100 µA target-current cascode current mirror designed and verified using the gm/Id transistor-sizing methodology in Cadence Virtuoso. This project covers NMOS characterization, transistor sizing, schematic design, physical layout, matching techniques, and pre-layout versus post-layout simulation.

## Project Overview

Current mirrors are fundamental building blocks in analog integrated circuits, commonly used for biasing, active loads, and current references.

This project focuses on designing an NMOS cascode current mirror with a target output current of 100 µA. The design process starts with transistor characterization and gm/Id-based sizing, followed by schematic implementation, layout design, and post-layout verification.

The objective is to investigate how well the physical implementation preserves the current-mirroring performance observed during pre-layout simulation.

## Design Specifications

| Parameter | Value |
|---|---|
| Circuit | NMOS Cascode Current Mirror |
| Target current | 100 µA |
| Initial characterization width | 1 µm |
| Calculated transistor width | Approximately 3.625 µm |
| Design tool | Cadence Virtuoso |
| Sizing methodology | gm/Id |
| Layout matching strategy | Common-centroid ABBA arrangement |
| Finger configuration | 2 fingers per transistor |
| Multiplier configuration | 2 multipliers per transistor |

*Note: The transistor width and device configuration are based on the design implementation. Confirm whether the reported width represents per-finger width, total effective width, or schematic instance width before interpreting the final geometry.*

## Design Flow

The project follows the analog IC design flow from device characterization to physical verification.

1. **NMOS Characterization**  
   Characterized an NMOS transistor using an initial width of 1 µm and studied the relationship between drain current, transconductance, and transistor sizing.

2. **gm/Id-Based Transistor Sizing**  
   Used the gm/Id methodology to guide transistor sizing for the desired current level. The resulting transistor width was approximately 3.625 µm.

3. **Schematic Design**  
   Implemented the cascode current mirror in Cadence Virtuoso and performed pre-layout simulation to evaluate its current-mirroring behavior.

4. **Physical Layout**  
   Implemented the transistor layout using a common-centroid ABBA arrangement to improve matching between corresponding devices. A multi-finger and multiplier-based implementation was used.

5. **Post-Layout Verification**  
   Evaluated the extracted layout through post-layout simulation and compared its output current against the pre-layout result.

## 1. NMOS Characterization

NMOS characterization provides insight into transistor behavior before designing the complete circuit.

The gm/Id methodology uses the ratio of transconductance to drain current:

\[
\frac{g_m}{I_D}
\]

where:

- \(g_m\) is the small-signal transconductance.
- \(I_D\) is the DC drain current.

The gm/Id ratio is useful for choosing an operating region and balancing current consumption, transconductance, and transistor sizing.

**Characterization setup:** Initial transistor width = 1 µm.

![NMOS characterization](characterization/gm_id_curve.png)

*Replace this image with the actual gm/Id characterization plot.*

## 2. Transistor Sizing

The transistor sizing process was guided by the characterized device behavior and the desired operating current.

The approximate transistor width obtained during the design process was:

\[
W \approx 3.625\ \mu\text{m}
\]

The final implementation also used two fingers and a multiplier of two per transistor instance.

The effective transistor width must be interpreted according to the PDK and the way the instance parameters are defined in Cadence Virtuoso. The sizing calculation and the physical finger geometry should be documented separately where applicable.

## 3. Cascode Current Mirror Schematic

The cascode current mirror uses additional transistors to improve output resistance and reduce the influence of output-voltage variations on the mirrored current, compared with a simple current mirror under suitable operating conditions.

The circuit was implemented in Cadence Virtuoso and simulated before layout.

![Cascode current mirror schematic](schematic/cascode_schematic.png)

*Insert the actual Cadence Virtuoso schematic screenshot.*

### Pre-Layout Simulation

The pre-layout simulation was used to evaluate the output current before including the parasitic effects introduced by physical implementation and interconnect extraction.

![Pre-layout simulation](schematic/pre_layout_simulation.png)

*Insert the actual pre-layout simulation plot.*

## 4. Layout Design and Matching

The physical layout was implemented in Cadence Virtuoso with attention to transistor placement and matching.

### Layout techniques

- **Common-centroid ABBA arrangement:** Used as a placement strategy to help reduce systematic mismatch caused by spatial process gradients when the corresponding devices are implemented as appropriately matched unit devices.
- **Multi-finger implementation:** Used two fingers per transistor instance.
- **Multiplier configuration:** Used a multiplier of two per transistor instance.
- **Device matching:** Considered device placement and layout symmetry to support consistent current-mirroring behavior.

The effectiveness of these techniques depends on the actual unit-device arrangement, routing symmetry, dummy devices where needed, and the surrounding layout environment.

![Current mirror layout](layout/layout_view.png)

*Insert the actual layout screenshot from Cadence Virtuoso.*

![Matching arrangement](layout/matching_strategy.png)

*Insert an annotated screenshot showing the ABBA arrangement, if available.*

## 5. Post-Layout Verification

Post-layout simulation was performed to evaluate the circuit after physical layout and parasitic extraction.

### Simulation Results

| Parameter | Current |
|---|---:|
| Target current | 100 µA |
| Pre-layout current | 97.99 µA |
| Post-layout current | 97.82 µA |
| Absolute pre/post difference | 0.17 µA |
| Pre/post relative change | Approximately 0.17% |

### Relative Change Calculation

\[
\Delta I = |97.99-97.82|
\]

\[
\Delta I = 0.17\ \mu\text{A}
\]

Using the pre-layout current as the reference:

\[
\%\text{ change} =
\frac{|I_{\text{post}}-I_{\text{pre}}|}
{I_{\text{pre}}}\times100
\]

\[
=\frac{0.17}{97.99}\times100
\approx 0.17\%
\]

The difference between the pre-layout and post-layout currents is approximately 0.17%, indicating close agreement between the two simulated results under the tested conditions.

The post-layout current is approximately 2.18% below the 100 µA target. This target-current error is distinct from the pre-layout-to-post-layout change.

![Post-layout simulation](verification/post_layout_simulation.png)

*Insert the actual post-layout simulation plot.*

![Pre-layout versus post-layout](verification/pre_vs_post_layout.png)

*Insert a comparison plot or a combined screenshot of both simulation results.*

## 6. Key Learnings

Through this project, I explored:

- MOSFET characterization and interpretation of gm/Id curves.
- gm/Id-based transistor sizing for analog circuit design.
- Cascode current mirror operation and current-mirroring principles.
- Multi-finger and multiplier-based transistor implementation.
- Common-centroid placement and the ABBA matching strategy.
- Schematic-to-layout implementation in Cadence Virtuoso.
- Pre-layout versus post-layout simulation and the influence of physical implementation.

## Tools and Technologies

- Cadence Virtuoso
- CMOS analog circuit design
- MOSFET characterization
- gm/Id methodology
- Analog layout and matching
- Parasitic extraction and post-layout simulation

## Future Improvements

Potential next steps include:

- Evaluating output resistance and current-mirror accuracy across the output-voltage range.
- Investigating the minimum output voltage required to keep the cascode devices in saturation.
- Quantifying layout parasitics and their effect on current accuracy.
- Performing process, voltage, and temperature (PVT) corner simulations.
- Evaluating mismatch using Monte Carlo simulations.
- Investigating power consumption, operating range, and robustness.

## Conclusion

This project provided practical exposure to the analog IC design flow, from transistor characterization and gm/Id-based sizing to schematic implementation, physical layout, and post-layout verification.

The close agreement between the pre-layout and post-layout simulated currents demonstrates that the implemented layout preserves the observed current-mirroring performance under the simulated conditions.

---

**Project focus:** Analog VLSI | CMOS Design | Current Mirrors | Cadence Virtuoso | Analog Layout & Verification

