[2022-07-07]
- DoDNet: Learning to segment multi-organ and tumors from multiple partially labeled datasets [[pdf]](https://arxiv.org/pdf/2011.10217.pdf) 
- *Jianpeng Zhang, Yutong Xie, Yong Xia, and Chunhua Shen*
- `CVPR 2021`

****

### Objective
Medical image segmentation on partially-annotated datasets

### Paper
#### Motivation
Introduce a single-path network to train on multiple partially labeled datasets

#### Method
DoDNet is a single-path network (U-Net) with dynamic head at the output level. The high-level feature from the bottleneck of U-Net, and a given one-hot task code, are concatenated and used to dynamically generate the filter weights in the last three convolutional (output) layers (kernels of 1x1). This is used as a controller to control which organ will be focused on. In this way, this single-path network can be fed with partially labeled dataset. During the inference, the feature maps are firstly generated. Then based on the desired organ of interest, final prediction can be predicted by using dynamic head at the generated feature map. Thus, making inference does not require long processing time.

#### Datasets
BTCV, MOTS

#### Compared Methods and Results
- individual networks for each organ (large storage and are trained with limited data)
- Multi-head network - TAL
- Multi-head network - Med3D
- cond-input: Fast image pro- cessing with fully-convolutional networks
- cond-decod: Learning multi- class segmentations from single-class datasets

- BTCV validation set (20 vols) after fine-tuning
	- PaNN
	- nnUNet
	- TFS
	- DLTK
	- AutoContext

### Comments
- One of my favoriate papers so far! Very inspiring.

Thinking:
- The design of task code
	-	Currently, the task code is designed as one-hot encoding vector. I'm not sure if other designs were tried by the authors. One-hot encoding makes sense, but may be limited when adding new organs to the existing network. This would be a very interesting future of this research: incremental/continue learning on DoDNet. If so, can the code just be like 000, 001, 002, ... 999, etc? In so, we can encode up to 999 classes using 3 digits task code. However, this design may also not ideal because 000 is very close to 001; 995 is very close to 996. 

- Fine-tuning
	- I notice that the fine-tuning only applies to the same ROI: both pre-trained and down-stream task are abdominal CTs. It would be interesting to expand it to whole body CT because CTs should share some low-level features.




