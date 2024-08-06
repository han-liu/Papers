[2021-04-06]
- DARCNN: Domain Adaptive Region-based Convolutional Neural Network for Unsupervised Instance Segmentation in Biomedical Images [[pdf]](https://arxiv.org/pdf/2104.01325.pdf) 
- Joy Hsu, Wah Chiu, Serena Yeung*
- `2021, CVPR`
- code not available.

****

### Objective
UDA with concept shift (from COCO to medical image).

### Proposed Method
Mask-RCNN is used as the backbone network for two-stage training. In the first stage, a shared encoder is used to extract the domain-invariant features. MMD loss is used to align the features from source and target domains. Separate encoders are used to extract the domain-specific features for source and target domain. Soft space orthogonality constraint loss is used: only half of the domain-invariant and domain-specific features are used to compute the orthogonal loss. Domain-invariant features are then used for region proposal. Then class-agnostic proposals are used to compute the foreground and background. The background regions above a pre-defined threshold is used as a mask for the target-domain features. The variance of the filtered features is minimized (consistency loss). For second-stage traininig, confident pseudo-labels from first stage are used as supervision and intensity transformations are used for data augmentation.

![Alt text](https://github.com/han-liu/Papers/blob/master/figures/DARCNN.png?raw=true)


### Comments
- The problem that this paper aims to address is interesting: concept shifts, but there are some concerns regarding the proposed methods and experiments.

- It was not clear how L<sub>diff</sub> contributes to the whole pipeline from the ablation study. It would be interesting to see the effects of the orthogonal loss, especially when the motivation of using this loss is not strong...

- In section 3.3, 'In addition, to better learn invariances of labels despite
imaging conditions, including quality and noise, we apply data augmentation procedures to strengthen pseudo-labels from the first stage DARCNN. The augmentations ensure that the same instance segmentations will be predicted of a given input regardless of lighting, contrast, and blur'. I thought the consistency between the predictions from original image and augmented image would be considered, as in semi-supervised learning. This may not be a good reason to show why only intensity transformations are considered. Geometric augmentation could also be used for instance segmentation.

- The assumption that the background of each proposal should be consistent is too weak... As in Figure 3, cells could be either white or read backgrounds. This loss would encourage the network to find the proposals with consistent background, e.g., red background, and thus fail to predict the cells in other background, e.g., white.

- Rather than directly tackling the problem of concept shift, I think this paper instead proposed something designed specifically for the applications that have uniform background (which could possibly solved by simply using Otsu thresholding or other techniques). Same issue as the assumption as mentioned above, this method is not a generalizable for concept shift problems in other applications. Thus, I think the performance of this method is not as good as expected as shown in Tabel 1 and Table 2, where the author mentioned that 'even against methods designed for nucleus-specific segmentation' (AJI=0.56 vs proposed AJI=0.51).



