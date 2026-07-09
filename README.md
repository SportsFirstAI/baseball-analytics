<div align="center">

<img src="https://img.shields.io/badge/AI-Baseball%20Analytics-1a73e8?style=for-the-badge&logo=python&logoColor=white" alt="Baseball AI"/>
<img src="https://img.shields.io/badge/YOLO26%20Pose-Computer%20Vision-00C853?style=for-the-badge&logo=opencv&logoColor=white" alt="YOLO"/>
<img src="https://img.shields.io/badge/License-MIT-f9a825?style=for-the-badge" alt="MIT License"/>
<img src="https://img.shields.io/badge/Google%20Colab-T4%20GPU-FF6F00?style=for-the-badge&logo=googlecolab&logoColor=white" alt="Colab"/>
<img src="https://img.shields.io/badge/Open%20Source-%E2%9D%A4-e91e63?style=for-the-badge" alt="Open Source"/>

<br/><br/>

# ⚾ Baseball Analytics AI Engine

### *Real-time Pitcher Biomechanics · Ball Tracking · Strike Zone Detection · Broadcast Intelligence*

**Powered by YOLO26-Pose · Built by [SportsFirstAI](https://github.com/SportsFirstAI)**

<br/>

</div>

---

## 🎬 Live Demo — AI Output Preview

> ⚡ **Skeleton overlay + real-time joint angle tracking on a live pitcher** — *click to watch full video*

<div align="center">

[![Baseball AI Demo](./demo_preview.gif)](./perfect_visual_broadcast_with_contact.mp4)

<sub>👆 Animated preview (first 3 seconds) · Click GIF to download & watch the full output video</sub>

</div>

---

## 🧠 What This Project Does

**Baseball Analytics AI Engine** is an open-source, notebook-based computer vision system that transforms raw baseball footage into **broadcast-quality analytical overlays** with real-time biomechanics data. Built for coaches, performance analysts, broadcasters, and sports tech enthusiasts.

### 📒 Notebooks Overview

| # | Module | What It Does | Notebook |
|---|--------|-------------|---------|
| 1 | 🦴 **Pitcher Biomechanics** | YOLO26-Pose skeleton isolation — tracks all 17 keypoints, isolates the main pitcher from crowd/background players, overlays real-time joint angles (e.g., elbow degrees) per frame | [`1_pitcher_biomechanics_pose.ipynb`](./Notebooks/1_pitcher_biomechanics_pose.ipynb) |
| 2 | 🔵 **BaseballCV Pro Engine v1** | Full CV pipeline — ball detection, player tracking, trajectory overlays using the BaseballCV library | [`2_BaseballCV_Pro_Engine.ipynb`](./Notebooks/2_BaseballCV_Pro_Engine.ipynb) |
| 3 | 📡 **BaseballCV Pro Engine v2** | Refined tracking with improved model config, GPU optimizations, and enhanced visualization | [`3_BaseballCV_Pro_Engine.ipynb`](./Notebooks/3_BaseballCV_Pro_Engine.ipynb) |
| 4 | 🎯 **Strike Zone Engine** | AI-powered strike zone detection + pitch classification (Strike / Ball / Borderline) using pose estimation and spatial geometry | [`4_Strike_Zone_Engine.ipynb`](./Notebooks/4_Strike_Zone_Engine.ipynb) |

---

## 🔬 How It Works

### Pipeline — Pitcher Biomechanics (Notebook 1)

```
Input Video ──► YOLO26-Large Pose Model ──► 17-Point Keypoint Detection
                                                        │
                                                        ▼
                                          Pitcher Isolation (Largest BBox)
                                                        │
                                                        ▼
                                          Skeleton Drawing + Angle Calc
                                                        │
                                                        ▼
                                             Output Broadcast Video
```

**Step-by-step:**
1. **YOLO26 Inference** — The large pose model processes every frame at high accuracy
2. **Pitcher Isolation** — Identifies the pitcher by finding the **largest bounding box** (eliminates background players, crowd, umpires)
3. **17-Point Skeleton** — Maps standard human keypoints: nose, eyes, ears, shoulders, elbows, wrists, hips, knees, ankles
4. **Trigonometric Angle Calc** — Uses `arctan2` to compute exact joint angles (shoulder → elbow → wrist) in real degrees
5. **Broadcast Overlay** — Skeleton lines in **magenta**, joint dots in **cyan**, angle text in **green**

### Pipeline — Strike Zone (Notebook 4)

1. **Batter Pose Detection** — Locates batter's key body landmarks
2. **Zone Geometry** — Constructs a batter-specific strike zone box based on body proportions
3. **Pitch Classification** — Each pitch evaluated as **Strike**, **Ball**, or **Borderline** in real-time

---

## 🚀 Quick Start

### ▶️ Run on Google Colab (Zero Setup)

> All notebooks are designed for **Google Colab** with a free **T4 GPU**. No local installation needed.

1. Click any notebook link from the table above
2. Open in Google Colab (use the Colab badge or upload manually)
3. Upload your input video file when prompted (rename it to `input_pitch.mp4`)
4. Click **Runtime → Run All**
5. Download the output video when processing completes

### 💻 Run Locally

```bash
git clone https://github.com/SportsFirstAI/baseball-analytics.git
cd baseball-analytics
pip install ultralytics opencv-python numpy baseballcv
jupyter notebook Notebooks/1_pitcher_biomechanics_pose.ipynb
```

### Dependencies

```python
ultralytics    # YOLO26 / YOLOv8 model suite
opencv-python  # Video I/O & frame-level drawing
numpy          # Array math & trigonometry
baseballcv     # Baseball-specific ML utilities (Notebooks 2-4)
```

---

## 📁 Repository Structure

```
baseball-analytics/
│
├── 📓 Notebooks/
│   ├── 1_pitcher_biomechanics_pose.ipynb    ← Pose + skeleton + angle detection
│   ├── 2_BaseballCV_Pro_Engine.ipynb         ← CV pipeline v1
│   ├── 3_BaseballCV_Pro_Engine.ipynb         ← CV pipeline v2 (refined)
│   └── 4_Strike_Zone_Engine.ipynb            ← Strike zone AI classifier
│
├── 🎬 test-video.mp4                         ← Sample input video
├── 🎬 perfect_visual_broadcast_with_contact.mp4  ← AI output demo video
│
├── .gitignore
├── LICENSE
└── README.md
```

---

## 🛠️ Tech Stack

<div align="center">

| Technology | Version | Role |
|-----------|---------|------|
| **YOLO26-Pose (Large)** | v8.4+ | Skeleton keypoint detection |
| **YOLOv8** | Latest | Object detection & tracking |
| **OpenCV** | 4.x | Video I/O, drawing, overlays |
| **NumPy** | 1.x | Angle math, array processing |
| **BaseballCV** | Latest | Domain-specific baseball ML |
| **Google Colab** | — | Cloud GPU runtime (T4) |
| **Python** | 3.10+ | Core language |

</div>

---

## 📊 What Gets Tracked

| Metric | Description |
|--------|-------------|
| **Elbow Angle** | Real-time degrees computed per frame during delivery |
| **Shoulder Rotation** | Tracked via keypoints 5–6 (left/right shoulder) |
| **Hip-Shoulder Alignment** | Posture & stride analysis |
| **Keypoint Confidence** | YOLO26 per-point detection confidence |
| **Pitcher Identity** | Auto-isolated via bounding box area ranking |
| **Pitch Zone** | Strike / Ball / Borderline classification |

---

## 🤝 Open Source & Contributing

This project is **fully open source** under the **MIT License**. We believe sports AI should be accessible to everyone — coaches, developers, researchers, and fans alike.

**You are free to:**
- ✅ Use in personal or commercial projects
- ✅ Fork, modify, and build upon this work
- ✅ Redistribute with attribution
- ✅ Submit pull requests with improvements

### How to Contribute

```bash
# 1. Fork this repository on GitHub
# 2. Clone your fork locally
git clone https://github.com/<your-username>/baseball-analytics.git

# 3. Create a feature branch
git checkout -b feature/your-feature-name

# 4. Make your changes
# 5. Commit with a descriptive message
git commit -m "feat: describe what you added"

# 6. Push and open a Pull Request on GitHub
git push origin feature/your-feature-name
```

**Ideas for contributions:**
- 🎯 Multi-person tracking (catcher + pitcher simultaneously)
- 📈 CSV export of per-frame angle data
- 🏏 Batter swing analysis module
- 📱 Real-time webcam demo mode
- 🌐 Web dashboard for analytics visualization

---

## 📄 License

This project is licensed under the **MIT License** — see [LICENSE](./LICENSE) for full details.

```
MIT License · Copyright (c) 2026 SportsFirstAI
```

---

## 👥 Team & Contact

<div align="center">

| | |
|--|--|
| 🏢 **Organization** | [SportsFirstAI](https://github.com/SportsFirstAI) |
| 👨‍💻 **Developer** | [Ishan-B-Mistri](https://github.com/Ishan-B-Mistri) |

</div>

---

<div align="center">

**⭐ Star this repo if it helped you — it keeps us motivated to build more sports AI tools!**

---

*Made with ❤️ for the baseball analytics community by [SportsFirstAI](https://github.com/SportsFirstAI)*

</div>
