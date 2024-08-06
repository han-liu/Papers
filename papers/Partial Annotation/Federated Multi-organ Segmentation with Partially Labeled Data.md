[2022-06-27]
- Federated Multi-organ Segmentation with Partially Labeled Data [[pdf]](https://arxiv.org/pdf/2206.07156.pdf) 
- *Xuanang Xu, Pingkun Yan*
- `ArXiv`

****

### Objective
Medical image segmentation on partially-annotated datasets in federated learning

### Paper

#### Method
Regarding the partial label learning, the authors proposed to train a network with different organ-specific sub-encoder and a shared decoder. Another light-weight auxillary generic decoder (AGD) is used for an auxillary task to make 'the feature learned from each sub-encoder more distinct'. Training loss consists of two parts: (1) marginal loss and exclusion loss for the multi-class segmentation model, and (2) auxillary loss (dice/ce/dicece) by the output obtained by AGD for each organ. 

#### Datasets
BTCV, decathlon pancreas, LiTs, KiTs

#### Compared Methods and Results
- Localized learning (training from each individual dataset)
- Centralized learning (typical partial label learning where data can be collected together)
- Federated learning (partial label learning where data from each site cannot be shared)

- Ablation studies on AGD


### Comments
- The novelty of this method seems quite limited. The design of organ-specific sub-encoders is not practical because there will be memory issues (the number of model parameters are not discussed) if the number of organs increases. Would it be possible to use DoDNet-like network to replace the multiple sub-encoders? Though the sub-encoders are supposed to produce organ-specific features, they should also share some low-level features as these organs are within the same ROI (recap that DoDNet has a shared network for all organs but only different output layers to control the desired organs). 

- The experimental results show that centralized learning did not outperform the the localized learning and federated learning. I find this result very surprising because theoratically, the centralized learning has fewer restrictions than federated learning, and as mentioned by the authors, it should serve as an upper bound. The authors argued that 'We attribute this phenomenon to the fact that the mixture of the partially labeled data could confuse the deep models during training, if the expertise of different ROIs is not well-decomposed. This result can also serve as an endorsement of our method that the organ-specific feature learning is necessary for the FL model when dealing with the partial labels'. 
