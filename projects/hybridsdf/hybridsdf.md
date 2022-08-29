---
layout: blank
title: "HybridSDF: Combining Deep Implicit Shapes and Geometric Primitives for 3D Shape Representation and Manipulation"
permalink: /hybridsdf/
---

<h1 style="text-align: center;">HybridSDF: Combining Deep Implicit Shapes and Geometric Primitives for 3D Shape Representation and Manipulation</h1>

<h2 style="text-align: center;">
    <a class="page-link" href="https://subeeshvasu.github.io/">Subeesh Vasu</a><sup>*,1</sup>,
    <a class="page-link" href="https://ntalabot.github.io/">Nicolas Talabot</a><sup>*,1</sup>, 
    <a class="page-link" href="https://scholar.google.com/citations?user=A9tNPiQAAAAJ&hl=en">Artem Lukoianov</a><sup>1,2</sup>, 
    <a class="page-link" href="https://scholar.google.com/citations?user=u56iZPkAAAAJ&hl=en">Pierre Baqué</a><sup>2</sup>, <br>
    <a class="page-link" href="https://scholar.google.com/citations?user=3hoYiLAAAAAJ&hl=en">Jonathan Donier</a><sup>2</sup>, 
    <a class="page-link" href="https://people.epfl.ch/pascal.fua?lang=en">Pascal Fua</a><sup>1</sup>
</h2>

<h3 style="text-align: center;"> 
    <sup>*</sup> Equal contributions <br>
    <div class="centered_div big">
        <div class="div_sidebyside"><sup>1</sup> CVLab, EPFL</div>
        <div class="div_sidebyside"><sup>2</sup> Neural concept</div>
    </div>
</h3>

<div class="centered_div big">
    <div class="div_sidebyside"><img src="/projects/hybridsdf/images/EPFL_logo.png"></div>
    <div class="div_sidebyside"><img src="/projects/hybridsdf/images/Neural_Concept_logo.png"></div>
</div>

<div class="centered_div big" style="padding-top:5px; padding-bottom:25px;">
    <!-- <div class="div_rounded_corners"><a href="" style="color: #fdfdfd;">Paper</a></div> -->
    <div class="div_rounded_corners"><a href="https://arxiv.org/abs/2109.10767" style="color: #fdfdfd;">arXiv</a></div>
    <div class="div_rounded_corners" style="background: #acaaaa"><p style="color: #fdfdfd;">Dataset</p></div>
    <div class="div_rounded_corners" style="background: #acaaaa"><p style="color: #fdfdfd;">Video</p></div>
</div>

<img src="/projects/hybridsdf/images/mixer_clip.gif" style="display:block; margin:auto; width: 50%; max-width: 50%; height:auto;">


<div class="div_text">
    <h1 style="text-align: center;">Abstract</h1>
    Deep implicit surfaces excel at modeling generic shapes but do not always capture the regularities present in manufactured objects, which is something simple geometric primitives are particularly good at. In this paper, we propose a representation combining latent and explicit parameters that can be decoded into a set of deep implicit and geometric shapes that are consistent with each other. As a result, we can effectively model both complex and highly regular shapes that coexist in manufactured objects. This enables our approach to manipulate 3D shapes in an efficient and precise manner.
</div>


<hr class="hr_style">


<div class="div_text div_gray">
    <div style="width: 100%; display:inline-block;">
    <h3> Hybrid Representation </h3>
    We propose a hybrid implicit representation that combines geometric primitives and deep implicit surfaces. To this end, we define three types of primitives represented by their <i>Signed Distance Functions</i> (SDFs):
    <ul>
        <li><b>Generic</b> primitives that may have arbitrarily complex shapes. Their SDFs are computed by neural networks; they are therefore purely deep implicit surfaces.</li>
        <li><b>Geometric</b> primitives, such as spheres and cylinders. Their SDFs are computed analytically given some geometric parameters.</li>
        <li><b>Geometry-assisted</b> primitives that resembles geometric ones but can deviate from them, such as car wheels that are almost but not quite cylinders. Their SDFs are computed by neural networks but are constrained to be similar to those of the corresponding geometries.</li>
    </ul>
    The number of primitives depends on the part decomposition of the shapes and, in practice, are known to the engineers performing the design. Parts with strong regularities should be represented by either geometric or geometry-assisted primitives, while the more complex ones should be generic primitives.
    </div>
</div>


<div class="div_text div_gray">
    <h3> Network </h3>
    <div style="width: 100%; display:block; margin:auto; padding-bottom:2px;"><img style="margin:5px; border-radius:10px;" src="/projects/hybridsdf/images/hybridsdf.png"></div>
    <p class="fig_caption" style="width: 100%; padding-bottom:10px"> Figure: <i>HybridSDF architecture.</i> A Point Encoder predict the parameters of the parts while multiple branches decode the different primitives' SDFs, which are combined to reconstruct the full shape. Grey boxes denote components used only during training. </p>
    <div style="width: 100%; display:inline-block;">
    The shapes are decoded from a combination of implicit and explicit parameters: latent vectors <b>LV</b> and geometric parameters <b>S</b>, <b>R</b>, and <b>T</b> that are respectively shape parameters (such as sphere radius), rotations, and translations. Different decoding branches output the SDFs of the three primitive types, which are then combined to obtain the full shape.
    </div>
</div>


<!-- TODO: add cars with bad wheels for baselines -->
<div class="div_text div_gray">
    <div class="div_aligned">
    <div style="width: 42%; display:inline-block;"> 
    <h3 style="text-align: left;"> Reconstruction </h3>
    Our representation is interpretable in terms of parts that have a semantic meaning and enforces consistency between them at no loss of accuracy. Additionally, it yields an increase in local regularity and realism of the geometric and geometry-assisted parts.
    </div>
    <div style="width: 55%; display:inline-block; vertical-align:middle; margin-left:3%;"><img style="margin:5px; width:100%;border-radius:10px;" src="/projects/hybridsdf/images/reconstruction.gif"> </div>
    </div>
</div>


<div class="div_text div_gray">
    <div class="div_aligned">
    <div style="width: 47%; display:inline-block; vertical-align:middle; margin-right:3%;"><img style="margin:5px; width:100%;border-radius:10px;" src="/projects/hybridsdf/images/manipulation_car.gif"> </div>
    <div style="width: 50%; display:inline-block;"> 
    <h3 style="text-align: right;"> Parametric Manipulation </h3>
    Using <i>HybridSDF</i>, one can manipulate 3D objects by directly editing the geometric parameters <b>S</b>, <b>R</b>, and <b>T</b>. The disentanglement of the parameter space makes it easy to define these specifications for several parts and have the rest of the object adapts to them. Moreover, the manipulation requires no optimization and is therefore fast and exact.
    </div>
    </div>
</div>



<h2> BibTeX </h2>
If you find our work useful, please cite it as:

    @inproceedings{vasutalabot2022hybridsdf,
        author = {Vasu, Subeesh and Talabot, Nicolas and Lukoianov, Artem and Baqu\'e, Pierre and Donier, Jonathan and Fua, Pascal},
        title = {HybridSDF: Combining Deep Implicit Shapes and Geometric Primitives for 3D Shape Representation and Manipulation},
        booktitle = {International Conference on 3D Vision},
        year = {2022}
    }

<hr class="hr_style_thin">

<!-- References -->
<h3> References </h3>
<div class="div_refs">
    <div class="div_aligned_top">
    <div style="width: 12%; display:inline-block; text-align:right; margin-right:1%;">[<i>DeepSDF</i>]</div>
    <div style="width: 87%; display:inline-block;">J. J. Park, P. Florence, J. Straub, R. A. Newcombe, and S. Lovegrove. DeepSDF: Learning Continuous Signed Distance Functions for Shape Representation. In <i>Conference on Computer Vision and Pattern Recognition</i>, 2019.</div>
    </div>
</div>
<div class="div_refs">
    <div class="div_aligned_top">
    <div style="width: 12%; display:inline-block; text-align:right; margin-right:1%;">[<i>NeuralParts</i>]</div>
    <div style="width: 87%; display:inline-block;">D. Paschalidou, A. Katharopoulos, A. Geiger, and S. Fidler. Neural Parts: Learning Expressive 3D Shape Abstractions with
Invertible Neural Networks. In <i>Conference on Computer Vision and Pattern Recognition</i>, pages 3204--3215, 2021.</div>
    </div>
</div>