# Stage 3: Computer Vision Hotspot Localization

Scans the registered thermal map for regions whose temperature deviates significantly
from the surrounding panel area, narrowing down candidate regions before YOLOv8-nano
classification in Stage 4.

## TODO
- Define a threshold/statistical method for flagging abnormal regions (e.g. local
  temperature deviation above N standard deviations from the panel's mean).
