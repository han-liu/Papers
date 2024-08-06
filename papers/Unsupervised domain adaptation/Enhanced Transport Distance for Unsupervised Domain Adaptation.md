[2021-04-02]
- Enhanced Transport Distance for Unsupervised Domain Adaptation [[pdf]](https://openaccess.thecvf.com/content_CVPR_2020/papers/Li_Enhanced_Transport_Distance_for_Unsupervised_Domain_Adaptation_CVPR_2020_paper.pdf) 
- *Mengxue Li, Yi-Ming Zhai, You-Wei Luo, Peng-Fei Ge, Chuan-Xian Ren*
- `2020, CVPR`
- [code](https://github.com/LavieLuo/ETD)

****

### Objective
UDA

### Proposed Method
Optimal transport (OT) model is used in domain adaptation for distribution matching. Two limitations of previous OT methods include (1) mini-batch training cannot fully reflect the true distribution of source and target domain and (2) label information and latent structure of the target domain are usually ignored. A shared feature extractor was used for both source and target domain. The distance matrix of source and target domain samples are re-weighted according to the classification prediction from two domains. This step is supposed to adjust the mini-batch distribution to the real distribution. However, I have not fully understood the Kantorovich potential (KP) section... I believe the KP serves as a regularization for domain adaptation. The final loss includes (1) CE loss in source domain (2) entropy of target domain and (3) KP loss. 


![Alt text](https://github.com/han-liu/Papers/blob/master/figures/Enhanced%20Transport%20Distance%20for%20Unsupervised%20Domain%20Adaptation.png?raw=true)


### Comments
- There seems to be a relationship between this paper and the TSA paper: in TSA, target domain features are constructed by f<sub>s</sub> + mean difference between two domains; in this work, the source domain feature was estimated by the f<sub>t</sub> - distance. 

- Based on the recent 2021 CVPR UDA papers, it can be observed that (1) most of these UDA methods are pseudo-label based methods (self-training); recent UDA methods rarely create pseudo images (cycle-GAN variants). This is probabily because such methods were well explored in the past few years. (2) Under the self-training framework, the loss functions usually includes CE/BCE, etc losses for BOTH source and target domains + some regularization losses.



