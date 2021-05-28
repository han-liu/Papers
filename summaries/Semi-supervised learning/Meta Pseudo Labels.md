[2021-05-27]
- Meta Pseudo Labels [[pdf]](https://arxiv.org/pdf/2003.10580.pdf) 
- *Hieu Pham, Zihang Dai, Qizhe Xie, Minh-Thang Luong, Quoc V. Le*
- `2021, CVPR`
- [code](https://github.com/google-research/google-research/tree/master/meta_pseudo_labels)

****

### Objective
Semi-supervised learning for classification tasks.

### Proposed Method
The proposed method aims to address the issue of traditional pseudo label method, comfirmation bias: pseudo labels are never updated. In each batch, we have both labeled image and unlabeled image. Teacher model is a model pre-trained on labeled dataset. (1) An unlabeled image is fed to both teacher and student models. The consistency loss (CE) is used to update the `student` weights. (2) based on the student loss, compute the teacher feedback coefficient. Compute teacher gradient from student feedback: coefficient * CE loss (teacher-one-hot, teacher-soft) (3) teacher graident update using labeled data (CE) (4) update teacher gradient using UDA loss (one original and one augmented by RandAug).


![Alt text](https://github.com/han-liu/Papers/blob/master/figures/Implicit%20Semantic%20Data%20Augmentation%20for%20Deep%20Networks.png?raw=true)

![Alt text](https://github.com/han-liu/Papers/blob/master/figures/Implicit%20Semantic%20Data%20Augmentation%20for%20Deep%20Networks.png?raw=true)


### Comments
- It is not clear how the weights of student model are initialized. In this paper, it was only mentioned that 'In our experiments, our teacher and our student share the same architecture but have independent weights.'

- In appendix D, figure 3, it is observed that UDA along outperformed supervised + MPL by a large margin. Even though the performance of UDA could be further improved using MPL, this makes the effectiveness of MPL unclear. 

- If the proposed method: dynamic teacher + student is really good, why do we need to fine-tune the student model on labeled data after using supervised + MPL training, where the labeled data has been used already?




