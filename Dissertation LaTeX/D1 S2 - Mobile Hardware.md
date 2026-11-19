# Research Papers Notes - Running NN on Mobile Hardware

## Improving Healthcare AI-Support Systems for Skin Lesion Diagnosis With tinyML
- https://doi.org/10.1109/ICDCSW63273.2025.00067
- 2025
- Abstract
- Tess' paper

- Reviewing tinyML for various existing multimodal models
- Proposes healthcare AI-support system for diagnosing in remote areas
- Discusses experiments that will be conducted (no results?):
	- Examining model compression techniques (knowledge distillation, pruning, quantisation)
	- Comparing CNNs with VLMs for skin lesion classification data
	- Developing a cheap, portable, energy-efficient system
- Suggests lack of open-source skin lesion data & research on compressing VLMs for use on constrained devices



## Moving Healthcare AI Support Systems for Visually Detectable Diseases to Constrained Devices
- https://doi.org/10.3390/app142411474
- Sep 27, 2024
- Abstract
- Tess' paper
### Design
- Explores using Tiny Machine Learning (tinyML) to host AI assistant on RPi3 instead of needing internet connection
- Classifying Visually Detectable Diseases (VDD)
- Trained image classifier ML model for VDD
- Model weights offloaded to RPi3
- Model trained on 2 datasets with different training settings

- CNN used MobileNetV2 architecture
- RPi3 runs at 1.5 - 4W
### Results
- Used Ham10000 dataset - achieved classification accuracy of 78%
- Compared against [Nugroho et al.](https://doi.org/10.1109/ICECS49266.2020.9294814), same test accuracy of 78% but this required fewer epochs

- Used ISIC2020 Challenge dataset - achieved classification accuracy of 85%
- Compared against [Aburaed et al.](https://doi.org/10.1109/ICECS49266.2020.9294814), they used Ham10000 with accuracy being 99% because different hyperparameters and more epochs
- Much higher training batch size