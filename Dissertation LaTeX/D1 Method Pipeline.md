# Methodology Implementation Pipeline
Implementing SCDNet model

## Model Workflow
### Primary
Keras -> QKeras -> hls4ml -> Vivado
### Backup (if struggling to shrink model enough)
Keras -> QKeras -> FINN (via QONNX) -> Vivado (through FINN)

## Steps
1. Dataset - Download then pre-process
2. ML model - Workflow to replicate SCDNet
3. Quantise - Changes/additions to ML workflow to shrink model
4. Deploy - Put on PYNQ-Z1 FPGA via hls4ml (and/or FINN if time or can't shrink model enough)

## Potential Experiments
- ISIC2019 (4 classes) vs Ham10000 (7 classes)
- hls4ml model stats vs FINN model stats
- Baseline vs SCDNet paper
- Deployed model stats vs baseline model stats