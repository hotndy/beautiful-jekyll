---
layout: page
title: "TensorFlow-Pix2Pix"
---

### Exponential Moving Average (E)
When training a model, it is often beneficial to maintain moving averages of the trained parameters. Evaluations that use averaged parameters sometimes produce significantly better results than the final trained values.   
> shadow_variable = decay * shadow_variable + (1 - decay) * variable  
> ema = tf.train.ExponentialMovingAverage(decay=0.99)  
> update_losses = ema.apply([discrim_loss, gen_loss_GAN, gen_loss_L1])  

### control_dependencies
It is not a conditional. It is a mechanism to add dependencies to whatever ops you create in the with block. More specifically, what you specify in the argument to control_dependencies is ensured to be evaluated before anything you define in the with block. 

### Training supervisor
A training helper that checkpoints models and computes summaries.
> tf.train.Supervisor  (newer version tf.train.MonitoredTrainingSession)    

The Supervisor is a small wrapper around a *Coordinator*, a *Saver*, and a *SessionManager* that takes care of common needs of TensorFlow training programs.
