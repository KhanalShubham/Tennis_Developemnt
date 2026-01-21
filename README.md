# 🎾 AI Tennis Analysis System

## 🚀 Project Overview

The **AI Tennis Analysis System** is a cutting-edge computer vision application designed to analyze tennis match footage automatically. By leveraging state-of-the-art machine learning models, it tracks players and the ball, maps their movements onto a 2D mini-court simulation, and extracts valuable performance statistics such as player speed and distance covered.

This tool is built for coaches, players, and data enthusiasts who want to derive actionable insights from match videos without manual tagging.

## ✨ Key Features

- **Object Detection & Tracking**: Utilizes **YOLOv8** to detect and track players and tennis balls with high precision.
- **2D Mini-Court Mapping**: Projects the 3D court view into a standard 2D top-down view using **Homography** and keypoint detection.
- **Shot Analysis**: Detects ball hits and enables trajectory analysis (in progress).
- **Performance Metrics**: Calculates real-time player speed (km/h) and total distance covered (meters).
- **Interactive Web Dashboard**: A modern React-based interface to upload videos and visualize the analysis results.
- **Robust Backend**: Powered by **FastAPI** to handle video processing and serve analytical data.

## 🛠️ Technical Architecture

This project combines multiple advanced computer vision techniques:

1.  **Stage 1: Detection (YOLOv8)**
    - Fine-tuned models detect players and the tennis ball frame-by-frame.
    - Humans are filtered to identify only the two active players on the court.

2.  **Stage 2: Court Line Detection (CNN)**
    - A custom Convolutional Neural Network detects 14 critical keypoints on the tennis court.
    - These points define the geometry of the court for perspective transformation.

3.  **Stage 3: Tracking & Smoothing**
    - Optical flow and custom trackers associates detections across frames.
    - Bounding box smoothing reduces jitter for cleaner visualization.

4.  **Stage 4: Perspective Transformation (Homography)**
    - A Homography matrix maps coordinates from the video frame (pixels) to real-world dimensions (meters).
    - This allows for accurate speed and distance calculations.

## 🏗️ Tech Stack

- **Core AI/ML**: Python, PyTorch, OpenCV, Ultralytics YOLOv8
- **Backend API**: FastAPI, Uvicorn
- **Frontend UI**: React, Vite, TailwindCSS (optional integration)
- **Data Processing**: NumPy, Pandas

## 📦 Installation & Setup

### Prerequisites

- Python 3.8+
- Node.js & npm
- GPU (Recommended for faster inference)

### 1. Clone the Repository

```bash
git clone https://github.com/KhanalShubham/Tennis_Developemnt.git
cd Tennis_Developemnt
```

### 2. Backend Setup

Create a virtual environment and install dependencies:

```bash
cd tennis_analysis
python -m venv venv
# Windows
.\venv\Scripts\activate
# Mac/Linux
source venv/bin/activate

pip install -r requirements.txt
```

_Note: Ensure you have the trained YOLO models (.pt) placed in the `models/` directory._

### 3. Frontend Setup

```bash
cd frontend
npm install
```

## 🚀 Usage

1.  **Start the Backend**:

    ```bash
    # From tennis_analysis directory
    python backend/main.py
    ```

    The server typically runs on `http://localhost:8000`.

2.  **Start the Frontend**:

    ```bash
    # From frontend directory
    npm run dev
    ```

    Access the UI at `http://localhost:5173`.

3.  **Analyze a Match**:
    - Open the Web UI.
    - Upload a tennis match video (MP4/AVI).
    - Wait for the processing pipeline to finish.
    - View the generated output video with overlayed statistics and the 2D mini-map.

## 🤝 Contribution

Contributions are welcome! If you'd like to improve the tracking accuracy or add new metrics, please fork the repository and submit a Pull Request.

## 📜 License

This project is open-source and available under the **MIT License**.
