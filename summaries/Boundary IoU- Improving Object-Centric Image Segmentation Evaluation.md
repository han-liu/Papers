[2021-04-15]
- Boundary IoU: Improving Object-Centric Image Segmentation Evaluation [[pdf]](https://arxiv.org/pdf/2103.16562.pdf) 
- *Bowen Cheng, Ross Girshick, Piotr Dollar, Alexander C. Berg, Alexander Kirillov*
- `2021, CVPR`
- [code](https://bowenc0221.github.io/boundary-iou/)

****

### Objective
Domain generalization (classification)

### Proposed Method
The proposed method aims to improve the model generalization ability by training on adversial samples. Three loss terms are considered: (1) classification loss: cross-entropy loss, (2) constraint loss and (3) relaxation loss. The constraint loss aims to have an opposite effects as the relaxation loss: limited domain transportation vs relaxation of semantic consistency (similar to GAN, they have an adverserial relationship). Specifically, the constraint loss is used to minimize the Wasserstein distance between the latent features between source domain image and adverserial samples. The relaxation loss is computed by using a WAE (pre-trained on source domain images) and expected to `maximize` the reconstruction loss of adverserial samples. Lastly, meta-learning to used where meta-train is the source domain images while meta-test is the adverserial samples.

![Alt text](https://github.com/han-liu/Papers/blob/master/figures/Learning%20to%20Learn%20Single%20Domain%20Generalization.png?raw=true)


### Comments

- Very interesting paper to read. It seems that meta-learning is a powerful tool for domain generalization problems. The WAE used in this paper is essentially a domain classifier which can be trained without domain code/ground truth. 
