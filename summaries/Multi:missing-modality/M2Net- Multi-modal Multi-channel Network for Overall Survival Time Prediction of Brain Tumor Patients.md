##### [2021-04-09]
- M2Net: Multi-modal Multi-channel Network for Overall Survival Time Prediction of Brain Tumor Patients [[pdf]](https://arxiv.org/pdf/2006.10135.pdf) 
- *Tao Zhou, Huazhu Fu, Yu Zhang, Changqing Zhang, Xiankai Lu, Jianbing Shen, and Ling Shao*
- `2020, MICCAI`

****

### Objective
Overall survival (OS) prediction (3-class classification) with multi-modality dataset (Brats 2018) 

### Proposed Method
First, 124x124x124 patches are cropped at the center of tumor for four modalities including T1, T1CE, T2 and FLAIR. For each modality, 3D volumes are projected to 2D image by taking the sum of all slices in each direction. The three-channel image of each modality are then fed into separate feature extractors (ResNet34) for domain-specific features. Based on the figure, the features from each moddlity is then connected to a FC layer and concatenated with supplemental feature for classification. However, this was not clearly stated in the paper. Bilinear pooling was used to fuse the features from different feature extractors and fed to FC as another prediction head (shared head). Lastly, the softmax output neurons from each modality and shared head are concatenated for another prediction. 

![alt text](https://github.com/han-liu/Papers/blob/master/figures/M2Net%20Multi-modal%20Multi-channel%20Network%20for%20Overall%20Survival%20Time%20Prediction%20of%20Brain%20Tumor%20Patients.png?raw=true)

### Comments
- It was unclear which prediction head's result was used as the final prediction (I assume the fusion branch is used).

- Bilinear pooling is useful to merge features from different branches.

- Supplemental features could be merged to flattened feature vectors by concatenation.

- The experiments presented in the paper should be divided into comparison to SOTA and ablation studies. It seems that in classification tasks, especially 3D applications, there were no strong or clear baseline methods.

- It does not make sense to me how classification could be performed with only the 2D projection images as inputs... 
