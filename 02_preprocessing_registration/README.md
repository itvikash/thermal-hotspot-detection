# Stage 2: Preprocessing & Thermal-Visual Registration

Aligns the thermal and visual frames geometrically (the two cameras sit at different
positions/fields of view) and normalizes temperature values for consistent model input.

## TODO
- Determine a fixed transform (homography) between the thermal and visual camera views
  using reference calibration points, since both cameras are rigidly mounted together.
- Apply temperature normalization before passing frames to Stage 3.
