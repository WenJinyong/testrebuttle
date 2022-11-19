Thank you for your careful reading and constructive comments. We will answer your questions as follows:

**Question 1:** In DCD, the *inter-view* minimum correlation seems not well-motivated. Could the authors provide more discussions to clarify the necessity of the inter-view term? Will the dimensionality collapse still occur provided that the inter-view part is ignored?

**Answer:**  In fact, in DCD, either intra-view minimum correlation or inter-view minimum correlation has the ability to prevent dimensional collapse. The joint participation of the two items can better guarantee the effect of decorrelation. The relevant ablation studies are as follows:

a) adopting matrix correlation to instantiate the consistency principle:

| variants        | Cora           | Citeseer        | Pubmed         | Computers        | Photo            | Cs               | Physics          |
| --------------- | -------------- | --------------- | -------------- | ---------------- | ---------------- | ---------------- | ---------------- |
| both            | 84.5 $\pm$ 0.3 | 73.6  $\pm$ 0.3 | 81.7 $\pm$ 0.3 | 88.70 $\pm$ 0.31 | 93.14 $\pm$ 0.15 | 93.60 $\pm$ 0.08 | 95.42 $\pm$ 0.12 |
| only intra-view | 84.2 $\pm$ 0.3 | 73.2  $\pm$ 0.4 | 81.4 $\pm$ 0.3 | 88.45 $\pm$ 0.28 | 93.02 $\pm$ 0.13 | 93.36 $\pm$ 0.10 | 95.27 $\pm$ 0.14 |
| only inter-view | 84.0 $\pm$ 0.3 | 73.0  $\pm$ 0.3 | 80.9 $\pm$ 0.2 | 88.40 $\pm$ 0.34 | 93.05 $\pm$ 0.13 | 93.30 $\pm$ 0.09 | 95.24 $\pm$ 0.11 |

b) adopting distance correlation to instantiate the consistency principle:

| variants        | Cora          | Citeseer        | Pubmed         | Computers        | Photo            | Cs               | Physics          |
| --------------- | ------------- | --------------- | -------------- | ---------------- | ---------------- | ---------------- | ---------------- |
| both            | 83.2 \pm$ 0.5 | 72.6  $\pm$ 0.3 | 79.1 $\pm$ 0.6 | 88.41 $\pm$ 0.32 | 93.02 $\pm$ 0.15 | 93.58 $\pm$ 0.13 | 95.34 $\pm$ 0.09 |
| only intra-view | 82.8 \pm$ 0.4 | 72.4  $\pm$ 0.4 | 78.7 $\pm$ 0.6 | 88.22 $\pm$ 0.35 | 92.92 $\pm$ 0.13 | 93.34 $\pm$ 0.15 | 95.26 $\pm$ 0.08 |
| only inter-view | 82.7 \pm$ 0.6 | 72.3  $\pm$ 0.3 | 78.5 $\pm$ 0.5 | 88.18 $\pm$ 0.29 | 92.94 $\pm$ 0.18 | 93.26 $\pm$ 0.12 | 95.25 $\pm$ 0.08 |

From the above tables, we can know that a competitive result can be obtained by applying either the inter-view term or the intra-view term. The combination of two items enhances performance.

Besides, the correlation matrices under a solo *inter-view* or *intra-view* constraint are added to the Figure 14 of the revised version. The results show that any one has an ability to decouple various representation channels.

**Question 2:** I'm curious about the details of sampling $\tau$ from $\mathcal{T}$. Specifically, how did the authors construct $\mathcal{T}$ in experiments? I have read Append M, $p_e$ and $p_f$ seem to be set as constants (from the context and Figures 14-15). However, in both Alg. 7 and descriptions in the main paper, \tau_A$ and \tau_B$ are re-sampled in each (outer-)iteration. If |$\mathcal{T}$|=2, the related claim is inadequate.

**Answer:**  Each combination of the determined values of $p_f$ and $p_e$ constructs a function space $\mathcal{T}$. In the function space $\mathcal{T}$, all functions for data augmentation have a common property: they are consistent in the number of dropped edges and the number of masked feature channels. But various augmentation functions in the space $\mathcal{T}$ have different operation objects. In other words, the positions of dropped edges and  the indices of masked feature channels are different for various functions in  $\mathcal{T}$. 

We take a more specific example to describe it more intuitively. Assuming the number of edges is $|\mathcal{E}|$ and the number of feature channels is $D$, given $p_f=0.2$ and $p_e=0.4$, a function space $\mathcal{T}$ is constructed. Each function $tau$ in $\mathcal{T}$ drops $p_e * |\mathcal{E}|$ edges and masks $p_f * D$ channels. However, various functions, such as $\tau_A$, $\tau_B$ and $\tau_C$, have their own operation objects. 

The concrete implementation is provided in the anonymous link https://github.com/ICLR2023-ID3781/ICLR2023ID3781/blob/main/aug.py , which is also offered in Page 10 of the paper. $p_f$ is the "mask_prob" of function mask_feature(feature, mask_prob), and $p_f$ is the "mask_prob" of function mask_edge(graph, mask_prob).

For each dataset, we fix $p_e$ and $p_f$, which determines the function space $\mathcal{T}$. Thus, the numbers of dropped edges and masked channels are determinate. We resample $\tau_A$ and $\tau_B$ in each iteration to decide which edges and feature channels to drop and mask. This operation makes augmented views different in various iterations, which helps to extract perturbation-invariant information.



**Question 3:** The introduction seems to focus on general contrastive learning while the topic of this paper is graph contrastive learning. The core of Introduction should be the main limitation of *graph* contrastive learning. More importantly, most discussions in Section 3 are independent of *graph*. It seems to limit the novelty and contributions of this paper to some extent.

**Answer:**  The authors have long concentrated on graph machine learning and thus take graphs as the research object in this paper. In this paper, the experimental datasets, data augmentation and backbone networks are closely related to graphs. Indeed, as the reviewer says, some of the ideas and concepts in this paper can be transferred to other fields. The extension work deserves a new and in-depth research in the future. We really appreciate your comments and reminders.

In the past weeks, we have studied the relationship between the decorrelation principle and graph smoothness. The results show that the decorrelation operation has potentially a smoothing effect on node representations, which makes neighborhood nodes more similar in representation space. The relevant content had been added to subsection 3.4 and appendix G. These new studies strengthen the relationship between our research and graphs, and expand the depth of the research.



We have tried our best to answer your questions carefully and improved our paper according to your comments. Your feedback is very important to us, and we look forward to further discussion and communication with you. Thank you for your careful comments again!

