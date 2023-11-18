---
layout: project_page
permalink: /

title: Learning Dense Correspondence for NeRF-Based Face Reenactment
Paper: https://Com-Vis.github.io/SeFi-IDE/
---

<div class="columns is-centered has-text-centered">
    <div class="column is-four-fifths">
        <h2>Abstract</h2>
        <div class="content has-text-justified">
Face reenactment is challenging due to the need to establish dense correspondence between various face representations for motion transfer. Recent studies have utilized Neural Radiance Field (NeRF) as fundamental representation, which further enhanced the performance of multi-view face reenactment in photo-realism and 3D consistency. However, establishing dense correspondence between different face NeRFs is non-trivial, because implicit representations lack ground-truth correspondence annotations like mesh-based 3D parametric models (e.g., 3DMM) with index-aligned vertexes. Although aligning 3DMM space with NeRF-based face representations can realize motion control, it is sub-optimal for their limited face-only modeling and low identity fidelity. Therefore, we are inspired to ask: Can we learn the dense correspondence between different NeRF-based face representations without a 3D parametric model prior? To address this challenge, we propose a novel framework, which adopts tri-planes as fundamental NeRF representation and decomposes face tri-planes into three components: canonical tri-planes, identity deformations, and motion. In terms of motion control, our key contribution is proposing a Plane Dictionary (PlaneDict) module, which efficiently maps the motion conditions to a linear weighted addition of learnable orthogonal plane bases. To the best of our knowledge, our framework is the first method that achieves one-shot multi-view face reenactment without a 3D parametric model prior. Extensive experiments demonstrate that we produce better results in fine-grained motion control and identity preservation than previous methods.
        </div>
    </div>
</div>

---

## <center> Framework
![](/static/image/pipeline.png)

---

## <center> Cross-Identity Face Reenactment
![](/static/image/demo_0.gif)
![](/static/image/demo_1.gif)

---

## <center> Multi-View Synthesis
![](/static/image/demo_2.gif)
![](/static/image/demo_3.gif)
