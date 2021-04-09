##### [2021-04-08]
- Uncertainty Quantification in Medical Image Segmentation with Normalizing Flows [[pdf]](https://arxiv.org/pdf/2006.02683.pdf) 
- *Raghavendra Selvan, Frederik Faye, Jon Middleton, Akshay Pai*
- `2020, MICCAI`
- [code](https://github.com/raghavian/cFlow)

****

### Objective
Stochastic segmentation outputs using normalizing flows (NF)

### Proposed Method
The proposed method is exactly the same as the Probabilistic U-net, except that (1) cFlow further processes the latent feature sampled from VAE with normalizing flows and (2) a context vector as condition. The loss function consists of two parts: (1) NF loss and (2) KL divergence between latent features from prior nets and posterior nets. 

![alt text](https://github.com/han-liu/Papers/blob/master/figures/Self-Attentive%20Spatial%20Adaptive%20Normalization%20for%20Cross-Modality%20Domain%20Adaptation.png?raw=true)

### Comments
- This paper shows that multi-task, i.e., segmentation and image synthesis, could be beneficial for individual other. 

- The code implementation of formula (1) is different from what was described in the paper.
