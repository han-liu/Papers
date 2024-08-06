##### [2021-05-25]
- CPM-Nets: Cross partial multi-view networks [[pdf]](https://papers.nips.cc/paper/2019/file/11b9842e0a271ff252c1903e7132cd68-Paper.pdf) 
- *Changqing Zhang, Zongbo Han, Yajie Cui, Huazhu Fu, Joey Tianyi Zhou, Qinghua Hu*
- `2019, NIPS`

****

### Objective
Cross Partial Multi-view learning


### Proposed Method
There are two key points proposed by this paper: 1. completeness and 2. versatility. With partial multi-view data, the author assumed that the complete multi-view representation can be used to reconstruct each view. The complete latent feature is used for final classification. The reconstruction loss is computed for each available views. For versatility, a method similar to prototypical learning is used: when a sample is correctly classified, no loss is computed; when wrongly classified, a loss similar to triplet loss is used to penalize the wrongly classified complete latent feature h to enforce that its similarity to the correct class feature center is higher than those of wrong classes (center was not clearly defined in this paper). During testing, the network is retuned by conducting reconstruction task. 

![Alt text](https://github.com/han-liu/Papers/blob/master/figures/CPM-nets.png?raw=true)

### Comments
- Great idea of forming a complete latent feature and reconstruct back to individual input. This is in contrast to common methods that use multi-inputs to create a common space. This scheme can overcome the limitation of having missing modalities.
