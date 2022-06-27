[2022-06-26]
- Prior-aware Neural Network for Partially-Supervised Multi-Organ Segmentation [[pdf]](https://openaccess.thecvf.com/content_ICCV_2019/papers/Zhou_Prior-Aware_Neural_Network_for_Partially-Supervised_Multi-Organ_Segmentation_ICCV_2019_paper.pdf) 
- *Yuyin Zhou, Zhe Li, Song Bai, Chong Wang, Xinlei Chen, Mei Han, Elliot Fishman, Alan L. Yuille*
- `ICCV 2019`

****

### Objective
Medical image segmentation on partially-annotated datasets

### Paper
#### Motivation
How to incoporate anatomical prior in partial label learning

#### Method
This method requires both full-annotation dataset and partially-labeled datasets. The assumption held by this work is that, different organs should have similar organ size distribution across different subjects. 

The authors proposed a prior-aware loss: based on the full-annotation dataset, train a model in a supervised manner. For each voxel, compute the prior distribution q. Then the same segmentation model was trained using pseudo labels repeatedly (self-training scheme).

#### Datasets
BTCV, decathlon liver, spleen, pancreas

#### Compared Methods and Results
- supervised without partial label dataset
- semi-supervised approach: treating partial label as unlabeled data
- partial label learning: PaNN without prior-aware loss
- labeled + partial label learning: PaNN

- other methods on the BTCV leaderboard. PaNN won the 1st place at the time, w/ or w/o the additional partial label dataset.


### Comments
- It is very interesting to incoporate anatomical prior in this application: organ segmentation in CT images. Indeed, I believe that all the segmentation algorithms for organs should consider this to improve the model robustness. In this paper, the organ size distribution was considered as the anatomical prior. 
- It would be interesting to explore if we can add the spatial relationship among organs (positional embedding in transformer) or some other anatomical priors (maybe different organs have different levels of regularizations: vessel vs liver).
- The major limitation of this method, as has been mentioned in other PSL papers, is that the prior distribution needs to be calculated using fully-annotated dataset, which may not be available.
