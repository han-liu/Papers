##### [2021-04-07]
- Self-Attentive Spatial Adaptive Normalization for Cross-Modality Domain Adaptation [[pdf]](https://arxiv.org/pdf/2103.03781.pdf) 
- *Devavrat Tomar, Manana Lortkipanidze, Guillaume Vray, Behzad Bozorgtabar, Jean-Philippe Thiran*
- `2021, TMI`
- [code](https://github.com/devavratTomar/sasan)

****

### Objective
UDA unpaired image segmentation.

### Proposed Method
The proposed method is one of the image-to-image translation methods for UDA. The pipeline is similar to the SynSeg framewor. The differences are (1) attention module, (2) discriminator for segmentation, (3) SPADE ResNetBlock to combine attention feature maps (4) orthogonal loss to make attention maps avoid redundency.

![alt text](https://github.com/han-liu/Papers/blob/master/figures/Self-Attentive%20Spatial%20Adaptive%20Normalization%20for%20Cross-Modality%20Domain%20Adaptation.png?raw=true)

### Comments
- This paper shows that multi-task, i.e., segmentation and image synthesis, could be beneficial for individual other. 

- The code implementation of formula (1) is different from what was described in the paper.
