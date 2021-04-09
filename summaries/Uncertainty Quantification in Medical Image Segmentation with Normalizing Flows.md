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

![alt text](https://github.com/han-liu/Papers/blob/master/figures/Uncertainty%20Quantification%20in%20Medical%20Image%20Segmentation%20with%20Normalizing%20Flows.png?raw=true)

### Comments
- The proposed method did not compare with the updated versions of Prob U-nets, even though these methods were mentioned in the related work section... In the experiment, only deterministic U-net and Prob U-net are compared.

- Since the latent vector is sampled from VAE first, would the Gaussian mean feature vector the most likely prediction, i.e., the one with highest Dice score? If so, why do we need other less likely predictions? Besides, methods like this such as Prob U-net or Stochastic Segmentation Network usually were only evaluated using metrics like GED. These methods did not really assess the qualities of the uncertainty maps. It should be made more clear why we need these methods if (1) they did not provide better segmentation results in terms of Dice and (2) the quality of uncertainty maps are not shown to be more effective than MC Dropout or model ensemble.
