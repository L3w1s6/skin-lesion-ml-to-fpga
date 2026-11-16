# Research Papers Notes - Running NN on FPGA

## Moving Healthcare AI Support Systems for Visually Detectable Diseases to Constrained Devices
- https://doi.org/10.3390/app142411474
- Sep 27, 2024
- abstract
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



## Design and Implementation of a Real-Time Embedded System for Early Skin Cancer Detection
- https://doi.org/10.1115/1.4069441
- Dec 22, 2025
- abstract, conclusion
### Design
- Paper contains hardware and software co-design
- Software design centred around an optimised lightweight NN
- "Self-Supervised Multidomain Knowledge Distillation (SSMD-KD) framework"
- introduces: "multilayer feature knowledge distillation (MFKD) loss to replace the original single-layer distillation method"
- Distillation framework uses ResNet50 model as teacher, MobileNetV2 model as student

- Combines quantitative training to achieve model compression & optimisation
- Fuses patient clinical metadata with image features

- Optimised model run on Xilinx Zynq-7020 SoC
- [Baseline KD method paper](https://doi.org/10.1016/j.media.2022.102693)
### Results
- Used ISIC2019 dataset to test proposed framework
- Classification accuracy of 86% on test set across 8 skin lesion classes
- Inference speed of 14.28FPS
- Power usage of only 2.9W
### Conclusion
- SSMD-KD improves skin lesion recognition of MobileNetV2 model - overall classification accuracy of 86% is 1.1% higher than original model
- Acceleration architecture for Zynq-7020 achieves 14.28FPS - 2.6x higher than existing FPGA solution (baseline paper above)
- Not been tried in actual clinical setting but designed to be for real-time



## 
- https://doi.org/10.1109/ICCCNT56998.2023.10308160
- 2023

- notes
<!-- - incremental learning Support Vector Machine (SVM) mapped to PYNQ overlay on Xilinx Zynq-7020 FPGA -->