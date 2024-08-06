[2022-06-23]
- Universal Segmentation of 33 Anatomies [[pdf]](https://arxiv.org/pdf/2203.02098.pdf) 
- *Pengbo Liu, Yang Deng, Ce Wang, Yuan Hui, Qian Li, Jun Li, Shiwei Luo, Mengke Sun, Quan Quan, Shuxin Yang, You Hao, Honghu Xiao, Chunpeng Zhao, Xinbao Wu, and S. Kevin Zhou*
- `ArXiv`

****

### Objective
Medical image segmentation on partially-annotated datasets

### Paper
#### Motivation
In the context of partially-supervised learning in medical imaging, how can we train a multi-class segmentation model when ROI is not limited? (e.g., not only in abdomin, but the whole vertebrae)

#### Method
Two highlights:

- cross patch transformer:
	- motivation: though transformer can learn long-range dependency, but can only learn within the cropped patch, e.g., 128 x 128 x 128. 
	- To tackle this, the author proposed to feed the network with the upper and lower part of the cropped patch so that global information can be learned, the high-level features obtained by the shared encoder are processed via transformer blocks and further reshaped back for further decoding. 

- To train a 33-class segmentation model, the authors first trained separate models using SOTA methods and use them to produce pseudo labels. [self-training] 

#### Datasets
vertebrae: CTSpine1K (proposed)
others: CTPelvic1K, MSD Liver, MSD Spleen, MSD Pancreas, KiTS, and Abdomen BTCV

#### Compared Methods and Results
separate models:
- nnUNet
- nnFormer
- Marginal exclusive loss
- CPTM (proposed)

Universal model
- CPTM


### Comments
- The authors did not mention the inference speed. During inference, for each patch, if the CPTM needs to take 3 forward passes, the inference speed would be much slower. 
- Pseudo labels are not updated. Maybe some self-training techniques can help further improve this. 
