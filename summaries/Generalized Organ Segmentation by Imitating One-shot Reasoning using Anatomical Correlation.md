[2021-04-20]
- Generalized Organ Segmentation by Imitating One-shot Reasoning using Anatomical Correlation [[pdf]](https://arxiv.org/abs/2103.16344) 
- *Hong-Yu Zhou, Hualuo Liu, Shilei Cao, Dong Wei, Chixiang Lu, Yizhou Yu, Kai Ma, Yefeng Zheng*
- `2021 IPMI`
- code unavailable.

****

### Objective
Deep learning version of statistical shape model (implicitly).

### Proposed Method
A mean shape distance field is computed first. The fixed image and the mean shape distance is fed to an encoder to generate (1) affine transformed mean shape (2) latent vector z for deformable transformation. The 3D coordinates and the latent feature z are fed to a MLP to predict the SDF value. During the training, the MLP is firstly trained by optimizing both the weights in MLP and the latent variable z. In this way, we can generate latent feature z for each image in the dataset and compute their mean feature vector. Then the weights in the MLP are fixed and the whole pipeline is optmized to learn a good lambda. During inference, only top 28 PCA components are used (72% variance). 

![Alt text](https://github.com/han-liu/Papers/blob/master/figures/Deep%20Implicit%20Statistical%20Shape%20Models%20for%203D%20Medical%20Image%20Delineation.png?raw=true)


### Comments
- Very interesting paper to read overall!
- Would this method work well for the unhealthy cases? For example, when there is tumor inside the liver or part of the liver is removed, would this method still generate the liver mask with or without tumor? Based on figure 6 row 3, I would expect the ground truth not to include the abnormalty but the proposed method seems to still generate the whole liver mask? Would this be a limitation of this method?
- Using DRL to obtain affine transformation parameters seems not very elegant here. Would an affine network be enough to solve this problem?
- The PCA part seems very similar to the mechanism of VAE. The main difference is that, the latent space is learned automatically in VAE while in this paper the mean is computed explicitly. The formula mu + W\*lambda can be considered as the reparametrization step in VAE.
- The whole pipeline is similar to a joint affine and deformable registration network. I thought for organs with strong anatomical priors, registration-based methods (like this paper) should always outperform pure AE models. Even though the dice scores are not improved significantly, at least the robustness can be guaranteed. It would be interesting to explore why registration-based methods are not widely used in these cases. 
