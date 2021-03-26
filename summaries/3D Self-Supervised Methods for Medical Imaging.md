##### [2021-03-26]
- 3D Self-Supervised Methods for Medical Imaging [[pdf]](https://arxiv.org/pdf/2006.03829.pdf) 
- *Aiham Taleb, Winfried Loetzsch, Noel Danz, Julius Severin, Thomas Gaertner, Benjamin Bergner, and Christoph Lippert*
- `2020, NIPS`

****

### Objective
Self-supervised learning (SSL) for 3D medical image analysis

### Proposed Method
The authors designed 5 pre-text tasks for pre-training and initialize the downstream's encoder with the pre-trained weights.
Five tasks are (1) constrastive predicting code (CPC): encoder to generate latent vector and context network to produce context vector; infoNCE loss is used to compute the similarity of positive/negative pairs (2) relative patch location (3) Jigsaw puzzle (4) rotation prediction and (5) examplar network: positive: transformed version of original volume (contrast and affine) and negative: different volume from dataset. Training: warm-up training with the encoder parameters fixed and then fine-tuning the entire network.

![Alt text](https://d3i71xaburhd42.cloudfront.net/11bdffb5d46e8510626384db9ae7420f4a88d981/4-Figure1-1.png)

### Comments
- This results show that when we have very limited data, SSL can help improve the performance by a large margin. When we have sufficient amount of data, SSL shows similar performance compared to baseline. However, since we do not know whether the amount of available data is sufficient for different applications, maybe we should always try SSL to check if the performance can be boosted.

- Regarding the experiments, there were no experiments to combine or compare the proposed 5 methods. Besides, it did not compare against other SSL methods, e.g., model genesis.

- The 5th SSL method: 3D-exe seems to be a classifier to differentiate affine and non-affine transformations.

- Would it be possible to develop specific SSL method for specific downstream tasks, e.g., segmentation, registration?
