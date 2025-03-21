---
layout: project_page
permalink: /

title: Beyond Inserting:Learning Subject Embedding for Semantic-Fidelity Personalized Diffusion Generation
Paper: https://Com-Vis.github.io/SeFi-IDE/
---

<div class="columns is-centered has-text-centered">
    <div class="column is-four-fifths">
        <h2>Abstract</h2>
        <div class="content has-text-justified">
Text-to-Image (T2I) personalization based on advanced diffusion models (e.g., Stable Diffusion), aiming to generate images of the target subjects given various prompts, has draw huge attention. However, when users require personalized image generation for specific subjects such as user himself or his pet cat, the T2I models fail to accurately generate their subject-preserved images. The main problem is that pre-trained T2I models do not learn the T2I mapping between the target subjects and their corresponding visual contents. Even if multiple target subject images are provided, previous personalization methods either failed to accurately fit the subject region or lost the interactive generative ability with other existing concepts in T2I model space. For example, they are unable to generate T2I-aligned and semantic-fidelity images for the given prompts with other concepts such as scenes (''Eiffel Tower''), actions (''holding a basketball''), and facial attributes (''eyes closed''). In this paper, we focus on inserting accurate and interactive subject embedding into the Stable Diffusion Model for semantic-fidelity personalized generation using one image. We address this challenge from two perspectives: subject-wise attention loss and semantic-fidelity token optimization. Specifically, we propose a subject-wise attention loss to guide the subject embedding onto a manifold with high subject identity similarity and diverse interactive generative ability. Then, we optimize one subject representation as multiple per-stage tokens and each token contains two disentangled features. This expansion of the textual conditioning space enhances the semantic control, thereby improving semantic-fidelity. We conduct extensive experiments on the most challenging subjects, face identities, to validate that our results exhibit superior subject accuracy and fine-grained manipulation ability. We further validate the generalization of our methods on various non-face subjects.
        </div>
    </div>
</div>

---

![](/static/image/teaser.png)

Previous methods for inserting new subjects (e.g., face identities and cats) into pre-trained Text-to-Image diffusion models for personalized generation have two problems: (1) **Attention Overfit** : As shown in the activation maps of Textual Inversion and Prospect, their ''V*'' attention nearly takes over the whole images, which means the learned embedding try to encode both the target subject and subject-unrelated information in the target images, such as the subject region layout and background. This problem extremely limits their interaction with other existing concepts such as ''cup'', which results in the failure of generating the image content aligned with the given prompt. (2) **Limited Semantic-Fidelity**: Despite they alleviate overfit by introducing subject prior such as face recognition models, the ''cup'' attention of Celeb Basis still affects the ''V*'' face region and this limitation hinders the control of subject attributes such as ''eyes closed'', while IP-Adapter learns mismatched subject embedding (i.e., its attention of  ''V*'' is inconsistent with the generated face). These flaws result in the limited semantic-fidelity of text-to-image generation. Therefore, we propose **Subject-Wise Attention Loss** and **Semantic-Fidelity Token Optimization** to address problem (1) and (2) respectively.

## <center> Framework
![](/static/image/pipeline.png)
The overview of our framework. We first propose a novel **Subject-Wise Attention Loss** to alleviate the attention overfit problem and make the subject embedding focus on the subject region to improve subject accuracy and interactive generative ability. Then, we optimize the target subject embedding as five per-stage tokens pairs with disentangled features to expend textural conditioning space with **Semantic-Fidelity** control ability.

## <center> Motivation
![](/static/image/why_atten.png)
We note that T2I models have learned a robust general concept prior for various subcategories, e.g., different human identities falling under the broad concept of ''person'', which could act as an anchor for regularizing subject embedding. Furthermore, when ''Obama'' is replaced with ''Hillary'' in prompts, the attention maps for each token remain similar. Thus, we propose the subject-wise attention loss, which encourages the effect of each token to align with those from a reference prompt for dual optimization of controllability and subject similarity.

![](/static/image/why_kvsplit.png)
When it comes to the generation of images with controllable attributes, previous methods fail to generate examples like ''an old person''. By analyzing the generation process of Stable Diffusion, we believe this is due to two reasons: (1)*Attention Mismatch*: The ${K}$ feature cooperates with the image feature ${Q}$ to decide how to sample from the feature ${V}$. However, the attention map is unmatched for prompts like ''beard'' or ''closed''. (2)*Insufficient ${V}$ Feature*: Even with a similar attention map (same $K$), the $V$ feature from prompt ''an old Emma Watson/Rich Sommer'', functioning as a provider of detailed texture features, may not adequately represent the ''old'' on them. We address this challenge by setting different $K$ or $V$ while keeping the other same as comparison methods. This observation underscores the impact of separately optimizing embeddings for $K$ and $V$ in facilitating semantic-fidelity generation.

---

# Results

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
## <center> More Evaluation
### Ablation
#### Choice of $\lambda$
With a small $\lambda$ value, the learned embedding would overfit to the target subject. Relatively, employing a larger $\lambda$ ($0.01$ or $0.05$) leads to underfitting of the optimized embedding to the target subject (lower subject similarity). $\lambda=0.003$ would be the best choice.
![](/static/image/ablation_lambda.png)
#### Attention Loss
Comparing Subject-Wise Attention Loss with existing attention regularization techniques.
![](/static/image/attention_com1.png)
![](/static/image/attention_com2.png)
![](/static/image/attention_ablation.png)
#### Number of K-V pairs
A sensitivity analysis of the Number of K-V Feature Pairs.
![](/static/image/kv_num_ablation.png)
#### Correlation of user selection with ID(P) metric
We analyze the correlation between user selection with Prompt score and ID(P) score.
![](/static/image/prompt_idp_score.png)

### Embedding Other Objects
#### Various subject generation or ours and comparison methods
Our method does not introduce face prior from other models, we adopt animals (**Bear**, **Cat**, and **Dog**) and general objects (**Car**, **Chair**, and **Plushie**) for experiments, which show the generalization ability of our method.
![](/static/image/more_objects.png)
![](/static/image/various_object1.png)
![](/static/image/various_object2.png)
#### Various scenes, actions, and attributes manipulation
![](/static/image/object_multi.png)

### Using Stable Diffusion XL
We select SDXL model *stable-diffusion-xl-base-1.0* as the target model and the newly released methods using it for comparison.
![](/static/image/generalize_to_sdxl_crop.png)

### Combining with ControlNet
![](/static/image/controlnet.png)

---
## <center> Limitation
Inherent limitations of current models persist, including semantic confusion in multiple similar concept generation and complex control (e.g., “winking” and “full of books”).
![](/static/image/limitation.png)
