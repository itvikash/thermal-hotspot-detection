# Stage 4: YOLOv8-nano Detection

Trains and deploys a YOLOv8-nano model to classify and draw bounding boxes around
confirmed hotspot regions. Chosen for its small size, allowing inference directly on the
Raspberry Pi 4 CPU without a GPU/accelerator.

## Dependencies
```
pip install ultralytics
```

## TODO
- Source/label a thermal hotspot dataset (bounding boxes around fault regions).
- Train: `yolo train model=yolov8n.pt data=hotspot_dataset.yaml epochs=100`
- Export/deploy trained weights for on-device inference on the Pi.
