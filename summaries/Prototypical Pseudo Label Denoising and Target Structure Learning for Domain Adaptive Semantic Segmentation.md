k,l,kkk##### [2021-03-26]
- Prototypical Pseudo Label Denoising and Target Structure Learning for Domain Adaptive Semantic Segmentation [[pdf]](https://arxiv.org/pdf/2006.03829.pdf) 
- *Aiham Taleb, Winfried Loetzsch, Noel Danz, Julius Severin, Thomas Gaertner, Benjamin Bergner, and Christoph Lippert*
- `2020, NIPS`

****

### Objective
Self-supervised learning (SSL) for 3D medical image analysis

### Proposed Method
The authors designed 5 pre-text tasks for pre-training and initialize the downstream's encoder with the pre-trained weights.
Five tasks are (1) constrastive predicting code (CPC): encoder to generate latent vector and context network to produce context vector; infoNCE loss is used to compute the similarity of positive/negative pairs (2) relative patch location (3) Jigsaw puzzle (4) rotation prediction and (5) examplar network: positive: transformed version of original volume (contrast and affine) and negative: different volume from dataset. Training: warm-up training with the encoder parameters fixed and then fine-tuning the entire network.

![Alt text](https://github.com/han-liu/Papers/blob/master/figures/3D%20Self-Supervised%20Methods%20for%20Medical%20Imaging.png?raw=true)

### Comments
- Why semi-supervised methods are not compared in the UDA field? mean teacher?

- why source domain is trained at same time. 

- network architecture not provided. 

- different from another paper's view, this paper trains source and target domain in one model?

- would strong and weak augmentation change the feture centroid for the same class? fix-match

- regularization term : evenly distributed.



