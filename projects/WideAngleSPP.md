---
layout: post
title: Conjectures over Wide Angle Super-resolution based on Narrow Angle References
publish: 
show-avatar: false
image: /projects/LFAngularSP/LFS_teaser.png
paperlink: 
codelink:
resourcelink:
---

The challenge of super-resulving a low-resolution wide-angle image (WAL) based on another high-resolution  arrow angle reference (NAH) lies in the following aspects:
- The dense correspondence betweent he WAL and the NAH. This part is essential for transfer of high resolution contents from NAH to WAL. We have some previous work on dense correspondence matching [1], which is highly relevent to this issue.
- * **Jie Chen**, Junhui Hou, Yun Ni, and Lap-Pui. Chau, "Accurate Light Field Depth Estimation with Superpixel Regularization over Partially Occluded Regions,'' _IEEE Transactions on Image Processing_ **(IEEE TIP)**, vol. 27, no. 10, pp. 4889-4900, 2018. [[pdf](https://arxiv.org/abs/1708.01964)] [[code](https://github.com/hotndy/LFDepth_POBR)]


We investigate the challenge of synthesizing dense light fields based on very sparse inputs. With a coarse-to-fine spatial-angular clue modeling, high quality views could be reconstructed that out-performs state-of-the-art methods.  

<p align='center'><figure class="image">
<img src="https://hotndy.github.io/projects/Extrapolation/workshop-1.gif" width="460px">
<img src="https://hotndy.github.io/projects/Extrapolation/workshop-2.5x.gif" width="460px">
<figcaption> Input references "Workshop" (3 views)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Camera baseline extended 2.5x by our PCOC model
</figcaption>
<img src="https://hotndy.github.io/projects/Extrapolation/workshop-5x.gif" width="460px">
<img src="https://hotndy.github.io/projects/Extrapolation/workshop-7.5x.gif" width="460px">
<figcaption> 
Camera baseline extended 5x by our PCOC model
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
extended 7.5x by our PCOC model </figcaption></figure></p>

<p align='center'><figure class="image">
<img src="https://hotndy.github.io/projects/Extrapolation/art-gallery-1.gif" width="300px">
<img src="https://hotndy.github.io/projects/Extrapolation/art-gallery-2.5x.gif" width="300px">
  <img src="https://hotndy.github.io/projects/Extrapolation/art-gallery-5x.gif" width="300px">
<figcaption> Input references "Workshop" (3 views)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Baseline extended 2.5x
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Baseline extended 5x
</figcaption>
</figure></p>
  
<p align='center'><figure class="image">
<img src="https://hotndy.github.io/projects/Extrapolation/bikes-1.gif" width="300px">
<img src="https://hotndy.github.io/projects/Extrapolation/bikes-2.5x.gif" width="300px">
  <img src="https://hotndy.github.io/projects/Extrapolation/bikes-5x.gif" width="300px">
<figcaption> Input references "Workshop" (3 views)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Baseline extended 2.5x
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Baseline extended 5x
</figcaption>
</figure></p>








<p align="center">
<img src="https://hotndy.github.io/projects/LFAngularSP/LFS_teaser.png" width="500px"/>
</p>



