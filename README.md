# 3D Reconstruction using SfM and NeRF

## Overview
This project explores 3D reconstruction from images using two fundamentally different approaches:

- **Structure from Motion (SfM)** — a classical geometry-based pipeline  
- **Neural Radiance Fields (NeRF)** — a deep learning-based neural rendering method  

Both approaches are implemented independently to understand their principles, capabilities, and differences in reconstructing 3D scenes.

## Structure from Motion (SfM)

This section implements an incremental **Structure from Motion (SfM)** pipeline to reconstruct a **sparse 3D point cloud** from a monocular image sequence.

Camera poses and 3D points are estimated progressively as new images are added.


### Pipeline Overview

The SfM pipeline consists of the following stages:

1. Camera intrinsic loading
2. Feature detection and matching (SIFT + KNN)
3. Essential matrix estimation (RANSAC)
4. Camera pose recovery
5. Triangulation of 3D points
6. Incremental pose estimation using PnP
7. Reprojection error validation

Output: Sparse 3D point cloud (.ply)

### 📂 Dataset

* Monocular image sequence with sufficient overlap
* known Camera intrinsic parameters (`K.txt`)`
  <img width="641" height="272" alt="image" src="https://github.com/user-attachments/assets/877e1a91-f8f9-4c3f-9ae1-c08fd49b6d03" />



### 📤 Output
- **Feature points** detected using SIFT  
- **Feature matches** between frames  
- **Colored sparse 3D point cloud** (`.ply` format), viewable in **MeshLab** or **CloudCompare**  

  
#### Feature points
<img width="220" height="307" alt="SIFT features" src="https://github.com/user-attachments/assets/d6d27b00-eac1-45b0-b890-070a7da9cfda" />  


#### Sparse 3D point cloud
<img width="837" height="293" alt="Sparse 3D point cloud" src="https://github.com/user-attachments/assets/044566ce-bd70-412f-a7b5-bb778bf46c0d" />  



### ⚙️ Dependencies

* Python 3.x  
* OpenCV (`opencv-python`)  
* NumPy  
* SciPy  
* Matplotlib  
* tqdm  
* tomlkit  

Install via pip:

```bash
pip install opencv-python numpy scipy matplotlib tqdm tomlkit
