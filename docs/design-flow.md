# Design Flow

## 1. NMOS characterization
The NMOS device was characterized in Cadence Virtuoso with an initial width of 1 µm. The gm/Id relationship was used to understand transconductance efficiency and guide sizing.

## 2. Device sizing
The current-mirror schematic shows approximately W = 3.63 µm, L = 100 nm, and multiplier m = 2. Confirm how width, finger count, and multiplier are interpreted by the selected PDK before treating these as total effective dimensions.

## 3. Schematic and pre-layout simulation
The cascode current mirror was simulated with a DC sweep of Vout. At the marker Vout = 0.6 V, the pre-layout output current was approximately 97.99958 µA.

## 4. Physical layout
The layout was implemented with a matching-oriented ABBA/common-centroid arrangement and multi-finger/multiplier configuration. Matching depends on unit-device partitioning, routing symmetry, orientation, surroundings, and parasitics.

## 5. Extracted-view and post-layout simulation
The extracted view was simulated after layout. At Vout = 0.6 V, the post-layout output current was approximately 97.8203 µA.

## Verification checklist
- [ ] DRC result documented
- [ ] LVS result documented
- [ ] Extraction setup and corner documented
- [ ] Pre-layout and post-layout conditions matched
- [ ] Output-current behavior checked across the intended Vout range
- [ ] PVT and mismatch analysis considered

Only mark checks complete when the corresponding run results are available.