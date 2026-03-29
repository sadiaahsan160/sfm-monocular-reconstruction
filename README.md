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
```


## Neural Radiance Fields (NeRF)

This section implements a **Neural Radiance Field (NeRF)** to model a 3D scene and synthesize novel views using a neural network.

### Pipeline


1. **Data Loading**: Images, camera poses, and focal length are loaded from the Tiny NeRF dataset (`tiny_nerf_data.npz`).
2. **Positional Encoding**: 3D spatial coordinates and viewing directions are encoded into a higher-dimensional space using sinusoidal functions.
3. **Neural Network (MLP)**: The encoded coordinates are passed to a Multi-Layer Perceptron (MLP) that predicts:
   - Volume density (σ)
   - RGB color (c) at each point in 3D space
4. **Differentiable Volume Rendering**: Rays are cast from the camera; radiance and density along each ray are integrated to generate the final image.
5. **Loss & Optimization**: Mean Squared Error (MSE) between rendered and ground truth images is minimized using the Adam optimizer.
6. **Training & Evaluation**: The model is trained on the Tiny NeRF dataset, and performance is evaluated using MSE and PSNR metrics.

**Output:** Photorealistic rendered views

---

### 📂Dataset

* **Images**: 106 images of size 100x100 pixels (RGB)
* **Camera Poses**: 106 camera poses (4x4 transformation matrices)
* **Format**: `.npz` file containing images, poses, and focal length  

---

### Results

#### Original vs Rendered Image
<img width="794" height="394" alt="image" src="https://github.com/user-attachments/assets/2c1bc17d-4452-4ace-80cc-ba708efc59d6" />


### PSNR Over Iterations
<img width="387" height="268" alt="image" src="https://github.com/user-attachments/assets/d7cdd794-c5ed-4e55-9a2c-22bdee118ef7" />

### Video Visualization
![video](https://github.com/user-attachments/assets/4e6217fb-c47f-4362-a43c-1c64ce16449c)

---

## Key Insights

- SfM reconstructs explicit 3D geometry using feature correspondences across images  
- NeRF learns an implicit representation of the scene using neural networks  
- SfM is efficient and interpretable but produces sparse reconstructions  
- NeRF generates high-quality renderings but requires significant computation  

---
