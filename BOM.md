# Bill of Materials & Wiring Notes

| Component | Specification | Interface |
|---|---|---|
| Thermal Sensor | MLX90640 (32x24 IR array) | I2C |
| Processing Unit | Raspberry Pi 4 (4GB/8GB RAM) | — |
| Visual Camera | Raspberry Pi Camera Module 3 (12MP) | CSI |
| Display | 3.5"/5" HDMI Touchscreen | HDMI + USB (touch) |
| Storage | 32GB microSD, Class 10 | — |
| Power | USB-C Power Bank | — |
| Cabling | Short HDMI-to-micro-HDMI | — |
| Current/Voltage Sensor | INA219 | I2C (distinct address from MLX90640) |
| Temperature Sensor | DS18B20 | 1-Wire (GPIO) |

## Setup Notes

- Enable I2C and Camera interfaces via `sudo raspi-config` before wiring anything.
- MLX90640 and INA219 share the I2C bus — confirm they resolve to different addresses
  (`i2cdetect -y 1`) before writing acquisition code.
- Test each sensor individually with a minimal script before combining them in the pipeline.
