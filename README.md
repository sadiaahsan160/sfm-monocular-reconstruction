# Structure from Motion (SfM)
This project implements an incremental **Structure from Motion (SfM)** pipeline to reconstruct a **sparse 3D point cloud** from a monocular image sequence using classical multi-view geometry techniques.
The implementation follows an incremental SfM approach, where camera poses and 3D points are estimated progressively as new images are added.


# Pipeline Overview

The SfM pipeline consists of the following stages:

1. Camera intrinsic loading
2. Image loading and downscaling
3. Feature detection and matching (SIFT + KNN)
4. Two-view geometry (Essential matrix estimation)
5. Initial camera pose recovery
6. Triangulation of initial 3D points
7. Incremental camera pose estimation using PnP
8. Incremental triangulation of new points
9. Reprojection error validation
10. Sparse point cloud export (`.ply`)

## 📂 Dataset

* Monocular image sequence (e.g., images of a scene captured with sufficient overlap)
* known Camera intrinsic parameters (e.g., `K.txt`)`
  <img width="641" height="272" alt="image" src="https://github.com/user-attachments/assets/877e1a91-f8f9-4c3f-9ae1-c08fd49b6d03" />


## 📤 Output
- Colored sparse 3D point cloud  (`.ply` format)
- Viewable in **MeshLab** or **CloudCompare**
   <img width="220" height="307" alt="image" src="https://github.com/user-attachments/assets/d6d27b00-eac1-45b0-b890-070a7da9cfda" />

   <img width="535" height="393" alt="image" src="https://github.com/user-attachments/assets/05f351c5-1b78-4656-985c-1db5c5b7e817" />


   <img width="837" height="293" alt="image" src="https://github.com/user-attachments/assets/044566ce-bd70-412f-a7b5-bb778bf46c0d" />


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
