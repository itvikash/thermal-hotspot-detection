# AI-Based Thermal Hotspot Detection System for Solar Photovoltaic Panels

A low-cost, Raspberry Pi-based prototype that combines thermal imaging (MLX90640) with a
visual camera and a lightweight YOLOv8-nano detection model to automatically detect and
localize hotspots (faults) on solar PV panels — catching problems early without expensive
industrial thermography equipment.

## Problem

Solar panels develop hidden faults (cracked cells, failing bypass diodes, loose connections,
shading) that raise the temperature of the affected area before the fault shows up as a
measurable drop in power output. Manual thermal inspection with professional cameras is
expensive and infrequent, so faults often go undetected for weeks. This project builds a
cheap, self-contained unit that automates that detection.

## Project Status

🚧 In progress — currently in the **PVsyst simulation phase** (system design + fault/loss
modeling) before moving to hardware assembly.

## Roadmap

- [x] Project synopsis & PBL report drafted
- [x] Related-work / literature comparison completed
- [ ] PVsyst system design (healthy baseline simulation)
- [ ] PVsyst fault simulation (shading/mismatch loss modeling)
- [ ] Hardware assembly & sensor testing
- [ ] Software pipeline: data acquisition & interpolation
- [ ] Software pipeline: thermal–visual registration
- [ ] Software pipeline: hotspot localization
- [ ] YOLOv8-nano training & on-device deployment
- [ ] Electrical correlation (INA219 logging)
- [ ] End-to-end integration & testing

## System Pipeline

1. **Data Acquisition & Interpolation** (Python) — read raw MLX90640 thermal frames (32x24)
   over I2C, upsample via interpolation, capture matched Pi Camera visual frame.
2. **Preprocessing & Thermal-Visual Registration** — geometrically align thermal and visual
   frames; normalize temperature values.
3. **Computer Vision Hotspot Localization** — flag regions with abnormal temperature relative
   to surrounding panel area.
4. **YOLOv8-nano Detection** — lightweight object detection model classifies and localizes
   confirmed hotspot regions; runs on-device on the Pi 4 CPU.

Electrical readings from an INA219 (voltage/current) and a DS18B20 (reference temperature)
are logged alongside imaging data to confirm a detected hotspot corresponds to real power loss.

## Hardware (Bill of Materials)

| Component | Specification |
|---|---|
| Thermal Sensor | MLX90640 (32x24 IR array) |
| Processing Unit | Raspberry Pi 4 (4GB/8GB RAM) |
| Visual Camera | Raspberry Pi Camera Module 3 (12MP) |
| Display | 3.5"/5" HDMI Touchscreen |
| Storage | 32GB microSD, Class 10 |
| Power | USB-C Power Bank |
| Cabling | Short HDMI-to-micro-HDMI |
| Current/Voltage Sensor | INA219 |
| Temperature Sensor | DS18B20 |

See [`hardware/BOM.md`](hardware/BOM.md) for wiring notes.

## Repository Structure

```
├── docs/                          # Synopsis, PBL report, related-work comparison
├── pvsyst/                        # PVsyst project files, loss reports, notes
├── hardware/                      # BOM, wiring diagrams/notes
├── software/
│   ├── 01_data_acquisition/       # MLX90640 + Pi Camera capture & interpolation
│   ├── 02_preprocessing_registration/  # Thermal-visual alignment
│   ├── 03_hotspot_localization/   # Anomaly region scanning
│   └── 04_yolo_detection/         # YOLOv8-nano training/inference
└── datasets/                      # Labeled thermal hotspot training data (not committed if large)
```

## Author

GitHub: [@itvikash](https://github.com/itvikash)

## License

Add a license of your choice (MIT is common for academic/open projects) before publishing.
