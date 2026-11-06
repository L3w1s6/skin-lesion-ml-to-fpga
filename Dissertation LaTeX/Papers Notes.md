# Research Papers Notes



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



## 
- https://doi.org/10.3390/app142411474
- 2024

- notes
<!-- - exploring using tinyML to run image classification on low-spec devices (Tess') -->



## 
- https://www.mdpi.com/2075-4418/13/19/3147
- 2023

- notes
<!-- - review of recent methods for skin lesion classification, segmentation and detection -->
