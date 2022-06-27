[2022-06-24]
- Multi-organ Segmentation over Partially Labeled Datasets with Multi-scale Feature Abstraction [[pdf]](https://arxiv.org/pdf/2001.00208.pdf) 
- *Xi Fang, Pingkun Yan*
- `IEEE Transcation of Medical Imaging (TMI) 2020`

****

### Objective
Medical image segmentation on partially-annotated datasets

### Paper

#### Method
The author proposed a new network architecture named PIPO-FAN for image segmentation.
For partial label learning, the authors proposed to use a Target Adaptive Loss (TAL).
The idea is: based on the cross-entropy loss, the voxels will be treated as background (0) if not labeled in the current dataset. 

#### Datasets
LiTs, KiTS, Spleen, and BTCV

#### Compared Methods and Results
Effectiveness of partial label learning: compare different combinations of the datasets.


### Comments
Regarding the proposed network architecture:
- 2.5D networks are used instead of 3D. The proposed architecture did not compare to nnU-Net. 
- For the compared networks such as U-Net, DenseU-Net, and etc, no analysis of the number of model parameters is found. The outperformance of the proposed approach could be simply from the increasing amount of the model parameters, rather than the proposed multi-scale mechanism.

Regarding the partial label learning:
- Personally, the idea of TAL did not seem to be a convincing way to compute the loss for partial label dataset. I would simply backpropagate the channels for the labeled organs and ignore the channels for unlabeled organs. I think the TAL would even cause negative impact because the same model receives different supervision signals for background using different datasets. In the end, what do you expect the model to output for background when each organ has been regarded as background during training?
- Another limitation of this method is that the model is computationally expensive and inflexible (we need to know the total number of classes beforehand) due to its multi-head design. 
- This paper basically demonstrated that by including more dataset for training, the performance could be improved. However, this paper did not compare to other methods for partial label learning. One of the reasons might be that this topic was not very popular back to the 2020s.
