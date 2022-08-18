---
layout: blank
---

<h1 style="text-align: center;"> HybridSDF: Combining Deep Implicit Shapes and Geometric Primitives for 3D Shape Representation and Manipulation </h1>

/!\ Under construction! /!\

<!-- <h2 style="text-align: center;"><a class="page-link" href="https://senakicir.github.io/">Sena Kiciroglu</a><sup>1</sup>, <a class="page-link" href="https://weiwangtrento.github.io/">Wei Wang</a><sup>1,2</sup>, <a class="page-link" href="https://people.epfl.ch/mathieu.salzmann">Mathieu Salzmann</a><sup>1,3</sup>, <a class="page-link" href="https://people.epfl.ch/pascal.fua/bio?lang=en">Pascal Fua</a><sup>1</sup></h2>

<h3 style="text-align: center;"> 
<sup>1</sup> CVLab, EPFL, Switzerland <br>
<sup>2</sup> MHUG, University of Trento, Italy <br>
<sup>3</sup> Clearspace, Switzerland </h3>

<div class="centered_div big">

<div class="div_sidebyside"><img src="https://lh4.googleusercontent.com/7uTSvpyjHR-PdHWJzORYi2VZIsv1D5H4Ocnswk0zVJ8P7n5xc-c6KGNUQRN6ni8dNGA=w2400"></div>
<div class="div_sidebyside"><img src="https://lh5.googleusercontent.com/ZB88A6mvFp-4O-zGKMGNDU1FV5H5QA8_n8qvWt7eyLa_rRpwJKYQ8r4Kv47xZMSRtco=w2400"></div>
<div class="div_sidebyside"><img src="https://lh6.googleusercontent.com/8u5qOkDzExfHNz5YS-AInl5nVgMNgngcU0S-wM0wkEOGXsmQKQo3kSqq2HEA2-Hdfv8=w2400"></div>
</div>

<div class="centered_div big" style="padding-top:25px;">
<div class="div_rounded_corners"><a href="https://arxiv.org/pdf/2012.04731.pdf" style="color: #fdfdfd;">arXiv</a></div>
<div class="div_rounded_corners"><a href="" style="color: #fdfdfd;">Code</a></div>
<div class="div_rounded_corners"><a href="" style="color: #fdfdfd;">Video</a></div>
</div>

<img src="https://lh4.googleusercontent.com/wHWR_HpkrH4UhS55Q6eY1wFc_SotTWEYkWvKqSTIVhPTkZ4SYMPHwEEEYE1W1n8XjjY=w2400" style="display:block; margin:auto; width: 75%; max-width: 75%; height:auto;">

<div class="div_text">
<h1 style="text-align: center;">Abstract</h1>
Long term human motion prediction is essential in safety-critical applications such as human-robot interaction and autonomous driving. In this paper we show that to achieve long term forecasting, predicting human pose at every time instant is unnecessary. Instead, it is more effective to predict a few keyposes and approximate intermediate ones by interpolating the keyposes. <br><br>

We demonstrate that our approach enables us to predict realistic motions for up to 5 seconds in the future, which is far longer than the typical 1 second encountered in the literature. Furthermore, because we model future keyposes probabilistically, we can generate multiple plausible future motions by sampling at inference time. Over this extended time period, our predictions are more realistic, more diverse and better preserve the motion dynamics than those state-of-the-art methods yield.
</div>

<hr class="hr_style">

<div class="div_text div_gray">
<div style="width: 100%; display:inline-block;">
<h3> Long Term Motion Prediction </h3>

Motion prediction is an essential component in safety-critical applications, such as human-robot interaction and autonomous driving. Most existing methods have accurate pose predictions of up to 1 second. Our work extends this time horizon to <b>5 seconds</b>, by following a different approach. Instead of regressing a pose at every future timestep, we aim to predict the next "keypose" in the sequence via a classification scheme.</div>
</div>

<div class="div_text div_gray">
<h3> Keyposes </h3>

<div style="width: 80%; display:block; margin:auto; padding-bottom:2px;"><img style="margin:5px; border-radius:10px;" src="https://lh6.googleusercontent.com/Z_Sa7pVsInhixF5A-tA2VPx7VYL_s841GFPpvDdoPWa_5uw_74VI-1ptQiaz5dxhsvA=w2400"></div>
<p class="fig_caption" style="width: 80%; padding-bottom:10px"> Figure: Distribution of keyposes in sequence. Plots show the x, y, and z coordinates of a single joint across time.</p>
<div style="width: 100%; display:inline-block;">
Human motion follows patterns that are well-represented by a <b>few essential poses</b> in the sequence. We call such poses "keyposes". By interpolating between the keyposes, we can reconstruct the original sequence. Therefore, it is sufficient to only predict the keyposes in the sequence. We extract the keyposes by determining the poses which yield <b>minimum L2 error</b> when used to reconstruct the original sequence.</div>
</div>

<div class="div_text div_gray">
<div class="div_aligned">
<div style="width: 35%; display:inline-block; vertical-align:middle;"><img style="margin:5px; width:85%;border-radius:10px;" src="https://lh6.googleusercontent.com/2W59IspHQFr65kN4HIZDBfRYmjRuUTx6a62-Tz8nVKC_3x3swflRTeVAJZupeOH062s=w2400"> </div>
<div style="width: 65%; display:inline-block;"> 
<h3 style="text-align: right;"> Predicting Keyposes</h3>

We cluster and label the keyposes and turn motion prediction into a <b>classification</b> problem. This shifts the focus on the transition from one keypose label to another and avoid accumulating errors. We have designed a GRU based framework for keypose prediction. Moreover, by sampling the predicted logits during inference we can generate <b>diverse future motions</b>. 
</div>
</div>
</div>



<h3> BibTeX </h3>
  If you find our work useful, please cite it as:

    @inproceedings{kiciroglu2022keyposes,
      author = {Kiciroglu, Sena and Wang, Wei and Salzmann, Mathieu and Fua, Pascal},
      booktitle = {3DV},
      title = {Long Term Motion Prediction Using Keyposes},
      year = {2022}
    } -->