---
layout: project_page
permalink: /

title: Beyond Inserting:Learning Identity Embedding for Semantic-Fidelity Personalized Diffusion Generation
Paper: https://Com-Vis.github.io/SeFi-IDE/
---

<div class="columns is-centered has-text-centered">
    <div class="column is-four-fifths">
        <h2>Abstract</h2>
        <div class="content has-text-justified">
Advanced diffusion-based Text-to-Image (T2I) models, such as the Stable Diffusion Model, have made significant progress in generating diverse and high-quality images using text prompts alone. However, when non-famous users require personalized image generation for their identities (IDs), the T2I models fail to accurately generate their ID-related images. The main problem is that pre-trained T2I models do not learn the mapping between the new ID prompts and their corresponding visual content. The previous methods either failed to accurately fit the face region or lost the interactive generative ability with other existing concepts in T2I models. In other words, they are unable to generate T2I-aligned and semantic-fidelity images for the given prompts with other concepts such as scenes ("Eiffel Tower"), actions ("holding a basketball"), and facial attributes ("eyes closed"). In this paper, we focus on inserting accurate and interactive ID embedding into the Stable Diffusion Model for semantic-fidelity personalized generation. We address this challenge from two perspectives: face-wise region fitting and semantic-fidelity token optimization. Specifically, we first visualize the attention overfit problem and propose a face-wise attention loss to fit the face region instead of entangling ID-unrelated information, such as face layout and background. This key trick significantly enhances the ID accuracy and interactive generative ability with other existing concepts. Then, we optimize one ID representation as multiple per-stage tokens where each token contains two disentangled features. This expansion of the textual conditioning space improves semantic-fidelity control. Extensive experiments validate that our results exhibit superior ID accuracy, text-based manipulation ability, and generalization compared to previous methods.
        </div>
    </div>
</div>

---

![](/static/image/teaser.png)
Previous methods for inserting new identities (IDs) into pre-trained Text-to-Image diffusion models for personalized generation have two problems: ***(1) Attention Overfit***: As shown in the activation maps of Textural Inversion and ProSpect, their "V\*" attention nearly takes over the whole images, which means the learned embeddings try to encode both the human faces and ID-unrelated information in the reference images, such as the face region layout and background. This problem extremely limits their generative ability and disrupts their interaction with other existing concepts such as "cup", which results in the failure of the given prompt (i.e., they fail to generate the image content aligned with the given prompt). ***(2) Limited Semantic-Fidelity***: Despite alleviating overfit, Celeb Basis introduces excessive face prior, limiting the semantic-fidelity of the learned ID embedding (e.g., the "cup" attention still continues to the "V\*" face region and this limitation hinders the control of facial attributes such as "eyes closed"). Therefore, we propose **Face-Wise Region Fit** and **Semantic-Fidelity Token Optimization** to address problem (1) and (2) respectively.

## <center> Framework
![](/static/image/pipeline.png)
The overview of our framework. We first propose a novel **Face-Wise Attention Loss** to alleviate the attention overfit problem and make the ID embedding focus on the face region to improve the ID accuracy and interactive generative ability. Then, we optimize the target ID embedding as five per-stage tokens with disentangled features to expend textural conditioning space with **semantic-fidelity control ability**.

---

## <center> Single Person's Generation

### Single Person's Comparisons
#### Various scenes, actions, and facial attributes manipulation
![](/static/image/figure3.png)
![](/static/image/com_single_person.png)
#### Various face photo generation or ours and comparison methods
![](/static/image/face_generation_crop.png)

### More Single Person's Generation Results
![](/static/image/figure4.png)

---

## <center> Multiple Persons' Generation
### Multiple Persons' Comparisons
![](/static/image/scene.png)
![](/static/image/action.png)

### More Multiple Persons' Gneration Results
![](/static/image/multiperson.png)

---
## More Evaluation
### Embedding Other Objects
Our method does not introduce face prior from other models, we adopt animals (**Bear**, **Cat**, and **Dog**) and general objects (**Car**, **Chair**, and **Plushie**) for experiments, which show the generalization ability of our method.
![](/static/image/more_object_crop.png)

### Using Stable Diffusion XL
We select SDXL model *stable-diffusion-xl-base-1.0* as the target model and the newly released methods using it for comparison.
![](/static/image/generalize_to_sdxl_crop.png)




