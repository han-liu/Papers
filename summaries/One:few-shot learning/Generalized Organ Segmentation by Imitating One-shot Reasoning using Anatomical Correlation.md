[2021-04-19]
- Generalized Organ Segmentation by Imitating One-shot Reasoning using Anatomical Correlation [[pdf]](https://arxiv.org/abs/2103.16344) 
- *Hong-Yu Zhou, Hualuo Liu, Shilei Cao, Dong Wei, Chixiang Lu, Yizhou Yu, Kai Ma, Yefeng Zheng*
- `2021 IPMI`
- code unavailable.

****

### Objective
One-shot learning for unseen class segmentation

### Proposed Method
The proposed method requires one anchor (atlas) image and mask and unlabeled images for training. Three separate encoders are used for anchor image, anchor mask and fixed image. The encoded features are fused with a pyramid reasoning module, which considers the relationships between the feature vectors of anchor image and fixed image within a neighboring patch. The training strategy is similar to meta-learning: (1) target image is first registered to the anchor image. (2) In each batch, labels of different classes of organs are used for training. TCIA pancreas dataset and BTCV abdomen dataset are used. This method is compared against other one-shot learning method: DataAug, Squeeze-Excitation and LT-Net.

![Alt text](https://github.com/han-liu/Papers/blob/master/figures/Generalized%20Organ%20Segmentation%20by%20Imitating%20One-shot%20Reasoning%20using%20Anatomical%20Correlation.png?raw=true)


### Comments
- One-shot learning here means that only during testing, we need one anchor image and mask for unseen classes. During training, more than one labeled images are involved.

- It would be interesting to know the reason why this method could outperform Voxelmorph-based registeration method. 