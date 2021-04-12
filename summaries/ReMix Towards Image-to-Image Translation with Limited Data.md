[2021-04-10]
- ReMix: Towards Image-to-Image Translation with Limited Data [[pdf]](https://arxiv.org/pdf/2103.16835.pdf) 
- Yulin Wang Xuran Pan, Shiji Song, Hong Zhang, Cheng Wu, Gao Huang*
- `2019, NIPS`
- [code](https://github.com/blackfeather-wang/ISDA-for-Deep-Networks)

****

### Objective
Feature augmentation.

### Proposed Method
The proposed method is a data augmentation technique which aims to augment class-specific feature embedding along semantic directions. The assumption is that different classes may vary differently along different semantic directions, e.g., 'people' may vary a lot along 'wear-glasses' direction but nearly zero variance along the 'have-propeller' direction. Instead of determinstic feature embedding for each input image, ISDA samples the feature vector from a normal distribution with zero mean and intra-class covariance. The sampled feature vector is considered as the augmented feature and could be visualized with the reversing convolutional networks. Besides, the authors demonstrate theoratically that when the number of sampled features approaches infinity, there's an upper bound for the expected CE loss, which can be computed more efficiently. Covariance matrix is computed in an online fashion by aggregating stats from ALL mini-batches. 

![Alt text](https://github.com/han-liu/Papers/blob/master/figures/Implicit%20Semantic%20Data%20Augmentation%20for%20Deep%20Networks.png?raw=true)


### Comments
- I think the motivation and assumption in this paper are strong: different classes may have different variances along each semantic direction. The loss function of the upper bound CE loss was nicely designed. The ISDA method serves as another learnable data (feature) augmentation approach and has not been utilized in medical image domain. It would be interesting to see how it performs in medical image analysis and compared to other learnable data augmentation methods, such as Brainstorm or NVIDIA paper which used data augmentation to improve domain generalization. 

- One common thing I found for the data augmentation papers is that, their experiments usually show that the proposed learnable augmentation technique could outperform the baseline (traditional random rotation and etc), but by incoporating these random data augmentation could further improve the proposed learnable method... For example, in Brainstorm paper and in this paper (in this paper it's actually data + feature augmentation) as well. This suggests that maybe a mixture of learnable and non-learnable augmentation is the best technique for data augmentation..

- ISDA vs VAE. There are some relationships between ISDA and VAE in some aspects.. VAE encodes the inputs to a latent space with a multi-variate normal distribution with zero mean and unit variance, while ISDA encodes to zero mean and class-specific variance. Is ISDA an updated version of VAE? Since VAE is typically used for reconstruction tasks, class information is not well used (maybe can be used in other versions of VAE). ISDA incorporates class-specific information to the co-variance term of the latent feature distribution. 




