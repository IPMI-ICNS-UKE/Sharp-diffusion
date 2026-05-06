# Sharp-Diffusion
This repository prvides code for the assessment of Feature loss for 2D super-Resolution of Diffusion MRI data.  

All code is available as jupyter notebooks which can be customized for application to new data.
Models are trained using data from n=10 subjects from the 7T HCP young adult cohort. 
        
If you are using this repository in your research, please cite [Lohr and Werner](https://github.com/IPMI-ICNS-UKE/Sharp-diffusion):


# Repository setup
1) in your console move to an appropriate directory and clone the repository
```
git clone https://github.com/IPMI-ICNS-UKE/Sharp-diffusion
```
2) create a virtual environment (conda/miniconda) and activate it
```
conda create -n SHARP python=3.10
```
```
conda activate SHARP
```
3) install required dependencies using the requirement.txt
```
pip install -r requirements.txt
```

# Loss function: L1 loss and Feature loss using various layers of the VGG16

# Quality metrics  
MSE and PSNR are tracked during training. Respective metrics could be included into the loss by adjusting the notebook 
util/Diffusion_Perception_loss.ipynb

# Experiments
1) Ablation study: models are trained for 4-fold SR using combinations of VGG16 layers for the loss (Diffusion_SR_Feature_Ablation_desc.ipynb)
2) Isolation study: models are trained for 4-fold SR using isolated VGG16 layers for the loss
(Diffusion_SR_Feature_Isolation.ipynb)
3) Resolution assessment study: selected models are fine-tuned for 9-fold SR
(Diffusion_SR_x3_Transfer.ipynb)

# Data structure of the repository
Download datasets from HCP Servers. Extract HCP files in Sharp-Diffusion/data and run util/nii2png.ipynb to set up Training, Validation, and test splits. 
- 'data/gt/train/xxxxxx'
- 'data/x2/train/xxxxxx'
- 'data/gt/valid/xxxxxx'
- 'data/x2/valid/xxxxxx'
Inference is applied for test data.
- 'data/x2/test/xxxxxx'
post inference run preds2nii to restore nifti files with original intensity scaling



   

