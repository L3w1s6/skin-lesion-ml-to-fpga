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

Use TensorFlow (for Keras 3 workflow) to resize/normalise
- Downscale from 450x600 to 224x224x3 (RGB) to match VGG16
- Pixel normalisation
### 2. ML model - Workflow to replicate SCDNet
#### Architecture
- They tested with dropout values of 0.05, 0.2, 0.25 - only 0.2 proved significant (avoids overfitting)

Replicating model layers:
- Input - 224x224x3 shape
- VGG16	- VGG16 using ImageNet weights - containing 5 blocks: 64 -> 128 -> 256 -> 512 -> 512
- CNN Layer 1 - Conv2D + ReLU
- CNN Layer 2 - Conv2D + ReLU + Normalisation
- Pooling & Flatten - MaxPooling2D + Flatten or GlobalAveragePooling2D
- Regularisation 1 - Dropout
- Hidden Dense layer - Dense (512) with ReLU activation function
- Regularisation 2 - Dropout (same val as other dropout)
- Output dense + softmax - Dense (4, number of classes) with softmax activation function

#### Training
- Run training for 50 epochs
- Batch size 20
- SGD (stochastic gradient descent) optimiser set initial learning rate to 0.05, learned rate decreased by 0.1 after 10 epochs to avoid overfitting, momentum set to 0.8

- Training may need to be split into 2
	- Freezing VGG16 layers to not disturb pre-trained ImageNet filters during main learning
	- Fine tune VGG16 top block with learning rate 100 factors smaller (could help better identify lesion borders)

- Epochs and batch size are specified at model.fit() (after building and compiling model)
### 3. Quantise - Changes/additions to ML workflow to shrink model
- Primarily use QKeras - minimal changes to QConv2D and QDense etc.
- Also use FTMOT pruning - can be used alongside, wraps each layer

- Both can be adjusted per layer to maximise effectiveness
### 4. Deploy - Put on PYNQ-Z1 FPGA via hls4ml (and/or FINN if time or can't shrink model enough)


## Eval metrics
### Model
- Accuracy
- F1 score
- Precision
- Sensitivity
### Model Compression
- Per layer bit precision using QKeras
- Per layer pruning tuning using TFMOT

## Potential Experiments
- ISIC2019 (4 classes) vs Ham10000 (7 classes)
- hls4ml model stats vs FINN model stats
- Baseline vs SCDNet paper
- Deployed model stats vs baseline model stats