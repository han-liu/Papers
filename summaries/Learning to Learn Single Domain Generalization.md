[2021-04-14]
- Learning to Learn Single Domain Generalization [[pdf]](https://arxiv.org/pdf/2003.13216.pdf) 
- *Fengchun Qiao, Long Zhao, Xi Peng*
- `2020, CVPR`
- [code](https://github.com/joffery/M-ADA)

****

### Objective
Domain generalization

### Proposed Method
The proposed method consists of two components: (1) segmentation model and (2) DAE. The segmentation model was firstly trained using the weak labels. Weighted cross-entropy loss is used to balance the foreground and background. Then, the outputs of initial segmentation results are used to train DAE. Three noise augmentation strategies are used: (1) closing, (2) dialtion and (3) extension of marginal slice. The intersection of DAE input and output is computed and thresholded according to the probability of DAE input (uncertainty filtering). Two thresholds are used for foreground and background. Then two components are trained jointly.

![Alt text](https://github.com/han-liu/Papers/blob/master/figures/Weakly%20Supervised%20Volumetric%20Segmentation%20via%20Self-taught%20Shape%20Denoising%20Model.png?raw=true)


### Comments

- It would be more informative if we can visualize the initial segmentation results and the DAE refined masks. 

- The weakly-supervised mechanism seems to work similarly like patch-based segmentation, where the foreground defined by weak labels can be considered as deformed patches. Hoepfully, the foreground pixels with correct weak labels can be learned and generalized to other unlabeled foreground pixels. 