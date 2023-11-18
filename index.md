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

---

## <center> Cross-Identity Face Reenactment
![](/static/image/demo_0.gif)
![](/static/image/demo_1.gif)

---

## <center> Multi-View Synthesis
![](/static/image/demo_2.gif)
![](/static/image/demo_3.gif)
