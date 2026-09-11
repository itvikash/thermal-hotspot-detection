# PVsyst Simulation

## Plan
1. Design the base system: location, panel model, small array size, inverter/string config.
2. Run the healthy-system baseline simulation → record PR (performance ratio) and yield.
3. Model a fault scenario using a shading object or increased module-quality/mismatch loss
   on one string to represent a degraded/hot panel.
4. Run the faulty-system simulation and compare loss reports against the baseline.
5. The yield/PR difference between the two runs quantifies the energy cost of an
   undetected hotspot — used to justify the hardware detection system in the report.

## Files (add once exported from PVsyst)
- `baseline_report.pdf`
- `fault_scenario_report.pdf`
- `comparison_notes.md`
