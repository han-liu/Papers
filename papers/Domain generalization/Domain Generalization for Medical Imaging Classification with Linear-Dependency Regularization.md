[2021-05-27]
- Domain Generalization for Medical Imaging Classification with Linear-Dependency Regularization [[pdf]](https://arxiv.org/pdf/2009.12829.pdf) 
- *Haoliang Li, YuFei Wang, Renjie Wan, Shiqi Wang, Tie-Qiang Li, Alex C. Kot*
- `2020, NIPS`
- [code](https://github.com/wyf0912/LDDG)

****

### Objective
domain generalization

### Proposed Method
The authors assumed that there is a linear dependency on the latent space, i.e., there is a dominant eigenvalue for category information. After obtaining the latent features, a rank loss is used to regularize the rank(z)=C. Different from previous methods, low-rank regularization is used on latent space rather than on classifier parameters. A KL loss (similar to VAE) is used to match latent features from different domains to a pre-defined prior. The total loss includes (1) classification CE loss (2) rank loss and (3) KL loss.

### Comments
- Idea is similar to ISDA regarding the linear assumption at latent space. ISDA assumes that different classes have different variances. `Can we use ISDA for domain generalization by replacing the 'class' to 'domain'?`
- It is not clear why probablistic U-net is compared in the experiment. This network is designed for domain generalization tasks.


