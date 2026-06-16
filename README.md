<div align="center">

# TruthSight — Deepfake Video Detection

</div>

<div align="center">

![Version](https://img.shields.io/badge/Version-1.0-blue)
![Platform](https://img.shields.io/badge/Platform-Windows%20|%20Linux%20|%20Mac-brightgreen)
![Python](https://img.shields.io/badge/Python-3.8+-yellow)
![Framework](https://img.shields.io/badge/Framework-Flask-red)
![License](https://img.shields.io/badge/License-Open--Source-green)
![AI](https://img.shields.io/badge/AI-Deep%20Learning-purple)

</div>

---

TruthSight is a web app I built to detect deepfake videos using deep learning. Upload a video, and it tells you whether it's real or fake — along with a confidence score.

The core idea is a two-stage pipeline: first enhance the video frames to improve quality, then classify each face as real or fake using ResNet50. Final verdict is based on majority voting across all analyzed frames.

---

## How it works

1. You upload a video (MP4, AVI, MOV, MKV, or WEBM — up to 500MB)
2. OpenCV pulls one frame per second from the video
3. Each frame gets passed through a Retinex-guided UNet model to improve image quality
4. Dlib's HOG-based face detector finds and crops faces from each frame
5. ResNet50 classifies each face crop as Real or Fake
6. Majority voting across all frames gives the final verdict + confidence %

The reason I added the enhancement step before classification is that low-light or compressed videos tend to hide manipulation artifacts. Running frames through the UNet first makes those artifacts more visible, which is why accuracy jumps from ~97% to 99.56% compared to skipping enhancement.

---

## Results

| Metric | Value |
|--------|-------|
| Test Accuracy | 99.56% |
| Precision | 96.84% |
| Recall | 97.65% |
| F1-Score | 97.25% |

**With vs without enhancement:**
| | Accuracy | F1 |
|--|--|--|
| Without enhancement | 97.3% | 0.971 |
| With enhancement | 99.56% | 0.995 |

---

## Models

| Model | Architecture | Input | Trained On |
|-------|-------------|-------|------------|
| Classification | ResNet50 | 224×224 | DFDC (Deepfake Detection Challenge) |
| Enhancement | Retinex UNet | 256×256 | LOL (Low-Light) dataset |
| Face Detector | Dlib HOG | Variable | Built-in |

### Download models

The model files are too large for GitHub. Download and place them in the `models/` folder:

> **📥 [Click here to download models](https://drive.google.com/drive/folders/1PLRYWGBN-fi8FlYnYEtZtqXmVvfbfB9o?usp=sharing)**

| File | Size | Description |
|------|------|-------------|
| `deepfake-detection-model.h5` | ~654 MB | ResNet50-based binary classifier trained on DFDC to detect real vs fake faces |
| `best_unet_model.keras` | ~373 MB | Retinex-guided UNet encoder-decoder that enhances video frames before classification |

---

## Tech stack

| Layer | Tools |
|-------|-------|
| Backend | Python, Flask |
| Frontend | HTML, CSS, JavaScript |
| Classification | ResNet50 (TensorFlow/Keras) |
| Enhancement | UNet (TensorFlow/Keras) |
| Face Detection | Dlib HOG |
| Video Processing | OpenCV |

---

## Project structure

```
truthsight-deepfake-detection/
├── app.py                          # Flask backend
├── README.md
├── .gitignore
│
├── templates/
│   ├── index.html                  # Upload page
│   └── result.html                 # Results page
│
├── static/
│   └── css/
│       └── style.css
│
├── models/                         # Download separately (see above)
│   ├── deepfake-detection-model.h5
│   └── best_unet_model.keras
│
├── codes/                          # Training notebooks
│   ├── deepfake-Copy1.ipynb
│   ├── enhancementModel.ipynb
│   ├── model_resnet50-Copy1.ipynb
│   └── createDataset.ipynb
│
└── uploads/                        # Auto-created at runtime
```

---

## Setup

### 1. Clone

```bash
git clone https://github.com/Axwathy/truthsight-deepfake-detection.git
cd truthsight-deepfake-detection
```

### 2. Install dependencies

```bash
pip install flask opencv-python dlib numpy tensorflow werkzeug
```

> **Windows note:** `dlib` needs Visual C++ Build Tools to compile. Install them from [here](https://visualstudio.microsoft.com/visual-cpp-build-tools/) and select "Desktop development with C++". Alternatively, grab a pre-built `.whl` from [this repo](https://github.com/z-mahmud22/Dlib_Windows_Python3.x) and install it directly.

### 3. Download models

Grab both model files from the link above and drop them in the `models/` folder.

### 4. Run

```bash
python app.py
```

Open `http://localhost:5000` in your browser.

---

## System requirements

| | Minimum | Recommended |
|--|---------|-------------|
| Python | 3.8+ | 3.10+ |
| RAM | 8GB | 16GB+ |
| GPU | Not required | NVIDIA with CUDA |
| Disk | 2GB | 4GB+ |
| OS | Windows / Linux / Mac | Windows 10+ / Ubuntu 20.04+ |

---

## Limitations

- Only works on videos with clearly visible faces — no faces means no result
- Trained on a subset of DFDC, so very sophisticated or new deepfake methods might fool it
- High-resolution videos take longer to process
- No real-time video stream support yet

---

## What's next

Things I want to add eventually:
- Real-time stream detection
- Grad-CAM visualization to show which facial regions triggered the detection
- Audio + video multimodal analysis
- Mobile/cloud deployment

---

## Built with

- [TensorFlow/Keras](https://www.tensorflow.org/)
- [Flask](https://flask.palletsprojects.com/)
- [OpenCV](https://opencv.org/)
- [Dlib](http://dlib.net/)

---

Built by **Axwathy** — [GitHub](https://github.com/Axwathy)

*Last updated: June 2026*
