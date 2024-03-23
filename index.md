---
layout: project_page
permalink: /

title: Beyond Inserting: Learning Identity Embedding for Semantic-Fidelity Personalized Diffusion Generation
Paper: https://Com-Vis.github.io/SeFi-IDE/
---

<div class="columns is-centered has-text-centered">
    <div class="column is-four-fifths">
        <h2>Abstract</h2>
        <div class="content has-text-justified">
Advanced diffusion-based Text-to-Image (T2I) models, such as the Stable Diffusion Model, have made significant progress in generating diverse and high-quality images using text prompts alone. However, when non-famous users require personalized image generation for their identities (IDs), the T2I models fail to accurately generate their ID-related images. The main problem is that pre-trained T2I models do not learn the mapping between the new ID prompts and their corresponding visual content. The previous methods either failed to accurately fit the face region or lost the interactive generative ability with other existing concepts in T2I models. In other words, they are unable to generate T2I-aligned and semantic-fidelity images for the given prompts with other concepts such as scenes (``Eiffel Tower''), actions (``holding a basketball''), and facial attributes (``eyes closed''). In this paper, we focus on inserting accurate and interactive ID embedding into the Stable Diffusion Model for semantic-fidelity personalized generation. We address this challenge from two perspectives: face-wise region fitting and semantic-fidelity token optimization. Specifically, we first visualize the attention overfit problem and propose a face-wise attention loss to fit the face region instead of entangling ID-unrelated information, such as face layout and background. This key trick significantly enhances the ID accuracy and interactive generative ability with other existing concepts. Then, we optimize one ID representation as multiple per-stage tokens where each token contains two disentangled features. This expansion of the textual conditioning space improves semantic-fidelity control. Extensive experiments validate that our results exhibit superior ID accuracy, text-based manipulation ability, and generalization compared to previous methods.
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


