##### [19-01-25] [paper33]
-  Unified generative adversarial networks for multimodal segmentation from unpaired 3D medical images [[pdf]](https://reader.elsevier.com/reader/sd/pii/S1361841520300955?token=DAF223683D23794B9A440988BDE5B128DEF9EC94CBC4A52F1DA219787873814824DB86A9F0EF83D21F9543CBB9D7471E) 
- *Wenguang Yuan, Jia Wei, Jiabing Wang, Qianli Ma, Tolga Tasdizen*
- `2020, Medical Image Analysis`

****

### General comments on paper quality:
- Well-written and very interesting paper. After reading the papers on [SGLD](https://www.ics.uci.edu/~welling/publications/papers/stoclangevin_v6.pdf) and [SGHMC](https://arxiv.org/abs/1402.4102), this paper ties the theory together and provides a general framework for SG-MCMC.

### Paper overview:
- The authors present a general framework and recipe for constructing MCMC and SG-MCMC samplers based on continuous Markov processes. The framework entails specifying a stochastic differential equation (SDE) by two matrices, D(z) (positive semi-definite) and Q(z) (skew-symmetric). Here, z = (theta, r), where theta are the model parameters and r are auxiliary variables (r corresponds to the momentum variables in Hamiltonian MC).
