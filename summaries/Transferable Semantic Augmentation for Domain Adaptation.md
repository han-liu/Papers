[2021-03-30]
- Transferable Semantic Augmentation for Domain Adaptation [[pdf]](https://arxiv.org/pdf/2103.12562.pdf) 
- *Shuang Li, Mixue Xie, Kaixiong Gong, Chi Harold Liu, Yulin Wang, Wei Li*
- `2021, CVPR`

****

### Objective
Unsupervised domain adaptation (UDA) for classification tasks.

### Proposed Method
The assumption of this paper is that source features can be augmented to effectively equip target semantics to train a more transferrable classifier. The feature centroids are first computed for source and target domains (with pseudo labels). The feature centroid for each class is updated in the same method as [ISDA](https://arxiv.org/pdf/1909.12220.pdf). The difference is that the features used to compute the upper bound of the cross-entropy loss are sampled from N(f_s + Δu, λΣ_t). This aims to gradually adapt source domain feature centroids to target domain feature centroids with the source domain supervision.

![Alt text](https://github.com/han-liu/Papers/blob/master/figures/KD-Net.png?raw=true)


### Comments
- This work seems a direct extension of ISDA to the UDA setting. The proposed method belongs to one of the popular 'prototypical learning' methods: deep features of f_s and f_t. 

- Directly replacing the memory module with the features and pseudo labels in current seems not stable. Would EMA be a better alternative?





