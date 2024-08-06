##### [2022-03-06]
- Unsupervised Domain Adaptation through Shape Modeling for Medical Image Segmentation [[pdf]](https://openreview.net/pdf?id=CwXCs6HObSw) 
- *Yuan Yao, Fengze Liu, Zongwei Zhou, Yan Wang, Wei Shen, Alan Yuille, Yongyi Lu*
- `2022, MIDL`

****

### Objective
Unsupervised domain adaptation segmentation with SHAPE PRIOR

### Proposed Method
In this paper, the authors proposed a Teacher-student based method for UDA segmentation task. Particularly, the SHAPE PRIOR is considered compared to other UDA methods. This paper is highly related to the paper published by the same group: An Alarm System For Segmentation Algorithm Based On Shape Model [[pdf]](https://arxiv.org/pdf/1903.10645.pdf). For source domain, the authors train a segmentation model and a VAE (trained for ground truth mask reconstruction). This segmentation model is used to provide pseudo labels for target domain, while the VAE is used to tell how different the output from the shape prior learned from source domain. Thus, the pseudo-label supervision and the shape prior are considered to be in an adverserial relationship. Note that the teacher model (trained from source domain) has fixed weights, and thus the pseudo labels can be very noisy. Imagine at the beginning of training, the student and teacher model produce similar results but may be very different from the VAE reconstruction (due to domain shift). Thus at the beginning, the VAE loss is dominating. Later, the training should be stopped at a point such that there's a balance between pseudo-label loss and VAE loss. The weighting factor of VAE loss is adjusted through the training process based on the VAE reconstruction loss. Both pseudo-label loss and VAE reconstruction loss are Dice loss. Also, during testing, 1 iteration is optimized.


![Alt text](https://github.com/han-liu/Papers/blob/master/figures/Unsupervised%20Domain%20Adaptation%20through%20Shape%20Modeling%20for%20Medical%20Image%20Segmentation.png?raw=true)


### Comments
- Limitations:
  	- The weights in the source model are fixed and thus the pseudo labels are never updated. How about some self-training methods which update the noisy label after each epoch?
	- This method would not work if the domain shift is huge: the source model on target data should at least produce some reasonable results. I think this is the assumption for other teacher-student (target data directly feeds to source model) UDA methods.
	- It seems the shape prior information is especially important for CT pancreas segmentation. It would be interesting to see these VAE based methods on other applications (some other organs with shape priors except pancreas).