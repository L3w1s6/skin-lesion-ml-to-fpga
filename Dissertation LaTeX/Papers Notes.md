# Research Papers Notes



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
- Compared against [Nugroho et al.](https://doi.org/10.1109/ICECS49266.2020.9294814), same test accuracy of 78% but this required less epochs

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



## FINN: A Framework for Fast, Scalable Binarized Neural Network Inference
- https://doi.org/10.1145/3020078.3021744
- Feb 22, 2017
- abstract
### Design
- Presents FINN framework to build fast and flexible FPGA accelerators
- Uses set of optimisations to efficiently map binarized NN to hardware
- Implements fully connected convolutional and pooling layers with per-layer compute resources tailored to user provided throughput requirements
- Reduces floating point weights and activation functions to binary
- FINN assumes all BNN parameters can fit into available On-Chip Memory (OCM) on single FPGA

### Results
- Run on ZC706 embedded FPGA platform with < 25W total power
- Up to 12.3 mil image classifications per second with 0.31us latency

- MNIST dataset - 12.3mil image classifications per second with 0.31us latency, 95.8% accuracy
- CIFAR-10 dataset - 21906 image classifications per second with 283us latency, 80.1% accuracy (94.9% accuracy for SVHN dataset)



## 
- https://doi.org/10.1109/ICCCNT56998.2023.10308160
- 2023

- notes
<!-- - incremental learning Support Vector Machine (SVM) mapped to PYNQ overlay on Xilinx Zynq-7020 FPGA -->



## 
- https://www.mdpi.com/2075-4418/13/19/3147
- 2023

- notes
<!-- - review of recent methods for skin lesion classification, segmentation and detection -->



# Online Documentation Notes



## PYNQ-Z1 Reference Manual
- https://digilent.com/reference/programmable-logic/pynq-z1/reference-manual
- Accessed 20/10/2026

- List of all hardware features of PYNQ-Z1 board
- List of hardware specs
- Explains architecture with useful diagram (Zynq APSoC)
- Talks of SoC as 2 distinct systems: Processing System (PS) and Programmable Logic (PL)
- PS has an ARM dual-core processor, connected to IO and PL via bus
- PL can connect indirectly through same bus to everything PS can
- Shorting specific pins sets up board modes:
    - Running a Linux bootloader (from a few different storage options)
    - Headless without OS overhead but requires connecting via physical pins



## FINN Docs
- https://finn.readthedocs.io/en/latest/
- Accessed 21/10/2026

- FINN used to describe 2 separate but related areas: FINN Project, FINN Compiler
### FINN Project

### FINN Compiler