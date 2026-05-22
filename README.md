# COVA-SLAM: Co-Visibility-Based Adaptive Dynamic Thresholding for Visual SLAM

This repository contains the official implementation of **COVA-SLAM**, a visual SLAM system based on 3D Gaussian Splatting with co-visibility-based adaptive dynamic thresholding. 

This paper has been accepted at the **IEEE/ASME International Conference on Advanced Intelligent Mechatronics (AIM)**.

COVA-SLAM builds upon the [MonoGS](https://github.com/muskie82/MonoGS) architecture, extending it with an adaptive thresholding mechanism to improve tracking robustness and mapping quality in dynamic or complex environments.

## 🛠️ Installation

### 1. Environment Setup
We recommend using Conda to manage your environment.

```bash
# Create the environment
conda env create -f environment.yml

# Activate the environment
conda activate MonoGS
```

### 2. Install Submodules
COVA-SLAM requires specific submodules for Gaussian Splatting rasterization and KNN calculations.

```bash
# Install specialized rasterizer
cd submodules/diff-gaussian-rasterization
pip install .

# Install simple-knn
cd ../simple-knn
pip install .
cd ../..
```

## 📊 Dataset Preparation

We provide scripts to download and set up common evaluation datasets (TUM, Replica, Euroc).

```bash
# Download TUM RGB-D sequences
bash scripts/download_tum.sh

# Download Replica sequences
bash scripts/download_replica.sh

# Download Euroc sequences
bash scripts/download_euroc.sh
```

By default, the datasets will be stored in the `datasets/` directory.

## 🚀 Running COVA-SLAM

### Running with GUI
To run COVA-SLAM on a specific sequence with the interactive GUI:

```bash
python slam.py --config configs/rgbd/tum/fr1_desk.yaml
```

### Evaluation Mode (Headless)
To run the system in evaluation mode (without GUI, results saved for wandb/logging):

```bash
python slam.py --config configs/rgbd/tum/fr1_desk.yaml --eval
```

## ⚙️ Configuration
Configuration files are located in the `configs/` directory, organized by sensor type and dataset:
- `configs/mono/`: Monocular setups
- `configs/rgbd/`: RGB-D setups
- `configs/stereo/`: Stereo setups
- `configs/live/`: Real-time Realsense setups

You can modify the `.yaml` files to adjust hyperparameters such as the COVA thresholding parameters, learning rates, or Gaussian densification intervals.

## 📈 Logging with WandB
This project supports [Weights & Biases](https://wandb.ai/) for experiment tracking. To enable it, ensure `use_wandb: True` is set in your config file or run with the `--eval` flag.

## 📜 Acknowledgments
This project is built upon several excellent open-source libraries:
- [MonoGS](https://github.com/muskie82/MonoGS): The base framework for our SLAM system.
- [3D Gaussian Splatting](https://github.com/graphdeco-inria/gaussian-splatting): The underlying point-based rendering technique.
- [Tiny Gaussian Splatting Viewer](https://github.com/limacv/GaussianSplattingViewer): Used for our interactive GUI.

Please refer to [Dependencies.md](Dependencies.md) for detailed licensing information of these components.

## 📝 Citation
If you find our work useful, please consider citing:

```bibtex
@inproceedings{akbaci2026cova,
  title={COVA: Co-Visibility-Based Adaptive Dynamic Thresholding for Visual SLAM},
  author={Akbaci, H., Kaya, O. and Bayraktar, E.},
  booktitle={IEEE/ASME International Conference on Advanced Intelligent Mechatronics (AIM)},
  year={2026}
}
```

## 📄 License
This project is licensed under the terms of the license found in [LICENSE.md](LICENSE.md).
The modifications for COVA-SLAM are Copyright (c) 2025 Akbaci H, Bayraktar E.
Original MonoGS code is Copyright (c) 2023 Matsuki H, Murai R, Kelly P, Davison A.
