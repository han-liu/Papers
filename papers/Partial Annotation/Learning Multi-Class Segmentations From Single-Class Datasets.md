[2022-07-10]
- Learning Multi-Class Segmentations From Single-Class Datasets [[pdf]](https://openaccess.thecvf.com/content_CVPR_2019/papers/Dmitriev_Learning_Multi-Class_Segmentations_From_Single-Class_Datasets_CVPR_2019_paper.pdf) 
- *Konstantin Dmitriev and Arie E. Kaufman*
- `CVPR 2019`

****

### Objective
Medical image segmentation on partially-annotated datasets （single class dataset）

### Paper
#### Motivation
Introduce a conditional convolutional network for segmentation

#### Method
The authors proposed a single convolutional network which is conditioned on the segmentation task. The task is passed to a hash function and returns a tensor with all values set to the hash(task label). This is concatenated to the intermediate layers as additional information to produce task-specific segmentation outputs. 

#### Datasets
Sliver, NIH Pancreas, private dataset, Cityscapes

#### Compared Methods and Results
- some supervised methods for individual organs
- ablations of removing conditions.

### Comments
- I believe this is one of the papers that inspires the DoDNet paper. Especially from the experiments, we can see that cond-dec performs the best, suggesting that we should use the same feature extractor but different layers (dynamic head) to output different organs. 
- Adding hash function seems an explicit way of adding attention to the network. 




