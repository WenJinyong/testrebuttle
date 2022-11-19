Thank you for your helpful feedback and constructive reviews. We will answer your questions as follows:

**Question 1:** The data augmentation is based on dropping edges or feature masking, which plays the effect of merely smoothing the data and thus has limited room to bring improvement. Thus, it is not convincing that the contrastive self-supervised approach can really help the node representation learning significantly.

**Answer:**  Our goal in applying edge dropping and feature masking is to augment the data and obtain various views, aiming to extract common information across different views. Whether the two augmentation strategies indeed play a smoothing effect deserves a new and in-depth study. But intuitively, edge dropping doesn't seem to have a smoothing effect. Concretely, after dropping an edge, the nodes associated with the edge can not perform message aggregation with each other. From this perspective, edge dropping hinders graph smoothing. An extreme example is that all edges are dropped, where message propagation will not occur.



**Question 2:** The performance improvements are marginal. The reviewer is wondering whether the listed baselines are the state-of-the-art. For example, the results of C&S [2] and the referred results are not listed as baselines.

**Answer:** The comparison methods are classic and advanced methods in the field of graph contrastive learning, which have shown very competitive results. Thank you for the recommendation, and we have carefully read the paper you mentioned. C&S gets rid of topological dependence in forward computation, which greatly reduces consumption of time and computing resources while maintaining good performance. We have added C&S to baseline methods for comparison in Table 1 of the main paper.



**Question 3:** The proposed approach is implemented over GCN, which suffers from over-smoothing issue. Could the proposed principles help to resolve the over-smoothing issue, or the over-smoothing issue is deteriorated further?

**Answer:** The over-smoothing phenomenon usually occurs in *deep* graph neural networks [1]. In our study, we adopt one or two layers of GCNs, where there is no over-smoothing issue. Besides, under the homophily assumption, nodes closely connected on a graph tend to have similar labels. Thus, good representations benefit from properly smoothing, which makes neighborhood nodes more similar in representation space [1]. 

Thank you very much for your inspiration. Based on your comments about graph smoothing, we studied the relationship between the decorrelation principle and graph smoothness. The results show that the decorrelation operation has potentially a smoothing effect on node representations, which helps learned representations cluster according to their true potential categories. The relevant content had been added to subsection 3.4 and appendix G. From this perspective, the decorrelation principle plays a similar role as the smoothing step of C&S. 

We can draw a new conclusion about the role of the decorrelation principle: 1) decoupling various representation channels and facilitating informative representations; 2) smoothing node representations and making neighborhood nodes more similar in representation space.

We really appreciate your comments and inspirations, which greatly enriches our research content and extent the research depth.



**Question 4:** In page 6, a "Proposition 1" is given but there is no proof. It is unusual that a proposition is given without a proof. A statement without proof is nothing but a conjecture. On contrary, Lemma 1 is a basic fact in standard textbook of multivariable statistics analysis. No need to emphisize it as a lemma.

**Answer:** For Proposition 1, we have empirically demonstrated its correctness through the experiments in subsection 4.4, Appendix H (Appendix I of the revised version), and Appendix I (Appendix J of the revised version). A lot of empirical research is also a support, so we would not change the title of Proposition 1. Thank you for your reminder, we have changed the title of "Lemma 1" to "Property 1". Specific statements and related proof of Property 1 are still retained for the convenience of those who may not be familiar with it.



[1] Deeper insights into graph convolutional networks for semi-supervised learning. AAAI 2018.

[2] Combining label propagation and simple models out-performs graph neural networks. ICLR, 2021.



The above is our response to your suggestions and feedback. If you have any other questions or suggestions, please feel free to tell us. Thank you again for your constructive comments.

