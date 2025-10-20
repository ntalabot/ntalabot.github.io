---
layout: blank
title: "PartSDF: Part-Based Implicit Neural Representation for Composite 3D Shape Parametrization and Optimization"
permalink: /partsdf/
---

<h1 style="text-align: center;">PartSDF: Part-Based Implicit Neural Representation for Composite 3D Shape Parametrization and Optimization</h1>

<h2 style="text-align: center;">
    <a class="page-link" href="https://ntalabot.github.io/">Nicolas Talabot</a><sup>1</sup>, 
    Olivier Clerc<sup>1</sup>, 
    <a class="page-link" href="https://scholar.google.com/citations?user=cTJTLx8AAAAJ&hl=en">Arda Cinar Demirtas</a><sup>2</sup>, 
    <a class="page-link" href="https://scholar.google.com/citations?user=1z-81bQAAAAJ&hl=en">Alexis Goujon</a><sup>3</sup>, 
    <a class="page-link" href="https://hieulem.github.io/">Hieu Le</a><sup>1,4</sup>,
    <a class="page-link" href="https://scholar.google.com/citations?user=ESA2CsAAAAAJ&hl=en">Doruk Oner</a><sup>2</sup>, 
    <a class="page-link" href="https://people.epfl.ch/pascal.fua?lang=en">Pascal Fua</a><sup>1</sup>
</h2>

<h3 style="text-align: center;"> 
    <div class="centered_div big">
        <div class="div_sidebyside"><sup>1</sup> CVLab, EPFL</div>
        <div class="div_sidebyside"><sup>2</sup> Bilkent University</div>
        <div class="div_sidebyside"><sup>3</sup> Neural Concept</div>
        <div class="div_sidebyside; width:40%"><sup>4</sup> University of North Carolina at Charlotte</div>
    </div>
</h3>

<!-- <div class="centered_div big">
    <div class="div_sidebyside"><img src="/projects/hybridsdf/images/EPFL_logo.png"></div>
</div> -->

<h2 style="text-align: center; padding-top:10px; font-weight:bold;">TMLR 2025</h2>

<div class="centered_div big" style="padding-bottom:20px;">
    <div class="div_rounded_corners"><a href="https://arxiv.org/abs/2502.12985" style="color: #fdfdfd;">
        <i class="ai ai-arxiv"></i> arXiv
    </a></div>
    <div class="div_rounded_corners"><a href="https://github.com/cvlab-epfl/PartSDF" style="color: #fdfdfd;">
        <svg class="svg-icon"><use xlink:href="{{ 'assets/minima-social-icons.svg#github' | relative_url }}"></use></svg> Code
    </a></div>
    <!-- <div class="div_rounded_corners"><a href="https://drive.google.com/file/d/1NtSLewlGysF2RgnXRsp2CfGmJQHzk3lV/view?usp=sharing" style="color: #fdfdfd;">
        <i class="fa-solid fa-folder fa-sm"></i> Data
    </a></div> -->
    <!-- <div class="div_rounded_corners"><a href="https://www.youtube.com/watch?v=vkMtn5Q446E&list=PLDqmL95Gm8yLluJMGuplQdre9QwnobvCt&index=9" style="color: #fdfdfd;">
        <svg class="svg-icon"><use xlink:href="{{ 'assets/minima-social-icons.svg#youtube' | relative_url }}"></use></svg>Video
    </a></div> -->
</div>

<img src="/projects/partsdf/images/drivaer_manip.gif" style="display:block; margin:auto; width: 30%; max-width: 30%; height:auto;">


<div class="div_text">
    <h1 style="text-align: center;">Abstract</h1>
    Accurate 3D shape representation is essential in engineering applications such as design, optimization, and simulation. In practice, engineering workflows require structured, part-based representations, as objects are inherently designed as assemblies of distinct components. However, most existing methods either model shapes holistically or decompose them without predefined part structures, limiting their applicability in real-world design tasks. We propose PartSDF, a supervised implicit representation framework that explicitly models composite shapes with independent, controllable parts while maintaining shape consistency. Thanks to its simple but innovative architecture, PartSDF outperforms both supervised and unsupervised baselines in reconstruction and generation tasks. We further demonstrate its effectiveness as a structured shape prior for engineering applications, enabling precise control over individual components while preserving overall coherence.
</div>


<hr class="hr_style">


<div class="div_text div_gray">
    <h3> Method </h3>
    <div style="width: 100%; display:block; margin:auto; padding-bottom:2px;"><img style="margin:5px; border-radius:10px;" src="/projects/partsdf/images/architecture.png"></div>
    <p class="fig_caption" style="width: 100%; padding-bottom:10px"> (Left) Overview of PartSDF cross-part auto-decoder. (Right) Single- and cross-part layers arrangement in the decoder <i>f</i><sub>θ</sub>. </p>
    <div style="width: 100%; display:inline-block;">
    At its core, our model is a cross-part auto-decoder <i>f</i><sub>θ</sub> that takes as input part latents <b>z</b><sub><i>p</i></sub> and poses expressed in terms of a quaternion <b>q</b><sub><i>p</i></sub>, translation <b>t</b><sub><i>p</i></sub>, and scale <b>s</b><sub><i>p</i></sub>, along with the query position <b>x</b>. It outputs signed distances ŝ<sub><i>p</i></sub> for all parts at the queried position, which may be combined into the global signed distance ŝ. Our decoder alternates between updating each part independently and sharing information across parts, allowing them to adapt to one another while preserving modularity. This is implemented through a sequence of lightweight convolutions applied along rows and columns of the part feature matrix.
    </div>
</div>

<div class="div_text div_gray">
    <h3> Results </h3>
    <div style="width: 100%; display:inline-block;"> Reconstruction </div>
    <div style="width: 100%; display:block; margin:auto; padding-bottom:2px;"><img style="margin:5px; border-radius:10px;" src="/projects/partsdf/images/reconstruction.png"></div>
    <p class="fig_caption" style="width: 100%; padding-bottom:10px"> Reconstruction of test shapes. For part-based methods, we color each part with a different color and translate the helix outside of the mixers for visualization. </p>
    <div style="width: 100%; display:inline-block;"> Generation </div>
    <div style="width: 100%; display:block; margin:auto; padding-bottom:2px;"><img style="margin:5px; border-radius:10px;" src="/projects/partsdf/images/generation.png"></div>
    <p class="fig_caption" style="width: 100%; padding-bottom:10px"> Shape generation and pose-conditioned generation (Ours<sup>†</sup>) where part latents are generated based on the poses' coarse description of the shape (left image for each pair). When possible, the helix is translated outside of the mixer for visualization. </p>
</div>


<div class="div_text div_gray">
    <div class="div_aligned">
    <div style="width: 60%; display:inline-block;"> 
    <h3 style="text-align: left;"> Manipulation </h3>
    PartSDF represents 3D shapes as assemblies of controllable parts. Each component can be moved, reshaped, or replaced independently, while the model preserves overall consistency. This enables intuitive part-based editing for design and optimization tasks.
    </div>
    <div style="width: 39%; display:inline-block; vertical-align:middle; margin-left:3%;"><img style="margin:5px; width:100%;border-radius:10px;" src="/projects/partsdf/images/shape_manipulation.gif"> </div>
    </div>
</div>


<div class="div_text div_gray">
    <h3> Optimization </h3>
    <div style="width: 100%; display:inline-block; margin-bottom:10px">
    Using PartSDF as a differentiable shape representation, complex designs can be optimized directly in 3D. Here, the car body is automatically refined to minimize drag, while the wheels remain fixed, showcasing part-aware optimization with overall consistency.
    </div>
    <div style="width: 100%; display:block; margin:auto; text-align:center;"><img style="margin:5px; border-radius:10px;" src="/projects/partsdf/images/shape_optim_3.gif"></div>
    <p class="fig_caption" style="width: 100%; padding-bottom:10px"> We show individual parts (left) and the surface pressure (right). </p>
</div>


<hr class="hr_style_thin">

<h2> BibTeX </h2>
If you find our work useful, please cite it:

    @misc{talabot2025partsdf,
        title={PartSDF: Part-Based Implicit Neural Representation for Composite 3D Shape Parametrization and Optimization}, 
        author={Nicolas Talabot and Olivier Clerc and Arda Cinar Demirtas and Hieu Le and Doruk Oner and Pascal Fua},
        year={2025},
        eprint={2502.12985},
        archivePrefix={arXiv},
        primaryClass={cs.CV},
        url={https://arxiv.org/abs/2502.12985}
    }