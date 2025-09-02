🚧 Forbidden Zone Violation (RetinaNet + OpenCV)

Monitor a pedestrian area and raise an alert whenever a vehicle enters a forbidden zone.
This can be used for security protocols on construction or industrial sites, restricted areas in airports and train stations, illegal parking, etc.

🧠 What it does

- Uses RetinaNet (TorchVision) to detect people and vehicles on each frame.
- Defines the forbidden area as a 6-point polygon ROI that you can adapt to your plaza/street.
The ROI is a polygon defined in normalized coordinates (x,y in 0..1) so it scales to any resolution.
- Runs a tiny tracker (distance-first + IoU fallback) to keep stable vehicle IDs
- Counts exactly once when a vehicle goes outside → inside the ROI (no double counting).
- Overlays:
  - ROI fill (blue when clear, red when any vehicle is inside).
  - Violations counter (top-left).
  - Alert banner (bottom-center) while any vehicle is inside.

🗺️ Why RetinaNet?

- It ships with TorchVision so no extra model downloads or proprietary wrappers.
- Good balance of accuracy/simplicity for a fixed camera and moderate FPS.

📝 Notes & limitations

- Ground contact is approximated by the bottom-center of the vehicle box.
- Performance depends on your hardware and video resolution.
- RetinaNet is robust but not perfect; lighting changes or unusual angles can impact detections.
- Detector: RetinaNet ResNet50 FPN from TorchVision.
- Visualization & tracking logic: OpenCV + a minimal greedy data-association (distance-first, IoU fallback).

- ### Output preview
https://github.com/ValerioCann/Forbidden-Zone-Violation-RetinaNet/blob/main/forbidden_zone_retinanet_output.mp4



🙌 Librairies

- TorchVision
- OpenCV
