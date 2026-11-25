# Methodology Implementation Pipeline
Implementing SCDNet model: https://doi.org/10.3390/s22155652

## Model Workflow
### Primary
Keras -> QKeras -> hls4ml -> Vivado
### Backup (if struggling to shrink model enough)
Keras -> QKeras -> FINN (via QONNX) -> Vivado (through FINN)

## Steps
### 1. Dataset - Download then pre-process
Use scikit-learn to create splits
- Ratio: 70% train, 20% test, 10% validate
- Target classes - Melanoma (MEL), Melanocytic Nevi (NV), Benign Keratosis (BKL), Basal Cell Carcinoma (BCC)

Use tensorflow (for Keras 3 workflow) to resize/normalise
- Downscale from 450x600 to 244x244x3 (RGB) to match VGG16
- Pixel normalisation
### 2. ML model - Workflow to replicate SCDNet
### 3. Quantise - Changes/additions to ML workflow to shrink model
### 4. Deploy - Put on PYNQ-Z1 FPGA via hls4ml (and/or FINN if time or can't shrink model enough)

## Potential Experiments
- ISIC2019 (4 classes) vs Ham10000 (7 classes)
- hls4ml model stats vs FINN model stats
- Baseline vs SCDNet paper
- Deployed model stats vs baseline model stats