##### [2021-03-25]
- HyperDense-Net: A Hyper-Densely Connected CNN for Multi-Modal Image Segmentation [[pdf]](https://arxiv.org/pdf/1804.02967.pdf) 
- *Jose Dolz, Karthik Gopinath, Jing Yuan, Herve Lombaert, Christian Desrosiers, Ismail Ben Ayed *
- `2018, TMI`

****

### Objective
Multi-modal image segmentation

### Proposed Method
This paper proposes a multi-path 3D FCN, where layers across different paths are connected in a DenseNet manner. Channel shuffling was used as a strong regularizer to enhance the efficiency and performance. 

### Comments
The proposed method improves model performance by solely modifying network archtectures (dense connections) and thus lacks novelty when we look at it in 2021. This method is not flexible to deal with missing-modality issue. However, since the code is publicly available, this method can serve as a baseline for multi-modal segmentation tasks.
