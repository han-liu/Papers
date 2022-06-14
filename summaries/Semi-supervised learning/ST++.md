[2022-06-13]
- ST++: Make Self-training Work Better for Semi-supervised Semantic Segmentation[[pdf]](https://arxiv.org/pdf/2106.05095.pdf) 
- *Lihe Yang, Wei Zhuo, Lei Qi, Yinghuan Shi, Yang Gao*
- `2022, CVPR`
- [code](https://github.com/LiheYoung/ST-PlusPlus)

****

### Objective
Semi-supervised learning for semantic segmentation.

### Proposed Method
The proposed method aims to improve the well-established self-training method for semi-supervised segmentation tasks. Two tricks were proposed. (1) The authors proposed to inject strong data augmentation to unlabeled images to alleviate overfitting noisy labels as well as decouple similar predictions between the teacher and student. (2) Three checkpoints are saved at 1/3, 2/3 and 3/3; the mean IoU between the segmentation results from them is used as a measure of the reliability of the unlabeled data. As mentioned in this paper, 'we observe that there is a positive correlation between the segmentation performance and the evolving stability of produced pseudo masks during the supervised training phase. Therefore, the more reliable and better predicted unlabeled images can be selected based on their evolving stability during training'. In the experiments,the authors showed that the proposed image-level selection is better than the pixel-level selection method. 





