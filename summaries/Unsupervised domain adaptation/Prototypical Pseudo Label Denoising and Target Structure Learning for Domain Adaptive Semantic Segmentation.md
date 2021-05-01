[2021-03-26]
- Prototypical Pseudo Label Denoising and Target Structure Learning for Domain Adaptive Semantic Segmentation [[pdf]](https://arxiv.org/pdf/2101.10979.pdf) 
- *Pan Zhang, Bo Zhang, Ting Zhang, Dong Chen, Yong Wang, Fang Wen2*
- `2021, CVPR`

****

### Objective
Unsupervised Domain Adaptation (image segmentation)

### Proposed Method
The proposed DA method employs the self-training strategy. Similar to semi-supervised training, images from source domain (w/ labels) and target domain (w/o labels) are trained simultaneously. Hard labels are used for supervision of target domain data. Hard labels are computed from weighted version of the soft pseudo labels, where the weights are obtained by calculating the softmax over feature distances to prototypes (feature centroids). Initial prototypes are calculated from the target domain data and hard pseudo labels. During training, CE and symmetric cross-entropy (SCE) are used for source and target domain respectively. The prototypes are updated every iteration in an EMA manner, e.g., 0.9999\*pre + 0.0001\*new. Another trick is to enforce the consistency of feature assignment (softmax of feature distance) for strong and weak augmentations by minimizing the KL divergence. Another regularization is used to encourage the output to be evenly distributed to different classes (Confidence regularized self-training). The final loss includes CE(source) + SCE(target) + KL + reg. Lastly, the performance can be further boosted by using pre-trained SimCLRv2 for student model and distilling knowledge from the trained teacher model.


### Comments
Very interesting paper to read. The idea of using feature centroids has recently been popular: [Uncertainty Estimation Using a Single Deep Deterministic Neural Network](https://arxiv.org/pdf/2003.02037.pdf). This method seems similar to the deep learning version of dictionary learning. The techqniues used in this paper seem to be adopted from existing SSL methods. For example, in this paper, EMA is used to update the feature centroids and further update the pseudo labels for target domain; while EMA is used to update teacher model weights and further update the pseudo labels in [Mean teacher](https://arxiv.org/pdf/1703.01780.pdf). The unlabeled data defined in SSL are the target domain data in this paper's setting. Besides, the consistency regularization of strong and weak augmentation is from [Fix-Match](https://arxiv.org/pdf/2001.07685.pdf). Since data from source domain and target domain could be trained at the same time, it suggests the domain shift was not very huge (probabiliy unlike CT and MR). This makes me wonder why SSL methods, e.g., mix-match, are not used/compared in the UDA fields (probabily they were compared somewhere but I did not notice). I like the idea of creating feature centroids and I believe this may also be useful for other topics, e.g., test-time training, uncertainty, OOD detection? Regarding the implementation details, one issue might be that the authors did not specify which layers of the model are used to compute the feature centroids.





