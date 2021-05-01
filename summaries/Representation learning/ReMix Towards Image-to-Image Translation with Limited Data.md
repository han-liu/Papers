[2021-04-10]
- ReMix: Towards Image-to-Image Translation with Limited Data [[pdf]](https://arxiv.org/pdf/2103.16835.pdf) 
- Jie Cao, Luanxuan Hou, Ming-Hsuan Yang, Ran He, Zhenan Sun*
- `2021, CVPR`

****

### Objective
Image translation with limited data

### Proposed Method
This paper is focused on image-to-image translation task. The authors proposed to mix-up features in a linear manner at latent space. A relative form loss is proposed. Specifically, unlike mix-up which interpolates the label linearly, the authors proposed a new loss which (1) forces the content loss (perceptual loss or style reconstruction loss..) between interpolated feature e' and e1 is greater than that between e' and e2, (2) the content loss between e' and feature from any other random image is greater than the previous two losses.

![Alt text](https://github.com/han-liu/Papers/blob/master/figures/ReMix%20Towards%20Image-to-Image%20Translation%20with%20Limited%20Data.png?raw=true)


### Comments
- Strategies, i.e., mix-up, applied to input image and output space can also be applied to feature space. 

- It would be interesting to know if this method is useful for classification task, either in fully-supervised or semi-supervised settings.