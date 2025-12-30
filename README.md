# Structure from Motion (SfM)
his project implements an incremental **Structure from Motion (SfM)** pipeline to reconstruct a **sparse 3D point cloud** from a monocular image sequence using classical multi-view geometry techniques.
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

## Dataset

* **Gustav II Adolf dataset** (monocular image sequence)
* Images captured with sufficient overlap for multi-view geometry
* Camera intrinsic parameters provided in `K.txt`

## 📤 Output

* **Colored sparse 3D point cloud**
* Exported in `.ply` format
* Viewable in **MeshLab** or **CloudCompare**

## ⚙️ Environment Setup

This project was developed and tested in **Google Colab**.

```bash
pip install tomlkit
pip uninstall opencv-python opencv-python-headless -y
pip install opencv-python
