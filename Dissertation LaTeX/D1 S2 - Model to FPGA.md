# Research Papers Notes - Skin Lesion Classification on FPGAs

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



## PYNQ Overlay for SVM-based Melanoma Classification with Learning Ability
- https://doi.org/10.1109/ICCCNT56998.2023.10308160
- 2023

- 
<!-- - incremental learning Support Vector Machine (SVM) mapped to PYNQ overlay on Xilinx Zynq-7020 FPGA -->



# FPGA Frameworks/Pipelines

## FINN
### FINN Project Page
- https://xilinx.github.io/finn/
- Accessed 9/11/26

- Implements NN network layers as streaming components (basically a hardware pipeline), super low latency
- Runs NN in constant time determined by layer structure (execution completely input dependant)
- Run speed variance is because of external factors

- Designed for running image classifiers
- Custom resources allocation for individual layers
### FINN: A Framework for Fast, Scalable Binarized Neural Network Inference
- https://doi.org/10.1145/3020078.3021744
- Feb 22, 2017
- Abstract
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



## Xilinx AI Engines and Their Applications
- https://semiengineering.com/xilinx-ai-engines-and-their-applications/
- Dec 16, 2022
- Abstract, AI Engine Development Environment

- Vitis is software platform which is used for digital signal processing, machine learning
- "Vitis AI is an AI inference development and deployment stack on Xilinx hardware platforms"
- Consists of tools, libraries, models & example designs
- The designs focus on high efficiency & ease of use
### PYNQ Version Support
- Current Vitis AI version is 5.0
- Zynq-7000 family (PYNQ-Z1) unsupported starting with version 1.4
- Evidence: [AMD Support Page 2021](https://adaptivesupport.amd.com/s/article/76742?language=en_US), [Official GitHub Releases](https://github.com/Xilinx/Vitis-AI/releases#release-v1.4)



## hls4ml
- 
- 



## A Compiler-Aware Framework for Partitioned Neural Network Inference on FPGA DPUs
- https://doi.org/10.64552/wipiec.v12i2.144
- Aug 25, 2026
- Abstract

- Builds on Vitis AI
- Models with many parameters can be split into separately compilable parts for more flexible deployment
- Vitis AI toolchain unable to properly optimise for models split into smaller compilable parts
- Split models using Vitis AI significantly lose performance
- Proposes a XIR-level splitting framework that can create separate compilable fragments while preserving context required for DPU mapping
- Framework keeps workflow high-level without needing advanced hardware design knowledge or low-level design changes