# Stage 1: Data Acquisition & Interpolation

Reads raw thermal frames from the MLX90640 (32x24) over I2C, upsamples them via
interpolation to a usable resolution, and captures a matched visual frame from the
Raspberry Pi Camera Module 3.

## Dependencies
```
pip install adafruit-circuitpython-mlx90640 picamera2 numpy scipy
```

## Files
- `capture_thermal.py` — placeholder for the MLX90640 read + interpolation script (TODO)
- `capture_visual.py` — placeholder for the Pi Camera capture script (TODO)
