Thank you for your valuable reviews. Here is our response to your questions and concerns:

**Question 1:** This paper aims to construct a general graph self-supervised framework. However, the problem mentioned in this paper is inherent problem in contrastive learning and it is uncorrelated with graph learning, which makes the motivation unclear.

**Answer:**  The authors have long concentrated on graph machine learning and thus take graphs as the research object in this paper. In this paper, the experimental datasets, data augmentation and backbone networks are closely related to graphs. Indeed, as you said, some of the ideas and concepts in this paper can be transferred to other fields. The extended work to other fields deserves a new research in the future. Thank you for your comments and reminders.

In the past weeks, we have studied the relationship between the decorrelation principle and graph smoothness. The results show that the decorrelation operation has potentially a smoothing effect on node representations, which makes neighborhood nodes more similar in representation space. The relevant content had been added to subsection 3.4 and appendix G. These new studies enhance the connection between our research and graphs, and expand the breadth of the research.



**Question 2:** The solution of the paper are both general in contrastive learning. This paper just find other implementations from existing statistical methods. The proposed decorrelation principle uses two strategies to actualize. The first one is Direct Channel Decorrelation, which looks like a combination of redundancy reduction term in Barlow Twins(inter-view) and covariance regularization term in VICREG(intra-view). In addition, the second one-Spectral Regularization-only makes a few changes on ZCA whitening and is similar to the work of ZERO-CL.

**Answer:**  a) In our paper, we employ various statistical indicators to instantiate the consistency principle. It is not an easy task to embed these indicators into the graph contrastive learning framework and make them work, in which we put a lot of effort. Besides, we evaluated the influence of various indicators on performance, which has certain enlightening and guiding significance.

b) The loss objectives in Barlow Twins and VICReg are biased towards the covariance. Our objective of DCD focuses on utilizing statistical indicators to remove correlations between different channels, and $Cor(\cdot)$ in Eq. (13) can be instantiated to any statistical indicators.

c) Our Spectral Regularization strategy has the same goal as ZCA, namely, removing correlations between different channels. However, the two methods are implemented in completely different ways. ZCA realizes decorrelation through *matrix transformation*, which does not produce gradients and does not change the parameters of the neural networks. Our spectral regularization strategy forces the neural networks to learn decorrelated representations via *loss function*, which can change the parameters of the neural networks.



**Question 3:** Experiments are inadequate. The author should give the comparison with other methods which aims to extracting invariant information from two different views and applying specific strategies to prevent collapsed solutions.

**Answer:**  Thank you for your valuable suggestions. The experiments related to Barlow Twins and VICReg on graph datasets are as follows 

| method             | Cora | Citeseer | Pubmed | Computers | Photo | CS    | Physics |
| ------------------ | ---- | -------- | ------ | --------- | ----- | ----- | ------- |
| Graph VICReg       | 84.2 | 73.1     | 81.6   | 88.74     | 93.14 | 93.31 | 95.38   |
| Graph Barlow Twins | 84.0 | 73.0     | 80.7   | 88.14     | 92.63 | 92.95 | 95.07   |
| Ours               | 84.5 | 73.6     | 81.7   | 88.78     | 93.31 | 93.60 | 95.50   |



The above is our response to your concerns. If you have any other questions, please feel free to tell us. We are glad to discuss and communicate with you.

