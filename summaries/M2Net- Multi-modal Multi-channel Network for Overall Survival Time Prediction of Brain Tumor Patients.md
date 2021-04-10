##### [2021-04-09]
- M2Net: Multi-modal Multi-channel Network for Overall Survival Time Prediction of Brain Tumor Patients [[pdf]](https://arxiv.org/pdf/2006.10135.pdf) 
- *Tao Zhou, Huazhu Fu, Yu Zhang, Changqing Zhang, Xiankai Lu, Jianbing Shen, and Ling Shao*
- `2020, MICCAI`

****

### Objective
Overall survival (OS) prediction (3-class classification) with multi-modality dataset (Brats 2018) 

### Proposed Method


![alt text]()

### Comments
- The proposed method did not compare with the updated versions of Prob U-nets, even though these methods were mentioned in the related work section... In the experiment, only deterministic U-net and Prob U-net are compared.

- Since the latent vector is sampled from VAE first, would the Gaussian mean feature vector the most likely prediction, i.e., the one with highest Dice score? If so, why do we need other less likely predictions? Besides, methods like this such as Prob U-net or Stochastic Segmentation Network usually were only evaluated using metrics like GED. These methods did not really assess the qualities of the uncertainty maps. It should be made more clear why we need these methods if (1) they did not provide better segmentation results in terms of Dice and (2) the quality of uncertainty maps are not shown to be more effective than MC Dropout or model ensemble.
