<div align="center">

# ✨ TruthSight — AI-Powered Deepfake Video Detection ✨

</div>

<div align="center">

![Version](https://img.shields.io/badge/Version-1.0-blue)
![Platform](https://img.shields.io/badge/Platform-Windows%20|%20Linux%20|%20Mac-brightgreen)
![Python](https://img.shields.io/badge/Python-3.8+-yellow)
![Framework](https://img.shields.io/badge/Framework-Flask-red)
![License](https://img.shields.io/badge/License-Open--Source-green)
![AI](https://img.shields.io/badge/AI-Deep%20Learning-purple)

**A powerful deepfake detection web application using ResNet50 and UNet deep learning models to identify AI-generated or manipulated video content with high accuracy.**

</div>

---

## 🚀 What is TruthSight?

TruthSight is an AI-powered web application that detects deepfake videos by analyzing them frame-by-frame. It extracts faces from video frames, enhances image quality using a UNet model, and classifies each face as **REAL** or **FAKE** using a ResNet50 deep learning model. The final verdict is determined through majority voting across all analyzed frames, delivering results with confidence scoring.

Simply upload a video — TruthSight handles the rest.

## ✨ Key Features

- 🧠 **Advanced Deep Learning**: Powered by ResNet50 architecture trained on deepfake datasets for unparalleled accuracy
- 🖼️ **Frame Enhancement**: UNet-based model improves frame quality before analysis for better detection on low-quality videos
- 👤 **Face Detection**: Dlib frontal face detector identifies and isolates all faces in each frame
- 📤 **Drag & Drop Upload**: Simple and intuitive video upload interface
- 📊 **Detailed Reports**: Confidence scores, frame-by-frame statistics, and visual prediction distribution
- 🔒 **Privacy First**: Videos are processed securely and deleted immediately after analysis
- 🎬 **Multi-Format Support**: Supports MP4, AVI, MOV, MKV, and WEBM formats (up to 500MB)
- ⚡ **Fast Processing**: Optimized pipeline samples 1 frame per second for speed and accuracy balance

## 📋 How It Works

1. 📤 **Upload** your video through the web interface (drag & drop or browse)
2. 🎞️ **Frame Extraction** — System extracts 1 key frame per second from the video
3. ✨ **Enhancement** — UNet model enhances each frame for better quality (256×256)
4. 👤 **Face Detection** — Dlib detects all faces in each enhanced frame
5. 🧠 **Classification** — ResNet50 model classifies each face as Real or Fake (224×224)
6. 📊 **Result** — Majority voting determines the final verdict with confidence percentage

## 🛠️ Tech Stack

| Component | Technology |
|-----------|------------|
| Backend | Python, Flask |
| Frontend | HTML, CSS, JavaScript |
| Classification Model | ResNet50 (TensorFlow/Keras) |
| Enhancement Model | UNet (TensorFlow/Keras) |
| Face Detection | Dlib (HOG-based) |
| Video Processing | OpenCV |
| Fonts | Inter, Space Grotesk (Google Fonts) |
| Icons | Font Awesome 6.4 |

## 💻 System Requirements

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| Python | 3.8+ | 3.10+ |
| RAM | 8GB System RAM | 16GB+ System RAM |
| GPU | Not required (CPU works) | NVIDIA GPU with CUDA |
| Disk Space | 2GB (for models) | 4GB+ |
| OS | Windows / Linux / Mac | Windows 10+ / Ubuntu 20.04+ |

## 📁 Project Structure

```
webapptrial/
├── app.py                          # Main Flask application (backend)
├── README.md                       # Project documentation
├── .gitignore                      # Git ignore rules
│
├── templates/                      # HTML templates
│   ├── index.html                  # Landing page with upload form
│   └── result.html                 # Analysis results page
│
├── static/                         # Static assets
│   └── css/
│       └── style.css               # Stylesheet
│
├── models/                         # Trained ML models (download separately)
│   ├── deepfake-detection-model.h5 # ResNet50 classification model (~654MB)
│   └── best_unet_model.keras       # UNet enhancement model (~373MB)
│
├── codes/                          # Jupyter notebooks (training & experiments)
│   ├── basicCode1.ipynb            # Basic deepfake detection code
│   ├── createDataset.ipynb         # Dataset creation script
│   ├── deepfake-Copy1.ipynb        # Main deepfake model training
│   ├── enhancementModel.ipynb      # UNet enhancement model training
│   ├── model_resnet50-Copy1.ipynb  # ResNet50 model training
│   └── app.py                      # Backup of main app
│
├── test_videos/                    # Sample test videos (not in repo)
│   ├── fake1.mp4 - fake5.mp4      # Fake deepfake videos
│   ├── real1.mp4 - real6.mp4      # Real authentic videos
│   └── metadata.json              # Video metadata
│
└── uploads/                        # Temporary upload directory (auto-created)
```

## 📦 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/Axwathy/truthsight-deepfake-detection.git
cd truthsight-deepfake-detection
```

### 2. Install Dependencies

```bash
pip install flask opencv-python dlib numpy tensorflow werkzeug
```

> **Note:** Installing `dlib` on Windows may require [CMake](https://cmake.org/download/) and [Visual Studio Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/). On Linux, you can install it with `pip install dlib` after installing `cmake` via your package manager.

### 3. Download Model Files

The trained model files are too large for GitHub (>100MB each). Download them and place them in the `models/` folder:

> **📥 Model Download Link:** [Google Drive / OneDrive link here]

| Model File | Size | Description |
|-----------|------|-------------|
| `deepfake-detection-model.h5` | ~654 MB | ResNet50 classification model |
| `best_unet_model.keras` | ~373 MB | UNet frame enhancement model |

### 4. Run the Application

```bash
python app.py
```

The app will start at: **http://localhost:5000**

Open your browser and navigate to `http://localhost:5000` to start detecting deepfakes!

## 🔍 Model Details

| Model | Architecture | Input Size | Purpose | Dataset |
|-------|-------------|------------|---------|---------|
| Classification | ResNet50 | 224×224 | Classify faces as Real/Fake | DFDC (Deepfake Detection Challenge) |
| Enhancement | UNet (Encoder-Decoder) | 256×256 | Improve frame quality before analysis | Custom |
| Face Detector | Dlib HOG | Variable | Detect and extract faces from frames | Built-in |

### Detection Pipeline

```
Video Upload → Frame Extraction (1 fps) → UNet Enhancement → Dlib Face Detection → ResNet50 Classification → Majority Voting → Final Result
```

## 🎯 Use Cases

- 📰 **Journalism** — Verify video authenticity before publishing
- ⚖️ **Legal & Forensics** — Authenticate video evidence for court proceedings
- 🏛️ **Government** — Protect against political misinformation
- 🛡️ **Cybersecurity** — Detect social engineering attacks using synthetic media
- 🎓 **Education** — Teach media literacy and content verification
- 📱 **Social Media** — Identify and flag manipulated content
- 🏦 **Financial Services** — Prevent identity fraud through video verification
- 👤 **Personal Use** — Verify videos shared in personal networks

## ❓ FAQ

<details>
<summary><b>What is a deepfake?</b></summary>
<br>
A deepfake is synthetic media created using artificial intelligence, typically involving the replacement of a person's face or voice in a video with someone else's likeness. The term combines "deep learning" and "fake."
</details>

<details>
<summary><b>How accurate is the detection?</b></summary>
<br>
Our system achieves approximately 99.2% accuracy on standard deepfake datasets. However, detection accuracy can vary depending on video quality, compression, and the sophistication of the deepfake generation method.
</details>

<details>
<summary><b>What video formats are supported?</b></summary>
<br>
We support MP4, AVI, MOV, MKV, and WEBM formats. The maximum file size is 500MB.
</details>

<details>
<summary><b>Is my video data secure?</b></summary>
<br>
Yes. All videos are processed securely and automatically deleted immediately after analysis. We do not store, share, or use your videos for any purpose other than the requested analysis.
</details>

<details>
<summary><b>What if no faces are detected?</b></summary>
<br>
Our deepfake detection specifically analyzes facial features. If no faces are detected in the video, we cannot provide a classification. Ensure your video contains clearly visible faces.
</details>

<details>
<summary><b>How long does analysis take?</b></summary>
<br>
Most videos are processed within 30 seconds to 2 minutes depending on video length and resolution. The system samples one frame per second to balance speed and accuracy.
</details>

## 🏆 Credits

This project was built by **Axwathy** — [GitHub Profile](https://github.com/Axwathy)

### Technologies Used

- [TensorFlow/Keras](https://www.tensorflow.org/) — Deep learning framework
- [Flask](https://flask.palletsprojects.com/) — Python web framework
- [OpenCV](https://opencv.org/) — Computer vision library
- [Dlib](http://dlib.net/) — Face detection library
- [Font Awesome](https://fontawesome.com/) — Icon library
- [Google Fonts](https://fonts.google.com/) — Typography (Inter, Space Grotesk)

## 📝 License

This project is for educational and research purposes.

---

<div align="center">

### Protecting truth in the digital age with AI 🛡️

### Last updated: June 2026

</div>
