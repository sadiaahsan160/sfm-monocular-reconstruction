# Structure from Motion (SfM)
This project implements an incremental **Structure from Motion (SfM)** pipeline to reconstruct a **sparse 3D point cloud** from a monocular image sequence using classical multi-view geometry techniques.
The implementation follows an incremental SfM approach, where camera poses and 3D points are estimated progressively as new images are added.


# Pipeline Overview

The SfM pipeline consists of the following stages:

1. Camera intrinsic loading
2. Image loading and downscaling
3. Feature detection and matching
4. Two-view geometry (Essential matrix estimation)
5. Initial camera pose recovery
6. Triangulation of initial 3D points
7. Incremental camera pose estimation using PnP
8. Incremental triangulation of new points
9. Reprojection error validation
10. Sparse point cloud export (`.ply`)

## 📂 Dataset

* **Monocular image sequence** with sufficient overlap between frames
* known Camera intrinsic parameters (e.g., in `K.txt`)`

## 📤 Output
- Colored sparse 3D point cloud  (`.ply` format)
- Viewable in **MeshLab** or **CloudCompare**

- <img width="837" height="293" alt="image" src="https://github.com/user-attachments/assets/044566ce-bd70-412f-a7b5-bb778bf46c0d" />


## ⚙️ Dependencies

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
