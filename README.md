# Sharp-Diffusion
This repository provides code for the assessment of feature loss for 2D super-resolution of diffusion MRI data as published in: Lohr, D and Werner, R. Layer Selection in Feature-Based Losses Affects Image Quality and Microstructural Consistency in Deep Learning Super-Resolution of Brain Diffusion MRI. ArXiv. DOI: 10.48550/arXiv.2605.15895. 2026  

All code is available as jupyter notebooks which can be customized for application to new data.
Models are trained using data from n=10 subjects from the 7T HCP young adult cohort. 
        
If you are using this repository in your research, please cite [Lohr and Werner](https://github.com/IPMI-ICNS-UKE/Sharp-diffusion/edit/master/README.md#citation)

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
4) pre-trained models are available via the associated zenodor repository https://doi.org/10.5281/zenodo.20267632


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
Download datasets from HCP Servers. Extract HCP files in Sharp-Diffusion/data and run util/nii2png.ipynb to set up Training, Validation, and test splits. Folders x2 and gt build low- and high-resolution pairs. 
- 'data/gt/train/volunteerID'
- 'data/x2/train/volunteerID'
- 'data/gt/valid/volunteerID'
- 'data/x2/valid/volunteerID'

Alternatively, set up your own training data following this structure.

# Inference
 For HCP data, nifti files and original original intensity scaling can be restored using preds2nii.ipynb. Adapting the path_base and testfolders enables application to new data (.pngs)

# Citation
```
@misc{lohr2026layerselectionfeaturebasedlosses,
      title={Layer Selection in Feature-Based Losses Affects Image Quality and Microstructural Consistency in Deep Learning Super-Resolution of Brain Diffusion MRI}, 
      author={David Lohr and Rene Werner},
      year={2026},
      eprint={2605.15895},
      archivePrefix={arXiv},
      primaryClass={eess.IV},
      url={https://arxiv.org/abs/2605.15895}, 
}
```
