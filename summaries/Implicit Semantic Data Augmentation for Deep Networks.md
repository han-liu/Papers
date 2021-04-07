[2021-04-05]
- Implicit Semantic Data Augmentation for Deep Networks [[pdf]](https://arxiv.org/pdf/1909.12220.pdf) 
- Yulin Wang Xuran Pan, Shiji Song, Hong Zhang, Cheng Wu, Gao Huang*
- `2019, NIPS`
- [code](https://github.com/blackfeather-wang/ISDA-for-Deep-Networks)

****

### Objective
Data augmentation in feature space.

### Proposed Method
The proposed method is a data augmentation technique which aims to augment class-specific feature embedding along semantic directions. The assumption is that different classes may vary differently along different semantic directions, e.g., 'people' may vary a lot along 'wear-glasses' direction but nearly zero variance along the 'have-propeller' direction. Instead of determinstic feature embedding for each input image, ISDA samples the feature vector from a normal distribution with zero mean and intra-class covariance. The sampled feature vector is considered as the augmented feature and could be visualized with the reversing convolutional networks. Besides, the authors demonstrate theoratically that when the number of sampled features approaches infinity, there's an upper bound for the expected CE loss, which can be computed more efficiently. Covariance matrix is computed in an online fashion by aggregating stats from ALL mini-batches. 

![Alt text](https://github.com/han-liu/Papers/blob/master/figures/Prototypical%20Networks%20for%20Few-shot%20Learning.png?raw=true)


### Comments
- I think the motivation and assumption in this paper are strong: different classes may have different variance along each semantic direction. 

- ISDA vs VAE. 




