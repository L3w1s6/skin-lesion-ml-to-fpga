# Research Papers Notes - Skin Lesion Classification Models Surveys

## Skin Lesion Classification and Detection Using Machine Learning Techniques: A Systematic Review
- https://doi.org/10.3390/diagnostics13193147
- Aug 30, 2023
- Abstract, Skin Datasets
### Coverage
- Reviews recent methods for skin lesion classification, segmentation & detection
- Examines other papers methods
- Highlights notable datasets, benchmark challenges, evaluation metrics relevant to skin lesion analysis
- Contains summary of major trends, challenges, potential future directions
### Datasets
- Section 4 tables 4-7 have a variety of details on datasets:
    - ISIC2020 - 2020, multiple versions with varying properties: 1884 - 11,108 images, 2 - 8 categories
    - Ham10000 - 2018, 10,015 images, 8 categories
    - BCN20000 - 2019, 19,424 images, 9 categories
    - MSK 1-5 - 2015 & 2017, 3,918 images, 15 categories



## Deep Learning-Based Dermatological Condition Detection: A Systematic Review With Recent Methods, Datasets, Challenges, and Future Directions
- https://doi.org/10.1109/ACCESS.2023.3339635
- Dec 5, 2023
- Abstract, Datasets Table, Conclusion

- More generally on detecting all dermatological conditions
- Dermatological conditions includes: "various skin issues such as rashes, moles, acne, blisters, hives, nodules, cysts, macules, and papules"
- Study of 22 methods for detecting dermatological conditions from dermoscopic images
- Reviews clinical diagnostic methods and need for computer-aided diagnostics for dermatological conditions
- Summarises majority of datasets available (P26)
- Presents challenges & potential future directions



## Diagnosis and prognosis of melanoma from dermoscopy images using machine learning and deep learning: a systematic literature review
- https://doi.org/10.1186/s12885-024-13423-y
- Jan 13, 2025
- Abstract

- 



## A comprehensive study of skin lesion segmentation and classification using deep learning techniques
- https://doi.org/10.3389/frai.2026.1907266
- Oct 23, 2026
- Abstract

- Focuses on a wide range of topics ranging from image preprocessing to sophisticated model architectures
- Major open problems include (copy-pasted): class imbalance, data bias, domain shift, limited representation of diverse skin tones, inadequate external validation, computational requirements, and limited explainability of efficient models
- 



## Characteristics of publicly available skin cancer image datasets: a systematic review
- https://doi.org/10.1016/S2589-7500(21)00252-1
- Nov 9, 2021
- Abstract, Methods, Results

- Analyses in depth characteristics of many datasets available as of 2021
### Quantities of Datasets
- 22 datasets excluded for being subsets of other datasets
- 29 individual datasets and 20 individual atlases remaining after removing duplicates
- 21 open access datasets, 17 open access atlases included images that could be downloaded without barriers
### Specific Datasets
- Multiple ISIC versions included
- Ham10000
- BCN20000
- etc.



# Research Papers Notes - Skin Lesion Classification (Unrelated to FPGAs)

## DSCC_Net: Multi-Classification Deep Learning Models for Diagnosing of Skin Cancer Using Dermoscopic Images
- https://doi.org/10.3390/cancers15072179
- Apr 6, 2023
- Abstract

- Proposes deep learning-based skin lesion classification network DSCC_Net
- DSCC_Net based on CNN, implemented on 3 benchmark datasets: ISIC2020, Ham10000, DermIS



## Advanced hybrid transformer CNN framework for improved skin lesion classification and segmentation
- https://doi.org/10.1038/s41598-026-43376-0
- Mar 15, 2026
- Abstract

- Transformer-based dual-architecture, contains multiple models for skin lesion classification and segmentation
- Based on Global Contextual Vision Transformer (GlobalSkinNet) which is a combination of convolution and transformer models
- GlobalSkinNet model trained using selected parameters & Adam optimiser for skin lesion classification



## Multimodal skin lesion classification for early cancer diagnosis using deep learning
- https://doi.org/10.3389/fphys.2026.1717517
- Feb 9, 2026
- Abstract

- Combines 3 prominent DCNN architectures into single model - DenseNet 201, VGG16, InceptionV3

- Used Ham10000 dataset - applied a variety of preprocessing methods
### Method
1. Creating customised CNN models:
    1. Top layers of base model re-trained
    2. Re-trained half layers of base models and additional layers added
2. Merged customised models and tuned hyperparameters to enhance performance
3. Model dependency for clinical applications improved using Grad-CAM
### Results
- New combined model outperforms individual models with testing accuracy of 97.9%, precision of 99.2%