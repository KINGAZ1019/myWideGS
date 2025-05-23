# Wideband RF Radiance Field Modeling Using Frequency-embedded 3D Gaussian Splatting


Keywords:
wireless channel; 3DGS; RF radiance field modeling

Abstract: 
This paper presents an innovative frequency-embedded 3D Gaussian splatting (3DGS) algorithm for wideband radio-frequency (RF) radiance field modeling, offering an advancement over the existing works limited to single-frequency modeling. Grounded in fundamental physics, we uncover the complex relationship between EM wave propagation behaviors and RF frequencies. Inspired by this, we design an EM feature network with attenuation and radiance modules to learn the complex relationships between RF frequencies and the key properties of each 3D Gaussian, specifically the attenuation factor and RF signal intensity. By training the frequency-embedded 3DGS model, we can efficiently reconstruct RF radiance fields at arbitrary unknown frequencies within a given 3D environment. Finally, we propose a large-scale power angular spectrum (PAS) dataset containing 50000 samples ranging from 1 to 100 GHz in 6 indoor environments, and conduct extensive experiments to verify the effectiveness of our method. Our approach achieves an average Structural Similarity Index Measure (SSIM) up to 0.72, and a significant improvement up to 17.8% compared to the current state-of-the-art (SOTA) methods trained on individual test frequencies. Additionally, our method achieves an SSIM of 0.70 without prior training on these frequencies, which represents only a 2.8% performance drop compared to models trained with full PAS data. This demonstrates our model's capability to estimate PAS at unknown frequencies. For related code and datasets, please refer to the supplementary materials.

NeurIPS 2025 website page:
[Wideband RF Radiance Field Modeling Using Frequency-embedded 3D Gaussian Splatting](https://openreview.net/forum?id=BddBODS3xX)


## Dataset

The dataset structure of a scene in the path location should be as follows:
```
<scene location>
|---spectrum
|   |---<spectrum 00001>
|   |---<spectrum 00002>
|   |---...
|---freq.txt
|---gateway_info.yml
|---point_cloud.ply
|---test_index.txt
|---train_index.txt
|---tx_pos.csv
```

Note: The current release includes part of sample data of 2 scenes (```./data/example1``` and ```./data/example2```). The full dataset of all 6 scenes will be open-sourced upon acceptance of this paper.

## Setup
Create and activate conda environment
```python
conda env create --file environment.yml
conda activate widegs
```
Install submodules
```python
cd submodules
pip install ./diff-gaussian-rasterization
pip install ./fused-ssim
pip install ./simple-knn
```


## Training & Testing
Use the default dataset path.
```python
python train.py
```
Or specify a dataset path.
```python
python train.py --dataset_path <path to dataset>
```
The model will be evaluated at epochs of the ```--test_iterations``` argument.
The testing results will be saved in ```./logs``` folder and the model checkpoints will be saved in ```./output``` folder.

## Additional Included File Descriptions:
Directory Structure Descriptions:
arguments/: Contains hyperparameters configured for model training.
data/: Provides sample datasets for training purposes.
scene/: Includes Gaussian model implementations and scene-specific code modules.
