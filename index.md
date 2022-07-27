---
layout: single
permalink: /
hidden: true
classes: wide
sidebar:
  - title: "Visual Foresight With a Local Dyanmics Model"
    image: 
    text: "Colin Kohler, Robert Platt Northeastern University" 
---
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>

**Abstract:** Model-free policy learning has been shown to be capable of learning manipulation policies which can 
solve long-time horizon tasks using single-step manipulation primitives. However, training these 
policies is a time-consuming process requiring large amounts of data. We propose the Local Dynamics 
Model (LDM) which efficiently learns the state-transition function for these manipulation primitives. 
By combining the LDM with model-free policy learning, we can learn policies which can solve complex 
manipulation tasks using one-step lookahead planning. We show that the LDM is both more sample-efficient 
and outperforms other model architectures. When combined with planning, we can outperform other 
model-based and model-free policies on several challenging manipulation tasks in simulation. 

# Paper
Our work has been accepted to the 54th International Symposium on Robotics (ISRR 2022). Currently a preprint is
avaliable on [Arxiv](https://arxiv.org/pdf/2206.14802.pdf).

# Local Dynamics Model
We investigate the use of visual foresight for use in complex robotic manipulation tasks through the use of a Local
Dynamics Model (LDM). The LDM learns the state-transition function for the pick and place primitves within the 
spatial action space. Unlike previous work which learns a dynamics model in latent space, LDM exploits the encoding
of actions into image-space native to the spatial action space to instead learn an image-to-image transition function.
Within this image space, we leverage both the localized effect of pick-and-place actions and the spatial equivariance
property of top-down manipulation to dramatically improve the sample efficeny of the dynamics model. The figure below
shows these two properties.

<figure>
  <a href="/assets/images/ldm_ex.png"><img src="/assets/images/ldm_ex.png"></a>
</figure>

In order to predict the next scene image $$s'_{scene}$$, we learn a model $$\bar{f}$$ that predicts how the scene will 
change within $$B_a$$, a neighborhood around the action $$a$$. The output of the model is then inserted back into the 
original scene. The figure below details the UNet model architecture which we use for the LDM in our experiments,
each blue box represents a 3x ResNet Block. For additional details on Local Dyanmics Models see our paper.

{% include figure image_path="/assets/images/ldm_ex.png" %}

<figure>
  <a href="/assets/images/ldm_model_sm.png"><img src="/assets/images/ldm_model_sm.png"></a>
</figure>

# Experiments

<figure>
  <a href="/assets/images/manip_details.png"><img src="/assets/images/manip_details.png"></a>
</figure>

<figure class="half">
  <a href="/assets/images/block_stacking_3_learning_curve.png"><img src="/assets/images/block_stacking_3_learning_curve.png"></a>
  <a href="/assets/images/house_2_learning_curve.png"><img src="/assets/images/house_2_learning_curve.png"></a>
</figure>

<figure class="half">
  <a href="/assets/images/bottle_tray_learning_curve.png"><img src="/assets/images/bottle_tray_learning_curve.png"></a>
  <a href="/assets/images/bin_packing_learning_curve.png"><img src="/assets/images/bin_packing_learning_curve.png"></a>
</figure>


# Video

# Code
The code for the Local Dynamics Model detailed in this work can be found [here](https://github.com/ColinKohler/LocalDynamicsModel).

# Citation
```
@misc{https://doi.org/10.48550/arxiv.2206.14802,
  doi = {10.48550/ARXIV.2206.14802},
  url = {https://arxiv.org/abs/2206.14802},
  author = {Kohler, Colin and Platt, Robert},
  title = {Visual Foresight With a Local Dynamics Model},
  publisher = {arXiv},
  year = {2022},
  copyright = {Creative Commons Attribution 4.0 International}
}

```

# Contact
If you have any questions, please feel free to contact [Colin Kohler](https://colinkohler.github.io/webpage/) at kohler[dot]c[at]northeastern[dot]edu.