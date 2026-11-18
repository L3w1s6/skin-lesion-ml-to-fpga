# Datasets Notes

## Ham10000
- 10,015 images
- 7 classes of pigmented skin lesions: benign keratosis, melanocytic nevus, dermatofibroma, melanoma, vascular lesion, basal cell carcinoma, and actinic keratosis
- Used as training dataset for task 3 of ISIC 2018 challenge
- Dermoscopic images collected from different populations, acquired and stored via different modalities
- Final dataset created for academic machine learning purposes
- Includes cases that represent all important diagnostic categories for pigmented skin lesions: Actinic keratoses and intraepithelial carcinoma / Bowen's disease (akiec), basal cell carcinoma (bcc), benign keratosis-like lesions (solar lentigines / seborrheic keratoses and lichen-planus like keratoses, bkl), dermatofibroma (df), melanoma (mel), melanocytic nevi (nv) and vascular lesions (angiomas, angiokeratomas, pyogenic granulomas and hemorrhage, vasc)
- Dataset has multiple images of same lesions - tracked via "lesion_id" column



## ISIC
- Different versions of this dataset exist
- Almost all images are dermoscopic images - polarised and zoomed in pictures taken with specialist equipment
### ISIC2020 Challenge
- 23,385 images
- 9 classes of skin lesions: atypical melanocytic proliferation, café-au-lait macule, lentigo NOS, lichenoid keratosis, melanoma, nevus, seborrheic keratosis, solar lentigo, and "unknown" lesions



## PH2 Dataset
- https://doi.org/10.1109/EMBC.2013.6610779
- Exclusively for melanocytic lesions
- 200 dermoscopic photos of both normal & uncommon melanocytic lesions
- Combined with expertly annotated ground truth for precise diagnosis



## Improving the Quality of Skin Lesion Data for Training Vision-Language Models
- https://doi.org/10.21203/rs.3.rs-8871094/v1
- Feb 27, 2026
- Abstract

- Suggests severe class & skin tone imbalance causing bias in most available datasets
- Aim was to combine 2 datasets to make a dataset suited for (Vision-Language Model) VLM training
- Proposes new dataset RHB which is combination of Ham10000 & BCN20000
- RHB optimised for training Google Gemma 3 4B model
- RHB performance is mildly better than Ham10000, BCN20000 has the worst accuracy

- [Dataset](https://huggingface.co/datasets/atufigwege/refined-dataset)
- [Project Code](https://github.com/atu88/gemma-lesion-classifier)

- BCN20000 contains many artifact-heavy images (includes dark borders) so paper suggests further processing that could be done



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



# FPGA Frameworks/Pipelines

## FINN Project Page
- https://xilinx.github.io/finn/
- Accessed 9/11/26

- Implements NN network layers as streaming components (basically a hardware pipeline), super low latency
- Runs NN in constant time determined by layer structure (execution completely input dependant)
- Run speed variance is because of external factors

- Designed for running image classifiers
- Custom resources allocation for individual layers



## FINN: A Framework for Fast, Scalable Binarized Neural Network Inference
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



## A Compiler-Aware Framework for Partitioned Neural Network Inference on FPGA DPUs
- https://doi.org/10.64552/wipiec.v12i2.144
- Aug 25, 2026
- Abstract

- Models with many parameters can be split into separately compilable parts for more flexible deployment
- Vitis AI toolchain unable to properly optimise for models split into smaller compilable parts
- Split models using Vitis AI significantly lose performance
- Proposes a XIR-level splitting framework that can create separate compilable fragments while preserving context required for DPU mapping
- Framework keeps workflow high-level without needing advanced hardware design knowledge or low-level design changes



## find Vitis AI paper? is it still being used?