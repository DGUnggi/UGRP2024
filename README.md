# UGRP2024
Mar, 2024 - Dec, 2024
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
- Noise Map Extraction Model : CBDNet-pytorch(Matlab pytorch


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

We accomplished 1% Map(Mean Average Precision) increase about NOD dataset!

![image](https://github.com/user-attachments/assets/27b069ee-1db2-4a57-9d43-7491827f6a45)


