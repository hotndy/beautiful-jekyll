---
layout: page
title: Light Field Imaging and Applications
show-avatar: false
---
A _Light Field camera_ captures the image of 3D world in a more immersive way than conventional 2D imaging. 
The light rays are recorded not only when they reach and integrate at the camera sensor plane, but also when they propagate across the imaging system. This naturally embeds the 3D spatial information of he scene contents into the final output, and enables a variety of amazing and useful applications that is beyond the limits of traditional imaging.

I have been working on a number of topics and applications that are related to light field imaging. This page gives a brief overlook of these areas.

> - Light Field Acquisition and Reconstruction  
> - Light Field Data Compression  
> - Light Field Depth Esitmation  
- Light Field View Synthesis  
- Novel Applications  
  
- Light Field Rain Removal
- Reflection Removal based on a Single LF Capture

<p align="center">
<img src="https://hotndy.github.io/projects/LFCS/opticalDiagram.jpg" width="500px"/>
</p>
  
The light field is a vector function that describes the amount 42 of light propagating in every direction through every point 43 in space [1]. As illustrated in Fig. 1, light field is usually 44 represented as four-dimensional data: L(x, y, s, t), in which 45 (x, y) is at the micro-lens array plane (which is near the 46 focal plane of the main lens); and (s, t) is at the camera main 47 lens plane. The four parameters at two planes can sufficiently 48 describe the propagation of all light rays in the imaging 49 system.
