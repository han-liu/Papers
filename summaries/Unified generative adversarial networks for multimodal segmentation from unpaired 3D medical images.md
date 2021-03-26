##### [2021-03-23]
-  Unified generative adversarial networks for multimodal segmentation from unpaired 3D medical images [[pdf]](https://reader.elsevier.com/reader/sd/pii/S1361841520300955?token=DAF223683D23794B9A440988BDE5B128DEF9EC94CBC4A52F1DA219787873814824DB86A9F0EF83D21F9543CBB9D7471E) 
- *Wenguang Yuan, Jia Wei, Jiabing Wang, Qianli Ma, Tolga Tasdizen*
- `2020, Medical Image Analysis`

****

### Objective
Unpaired multi-modality segmentation


### Proposed Method
The proposed network consists of two stages including (1) modality translation (A->B) and (2) modality recovery (B->A). The modality information is coded by the subtraction of two hot-encoded vectors, e.g., [-1, 1, 0, 0]. For each stage, the sub-network is a Y-shape architecture, i.e., shared encoder and separated decoders for two tasks: (1) segmentation and (2) translation. The results of the translation branch is passed to a discriminator for adverserial training. The last layer (low-level details) of the translation decoder and was then combined to that of the segmentation decoder to obtain the final result. The combination strategy is similar to the squeezed-excitation (SE) block.

### Comments
- I like how this paper interprets the U-net decoding process: 'In the U-Net architecture, the encoders capture multilevel information from low-level textures to high-level semantic knowledge. The decoders first produce the coarse location of target objects and then combine the lower level details from the skip connection and gradually reconstruct the final results'. Ablation study of the effect of the levels of cross-task skip connections is also conducted.  

- Is there a better way to fuse the decoding code, i.e., [-1, 1, 0, 0] and the 3D volume? Direct broadcasting does not seem to be a good strategy.