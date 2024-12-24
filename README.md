# UGRP2024
Mar, 2024 - Dec, 2024
# 📜 Project Overview
- This project proposes a novel pipeline to enhance object detection performance in low-light conditions.
- Core Features: YOLO-based object detection, noise map utilization, and integrated pre/post-processing techniques.
Goals:
- Improve detection accuracy under low-light conditions.
- Ensure real-time data processing.
- Expand applicability in various domains (e.g., autonomous driving, surveillance systems).

## Motivation
In Autonomous driving situation which is especially for Low-light environment, it is difficult to detect object such as car, person, truck, ..etc. Therefore, we suggested Noise Map-Driven Dynamic Framework Processing for improved Object Detection in Low-Light Conditions.
Our pipeline is shown below.

![image](https://github.com/user-attachments/assets/8d705f13-cc20-4ef7-9f2d-d8f4b6133235)

## Requirements
- Jupyter Notebook
- GPU : RTX 3090
- Python 3.8.5
- Low Light Image Enhancement Model : Zero-DiDCE
- Dataset : BDD100k, NOD(Night Object Detection)

# 🚀 Key Features
## Image Preprocessing
Zero-DiDCE: Enhances brightness and quality of low-light images.
CBDNet: Generates noise maps for identifying critical regions.
MFDNet: Removes strong light flares effectively.
NAFNet: Restores blurry images with high efficiency.
## Frame Optimization 
- Reduces computational load by filtering out less significant frames (Frame Drop Mechanism).
## YOLO Model Extension
- Integrates advanced preprocessing methods into the YOLO framework for improved accuracy in low-light environments.


## Frame drop mechainsm psuedo code
```
Initialize frame_queue as empty
For each video file:
   Open video capture
   While video capture is open:
       Retrieve frame from video capture and append to frame_queue
       If frame_queue size == 5:
           Compute average_total_box_area as the mean of total box areas in frame_queue
           Initialize importance_scores as an empty list
           For each frame in frame_queue:
               Compute importance_score as:
               1 - abs(total_box_area - average_total_box_area) / average_total_box_area
               Append importance_score to importance_scores
           Sort importance_scores in descending order
           Select the frame with the highest importance_score
           Save the selected frame and metadata
           Clear frame_queue
       If no more frames in video:
           Release video capture
```

Image processing procedure is shown below

![image](https://github.com/user-attachments/assets/beedc9d6-d209-44e0-a3b3-22d4c365e359)

# 📊 Experimental Results
Dataset: BDD100k, NOD (Night Object Detection)
Key Metrics:
Mean Average Precision (mAP): Improved by ~1%
Average Processing Time: Achieved real-time processing at 20 FPS on RTX 3090

![image](https://github.com/user-attachments/assets/27b069ee-1db2-4a57-9d43-7491827f6a45)

# 🤝 Contributors
Seungbin Lee (sblee1018@dgist.ac.kr)
Unggi Lee (logg72@dgist.ac.kr)
Yeo-Jin Kim (kimyeojink@dgist.ac.kr)
Hanseul Choi (hanseul.choi@dgist.ac.kr)

# Contact
If you have any question about this research or want to see entire report, feel free to contact to logg72@dgist.ac.kr.


