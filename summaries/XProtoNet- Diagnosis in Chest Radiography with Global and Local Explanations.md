[2021-03-31]
- XProtoNet: Diagnosis in Chest Radiography with Global and Local Explanations [[pdf]](https://arxiv.org/pdf/2103.10663.pdf) 
- *Eunji Kim, Siwon Kim, Minji Seo, Sungroh Yoon*
- `2021, CVPR`

****

### Objective
Prototypical learning for chest X-ray classification.

### Proposed Method
The focus of this paper is to use prototypical learning to determine the top K (K=3 in this paper) examples for each thoracic disease. Once we obtain the deep features from the feature module, C x K occurance maps (each is H x W and has a range between 0 and 1) are obtained and used as attention mask for further average pooling. The cosine similarities between K pooled feature vectors and K pre-computed prototypes are further used to produce the final predicted probability. Cluster loss is used to maximize the similarity for positive samples and minimize the similarity for negative samples. 

![Alt text](https://github.com/han-liu/Papers/blob/master/figures/Transferable%20Semantic%20Augmentation%20for%20Domain%20Adaptation.png?raw=true)


### Comments
- This work seems a direct extension of ISDA to the UDA setting. The proposed method belongs to one of the popular 'prototypical learning' methods: deep features of f<sub>s</sub> and f<sub>t</sub>. 

- Directly replacing the memory module with the features and pseudo labels in current seems not stable. Would EMA be a better alternative?





