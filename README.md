# Motorcycle Detection Using YOLOv8 in a Pakistan Environment

## Overview

This project aims to detect motorcycles in various environments found in Pakistan using the YOLOv8 object detection model. The main objective is to detect motorcycles effectively in challenging conditions typical in Pakistan, such as crowded streets, different types of motorcycles, and diverse lighting and weather scenarios. Additionally, the detection can be enhanced to identify riders wearing helmets or not.

## Features
- Motorcycle detection in urban and rural environments.
- Identification of helmet use by riders.
- Robust detection under different lighting conditions, such as daylight, dusk, and night-time settings.
- Handles crowded environments like marketplaces and traffic-heavy areas.

## Dataset
For this project, data will be collected from various cities in Pakistan to cover a diverse range of settings. The dataset will include:
- **City Traffic**: Motorcycles in dense traffic.
- **Rural Roads**: Motorcycles in less congested environments.
- **Weather Variations**: Images in sunny, rainy, and foggy conditions.

### Data Labeling
To label the dataset, RoboFlow's Autolabeler can be used with the following prompt:
"Label all instances of a person riding a motorcycle, including separate bounding boxes for the person, motorcycle, and helmet (if present). Ensure the labels clearly capture the interaction between the rider and the motorcycle, accounting for occlusions, and accurately indicate if the rider is wearing a helmet or not."

## Requirements
To run the YOLOv8 detection system, you will need the following:

- Python 3.8+
- **PyTorch** for deep learning support
- **Ultralytics YOLOv8** implementation
- **OpenCV** for image and video processing
- **Roboflow** for data management and annotation

You can install the required packages using:
```sh
pip install ultralytics opencv-python roboflow
```

## Training the YOLOv8 Model

1. **Clone the YOLOv8 Repository**:
   ```sh
   git clone https://github.com/ultralytics/ultralytics.git
   cd ultralytics
   ```

2. **Prepare the Dataset**:
   - Use RoboFlow to label the motorcycle images collected from Pakistani streets.
   - Download the annotated dataset and ensure it's in YOLO format.

3. **Train the Model**:
   ```sh
   yolo train model=yolov8n.pt data=path/to/your/dataset.yaml epochs=100 imgsz=640
   ```
   - Replace `path/to/your/dataset.yaml` with the actual path to your dataset configuration file.
   - Adjust `epochs` and `imgsz` as necessary for your requirements.

## Testing and Evaluation

Once the model is trained, you can test it on real video footage to assess its performance:

```sh
yolo detect model=path/to/your/best.pt source=path/to/test/video.mp4
```
- Replace `path/to/your/best.pt` with the path to the trained model weights.
- The `source` can be a video file or a webcam for live detection.

## Real-Time Detection
For real-time detection, use a connected camera to feed video directly to the model:

```sh
yolo detect model=path/to/your/best.pt source=0
```
- `source=0` specifies the default webcam.
- The detection system can be deployed on local traffic cameras to monitor motorcycle riders and detect violations like riding without a helmet.

## Deployment
The trained YOLOv8 model can be deployed on various platforms for real-time monitoring:
- **Edge Devices**: Use NVIDIA Jetson devices to deploy the model in the field.
- **Cloud Platforms**: Deploy using cloud services such as AWS, Azure, or Google Cloud for centralized monitoring.
- **Web Application**: Use Flask or FastAPI to create a web interface that streams video feeds and shows real-time detection results.

## Future Work
- Improve the model’s accuracy by incorporating more diverse motorcycle data from different parts of Pakistan.
- Expand the scope to detect other violations, such as overloading or dangerous driving behaviors.
- Integrate the detection system with law enforcement to automate fine issuance for helmet law violations.

## Acknowledgments
- **Ultralytics** for providing the YOLOv8 implementation.
- **RoboFlow** for data annotation and management tools.
- **OpenCV** for computer vision utilities.

## License
This project is licensed under the MIT License. Please see the LICENSE file for more details.
