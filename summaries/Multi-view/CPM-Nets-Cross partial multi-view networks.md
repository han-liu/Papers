##### [2021-05-25]
- CPM-Nets: Cross partial multi-view networks [[pdf]](https://papers.nips.cc/paper/2019/file/11b9842e0a271ff252c1903e7132cd68-Paper.pdf) 
- *Changqing Zhang, Zongbo Han, Yajie Cui, Huazhu Fu, Joey Tianyi Zhou, Qinghua Hu*
- `2019, NIPS`

****

### Objective
Cross Partial Multi-view learning


### Proposed Method


![Alt text](https://github.com/han-liu/Papers/blob/master/figures/Unified%20generative%20adversarial%20networks%20for%20multimodal%20segmentation%20from%20unpaired%203D%20medical%20images.jpg?raw=true)

### Comments
- I like how this paper interprets the U-net decoding process: 'In the U-Net architecture, the encoders capture multilevel information from low-level textures to high-level semantic knowledge. The decoders first produce the coarse location of target objects and then combine the lower level details from the skip connection and gradually reconstruct the final results'. Ablation study of the effect of the levels of cross-task skip connections is also conducted.  

- Is there a better way to fuse the decoding code, i.e., [-1, 1, 0, 0] and the 3D volume? Direct broadcasting does not seem to be a good strategy.