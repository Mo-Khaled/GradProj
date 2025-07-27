# 🚗 AI-Powered Obstacle Detection & Monitoring System for Smart Cars

## 🔍 Overview

This project is an end-to-end AI agent system that uses LiDAR point cloud data to:
- Detect obstacles in real-time.
- Assess obstacle severity.
- Initiate safe actions: from alerts to autonomous braking.
- Provide driver assistance via PointNet visualization.
- Monitor internal car health and display it on a car-friendly UI.
- Simulate the full environment using open-source tools.

This solution is built on **Raspberry Pi**, and integrates **LiDAR**, **AI models (like PointNet)**, and a **React-based UI** for real-time data visualization.

---

## 👥 Team Roles

| Member | Role | Responsibilities |
|--------|------|------------------|
| Member 1 | Hardware Integration Engineer | Configure Raspberry Pi, interface with LiDAR, setup CAN Bus, GPIO sensors. Tools: Raspberry Pi OS, Python, SSH. |
| Member 2 | Data Engineer | Collect, preprocess and annotate point cloud data, optimize dataset pipeline. Tools: Python, Open3D, ROS, pandas. |
| Member 3 | AI/ML Engineer | Implement PointNet for classification/segmentation, train/test/validate obstacle detection model. Tools: PyTorch, CUDA, matplotlib, NumPy. |
| Member 4 | Simulation & Testing | Run Carla/LGSVL/ROS Gazebo simulations, test ADAS responses, log metrics. Tools: Carla, ROS2, Python. |
| Member 5 | UI & Integration Engineer | Build car dashboard interface to show detected objects, alerts, and internal sensors. Tools: React.js, Flask, WebSocket, CAN Bus SDKs. |

---

## 🛠️ Technologies & Tools

- **Hardware**: Raspberry Pi 4, LiDAR sensor (Velodyne or RPLIDAR), CAN Bus adapter
- **Software**: Python, PyTorch, ROS2, Open3D, Carla/LGSVL, Flask, React.js
- **AI Models**: PointNet (Segmentation + Classification)
- **DevOps & Deployment**: Docker, Dify.ai (for LLM agents), GitHub Actions

---

## 🧠 AI Model Pipeline

1. **Input**: Raw 3D point cloud from LiDAR.
2. **Transform**: Through T-Net for alignment invariance.
3. **Feature Extraction**: Using shared MLP layers.
4. **Classification/Segmentation**: Obstacle detected, object class, relative location.
5. **Severity Analysis**: Calculate risk based on size, location, speed.
6. **Decision Making**: Either alert the driver or initiate braking.

---

## 🗺️ Environment Mapping & Obstacle Avoidance

- 3D environment built using SLAM or Octomap.
- Point clustering (DBSCAN) for object separation.
- YOLO (optional camera fusion) for visual cross-verification.
- Braking/Steering signals passed via GPIO or CAN Bus.

---

## 🧪 Simulation & Testing

- **Tool**: Carla Simulator + ROS Bridge
- Test scenarios include:
  - Pedestrian crossing unexpectedly.
  - Static obstacle detection.
  - Night-time & low-light obstacle visibility.
- Evaluate false positives, false negatives, braking delay.

---

## 🖥️ Driver Dashboard UI

- Built using React.js & WebSocket connection to Raspberry Pi.
- Displays:
  - Real-time segmented LiDAR view (PointNet Output)
  - Oil temperature, tire pressure, internal system diagnostics.
  - Alerts for detected objects.
  - Current driving suggestion (Manual / Auto Brake)

---

## 🧱 GitHub Repository Structure

```
ai-car-agent/
│
├── backend/                  # Flask + AI models
│   ├── lidar_reader.py
│   ├── pointnet_model.py
│   ├── severity_analyzer.py
│   ├── api.py
│   └── requirements.txt
│
├── frontend/                 # React.js dashboard
│   ├── public/
│   └── src/
│       ├── components/
│       └── App.js
│
├── simulation/               # Carla/ROS2 scenarios
│   └── pedestrian_test.launch
│
├── deployment/               # Docker, Dify, agent logic
│   ├── Dockerfile
│   └── docker-compose.yml
│
├── data/                     # Preprocessed LiDAR datasets
│   ├── raw/
│   ├── processed/
│   └── labels/
│
├── docs/                     # Design documents & deliverables
│   └── architecture_diagram.png
│
└── README.md
```

---

## 📦 Deployment

- Package backend using **Docker** for Raspberry Pi ARM build.
- Use **Dify** for natural language interface (optional):
  - Example: “Is it safe to overtake now?” → Dify consults vision + speed.
- Auto start agent on boot using `systemd` service.
- Use **RAG (Retrieval-Augmented Generation)** to reduce hallucination if LLMs involved (e.g., querying manuals for sensor errors).

---

## 📚 Sample Datasets & Simulation Resources

- [SemanticKITTI](http://www.semantic-kitti.org/dataset.html) – Point cloud semantic segmentation
- [Carla Simulator Scenarios](https://carla.org)
- [Open3D LiDAR examples](http://www.open3d.org/)
- [Velodyne sample data](https://github.com/VelodyneLiDAR)

---

## ✅ Deliverables

- [x] Preprocessed LiDAR Dataset
- [x] Trained PointNet Model
- [x] Raspberry Pi LiDAR Stream
- [x] React.js Dashboard
- [x] Simulation Logs & Metrics
- [x] GitHub Repo with Docker Deployment
- [x] Final Report + Architecture Diagram

---
