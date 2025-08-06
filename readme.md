# AutoTrack 🚗🔍

**AutoTrack: A Deep Learning approach on a Novel Dataset for Vehicle Detection and Route Tracking from CCTV Images**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) [![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/) [![YOLOv5](https://img.shields.io/badge/YOLOv5-Model-orange.svg)](https://github.com/ultralytics/yolov5)

## 🔍 Overview

AutoTrack is an intelligent deep learning system designed to **detect vehicles from CCTV footage**, **read license plates**, and **track their routes across multiple camera locations**. Developed as part of a research project at **United International University**, in collaboration with the **University of Portsmouth**, the system aims to assist **law enforcement agencies** in investigating hit-and-run and traffic violation cases faster and more accurately.

---

## 🚘 Features

- 🚗 **Vehicle Detection** using YOLOv5 (custom-trained)
- 🔢 **License Plate Recognition** using OCR (EasyOCR / YOLOv8+OCR)
- 🛰️ **Multi-Camera Tracking** using timestamp and location metadata
- 🗺️ **Route Mapping** using OpenStreetMap
- 🧠 **Custom Dataset** with 4,856+ labeled vehicle images
- 📊 **mAP, Confusion Matrix, and Evaluation Metrics** for model performance

---

## 📁 Dataset

We curated a novel dataset of **4,856 images** collected from:

- Real-world CCTV cameras
- Mobile surveillance footage
- Public datasets

It includes diverse:

- Lighting conditions (day/night)
- Vehicle types and colors
- Realistic traffic scenes in Bangladesh

Annotations are in YOLO format:

`<class_id> <x_center> <y_center> <width> <height>`

---

## 🧠 Model Architecture

We use **YOLOv5s** for object detection, fine-tuned on our dataset.

### Detection Pipeline:

1. **YOLOv5** → Vehicle Detection
2. **EasyOCR / YOLOv8** → License Plate Recognition
3. **Tracking** → Cross-camera route building
4. **OpenStreetMap** → Visualize the route of suspected vehicles

---

## 🛠 Installation

### 🔹 Requirements

- Python 3.8+
- PyTorch
- OpenCV
- EasyOCR
- Ultralytics (for YOLOv5)
- Jupyter or Streamlit (for visualization)

### 🔹 Setup

```bash
git clone https://github.com/itsrifathridoy/Hit-And-Run-Case.git
cd AutoTrack

# Create a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

---

## 🚀 Getting Started

### 🔸 Step 1: Train the YOLOv5 Model

```bash
cd yolov5
python train.py --img 640 --batch 16 --epochs 50 --data data.yaml --weights yolov5s.pt --name autotrack
```

### 🔸 Step 2: Run Detection

```bash
python detect.py --weights runs/train/autotrack/weights/best.pt --source ../test_images
```

### 🔸 Step 3: License Plate Recognition (OCR)

```bash
python plate_reader.py --input results/
```

### 🔸 Step 4: Route Tracking & Mapping

```bash
python track_and_map.py --log metadata.json
```

---

## 📊 Results

| Metric          | Before Augmentation | After Augmentation |
| --------------- | ------------------- | ------------------ |
| Accuracy        | 71.2%               | 84.5%              |
| mAP\@0.5        | 0.66                | 0.81               |
| Inference Speed | 18 FPS              | 19 FPS             |

- **F1-Score**, **Precision**, and **Recall** improved after class balancing.
- Best performance on **bright outdoor images** with clear vehicle view.

---

## 📌 Use Cases

- 👮 **Law Enforcement**: Track hit-and-run suspects
- 🚦 **Traffic Analysis**: Monitor vehicle flow and behavior
- 🛣️ **Toll/Gate Surveillance**: Validate vehicle entry/exit
- 🎓 **Academic Use**: Real-world dataset and code for research

---

## 🔮 Future Work

- Integrate with **real-time CCTV feed**
- Improve OCR in **low-light/night conditions**
- Add **vehicle re-identification** (Re-ID) features
- Deploy to **Raspberry Pi or Jetson Nano** for edge use

---

## 🧑‍💻 Contributors

| Name                        | Student ID | Institution                     |
| --------------------------- | ---------- | ------------------------------- |
| **Jiyasmin Akter Sinthiya** | 011221503  | United International University |
| **Md. Musfiqur Rahman**      | 011221334  | United International University |
| **Rifat Ibne Yousuf**       | 011221235  | United International University |
| **Md. Tashin Parvez**       | 011221437  | United International University |
| **Md. Azizul Haque Noman**  | 011221338  | United International University |

**🔬 Supervisor:**
**Mr. Raiyan Rahman**
*University of Portsmouth, UK*

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).

---

## 🤝 Acknowledgements

- [Ultralytics YOLOv5](https://github.com/ultralytics/yolov5)
- [OpenStreetMap](https://www.openstreetmap.org/)
- [EasyOCR](https://github.com/JaidedAI/EasyOCR)

---

## 📬 Contact US

| Name              | GitHub                                           | LinkedIn                                              | Email                                                           |
| ----------------- | ------------------------------------------------ | ----------------------------------------------------- | --------------------------------------------------------------- |
| **Md. Tashin Parvez** | [@tashinparvez](https://github.com/tashinparvez) | [Tashin Parvez](https://linkedin.com/in/tashinparvez) | [tashinparvez.cse@uiu.ac.bd](mailto:tashinparvez2002@gmail.com) |
| **Rifat Ibne Yousuf** | [@itsrifathridoy](https://github.com/itsrifathridoy)           | [Rifat Hridoy](https://linkedin.com/in/itsrifathridoy)           | [itsmerifathridoy@gmail.com](mailto:itsmerifathridoy@gmail.com)                   |
| **Md. Azizul Haque Noman** | [@author2](https://github.com/author2)           | [Author 2](https://linkedin.com/in/author2)           | [author2@email.com](mailto:author2@email.com)                   |
| **Jiyasmin Akter Sinthiya** | [@jsinthiya](https://github.com/jsinthiya) | [Jiyasmin Sinthiya](https://linkedin.com/in/jsinthiya)  | [jaksinthi@gmail.com](mailto:jaksinthi@gmail.com)                   |
| **Md. Musfiqur Rahman** | [@musfiqurR661](https://github.com/musfiqurR661)           | [Md Musfiqur Rahman](https://www.linkedin.com/in/musfiqur661/)           | [MRahman](musfiqurm661@email.com)                   |
| **Mr. Raiyan Rahman**  | [@faculty](https://github.com/faculty)           | [Faculty](https://linkedin.com/in/faculty)            | [faculty@university.ac.bd](mailto:faculty@university.ac.bd)     |
