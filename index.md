---
layout: project_page
permalink: /

title: SeFi-IDE Semantic-Fidelity Identity Embedding for Personalized Diffusion-Based Generation
Paper: https://Com-Vis.github.io/SeFi-IDE/
---

<div class="columns is-centered has-text-centered">
    <div class="column is-four-fifths">
        <h2>Abstract</h2>
        <div class="content has-text-justified">
The advanced diffusion-based Text-to-Image (T2I) models (e.g., Stable Diffusion Model) have made significant progress in generating diverse and high-quality images using only text prompts. However, when the non-famous users further require these T2I models to generate person-specific images, T2I models are unable to handle the accurate identity (ID) mapping. The essential problem is that the ID-image alignments of these new users are not learnt by existing T2I models. The previous methods either failed to accurately fit the face region or lost the interactive generative ability with other existing concepts in T2I models (i.e., unable to generate other concepts described in given prompts such as scenes, actions, and facial attributes). In this paper, we focus on accurate and semantic-fidelity ID embedding into the Stable Diffusion Model for personalized generation. We tackle this challenge from two perspectives: face-wise region fitting, and semantic-fidelity token optimization. Specifically, we first visualize the attention overfit problem, and propose a face-wise attention loss to fit the face region instead of the whole target image. This key trick can improve the ID accuracy and interactive generative ability with other existing concepts. Then, we optimize one ID representation as several per-stage tokens and each token consists of two disentangled features, which expands the textual conditioning space with semantic-fidelity control ability. Extensive experiments validate that our results have better ID accuracy and manipulation ability than previous methods.
        </div>
    </div>
</div>

---

## <center> Framework
![](/static/image/teaser.png)
The face identity (ID) embedding of previous personalized generation methods has two problems: (1) Attention Overfit : The attention of Textural Inversion and ProSpect} towards to the V* takes over the whole image, disrupting the interaction between newly embedded concepts and other existing concepts. Consequently, their attention towards to the cup is wrong, which results in the failure of the given prompt. (2) Limited Semantic-Fidelity: Despite alleviating overfit, Celeb Basis introduces excessive face prior, limiting the semantic-fidelity of the learned ID embedding. Specifically, this means that the cup attention map continues to concentrate on the face region. We propose Face-Wise Attention Loss and Semantic-Fidelity Token Optimization to address problem (1) and (2) respectively.
![](/static/image/pipeline.png)
The overview of our framework. We first propose a novel Face-Wise Attention Loss to alleviate the attention overfit problem and make the ID embedding focus on the face region to improve the ID accuracy and interactive generative ability. Then, we optimize the target ID embedding as five per-stage tokens with disentangled features to expend textural conditioning space with semantic-fidelity control ability.
---

## <center> Single Person's Generation

### <center> Single Person's Comparisons
![](/static/image/figure3.png)
![](/static/image/com_single_person.png)

### <center> More Single Person's Generation Results
![](/static/image/figure4.png)

---
## <center> Multiple Persons' Generation
### <center> Multiple Persons' Comparisons
![](/static/image/multi_scen.png)
![](/static/image/action.png)

### <center> More Multiple Persons' Gneration Results
![](/static/image/multi_person.png)

## More Evaluation
Our method does not introduce face prior from other models, we adopt bear, cat, and dog for experiments, which show the generalization ability of our method.
![](/static/image/more_objects.png)


