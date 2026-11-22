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



# Skin Lesion Classification Papers that Should Be Work on PYNQ-Z1

## SkinLesNet: Classification of Skin Lesions and Detection of Melanoma Cancer Using a Novel Multi-Layer Deep Convolutional Neural Network
- https://doi.org/10.3390/cancers16010108
- Dec 24, 2023
- Abstract, Conclusions, Results

- Proposes SkinLesNet model
- Compared to VGG16 and ResNet50
- Uses dataset extracted from PAD-UFES-20 called PAD-UFES-20-Modified to train and test SkinLesNet (3 classes of skin lesions)

- SkinLesNet generally outperformed ResNet50 and VGG16 in all metrics
- Accuracy of 96% with PAD-UFES-20-Modified
- Accuracy of 90% with Ham10000
- Accuracy of 92% with ISIC2017



## Multiclass Skin Lesion Classification Using a Novel Lightweight Deep Learning Framework for Smart Healthcare
- https://doi.org/10.3390/app12052677
- Mar 4, 2022
- Abstract, Conclusions, Experiment

- Designed to be lightweight and suitable for use on small system like mobile healthcare systems
- Evaluated using Ham10000 and ISIC2019
- Contains table on class distribution in Ham10000

- Evaluated with metrics: precision, sensitivity, specificity, F1 - score, accuracy
- Proposed method accuracy over 3 experiments: 84.8% (Ham1000, 80% train and 20% test), 86.33% (Ham10000, 90% train and 10% test), 82.56% (ISIC2019, 90% train and 10% test)



## SCDNet: A Deep Learning-Based Framework for the Multiclassification of Skin Cancer Using Dermoscopy Images
- https://doi.org/10.3390/s22155652
- Jul 28, 2022
- Abstract, Conclusions, Methodology

- Creates new model called SCDNet
- Combines several models: Vgg16 + specialised CNNs for different types of skin cancer
- Trained and tested using ISIC 2019 dataset
- Accuracy compared with 4 existing classifiers (pre-trained): Resnet 50, Inception v3, AlexNet and Vgg19

- Accuracy of 96.91%



## Gabor wavelet-based deep learning for skin lesion classification
- https://doi.org/10.1016/j.compbiomed.2019.103423
- Sep 4, 2019
- Abstract, Conclusion, Method

- Paper from more biology and medicine perspective (seems less clear about certain details)
- 8 parallel CNNs (looks like 1 per class)
- Model fuses Gabor wavelet-based model with an image-based CNN model
- Training used ISIC2017
### Method
- Extracts spatial frequencies from dataset into 7 directional frequencies (using Gabor filtering) to train 7 CNNs which output probabilities
    - Use pre-trained networks like ResNet architecture
    - Trained independently
- Additional CNN uses original images to generate probabilities (retaining global colour, lesion pigmentation, macroscopic spatial geometry)
- All final output probabilities fused together to get final diagnosis

- Prevents dominant colour patterns overshadowing delicate directional texture cues (improving classification accuracy)
### Results
- Paper doesn't explicitly state final accuracy
- Best performing model is I-GR0235 with M-ACC of 0.83, M-AUC of 0.96
- Max accuracy of model used in paper is 83% (max AUC is 96%)



## A comprehensive analysis of deep learning and transfer learning techniques for skin cancer classification
- https://doi.org/10.1038/s41598-024-82241-w
- Feb 7, 2025
- Abstract, Conclusion, Results

### Method
- Investigates 3 classifying approaches:
    - 3 pre-trained networks as classifiers
    - 3 pre-trained networks as feature extractors along with 4 ML classifiers
    - Find best combination of networks from above approaches
- Used ISIC2018 dataset
- Models combined using concatenation with a (Support Vector Machine) SVM classifier
### Results
- Best merged model accuracy of 92.87% from combining ResNet-18 and MobileNet pre-trained networks