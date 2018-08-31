---
layout: page
title: "TensorFlow-Pix2Pix"
---

### Exponential Moving Average (EMA)
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

### Exporting and Serving Models with TensorFlow

Saver adds operations that allow us to save and restore the model’s parameters by using binary files called _checkpoint files_, mapping the tensor values to the names of the variables. (Here take note that the the saving use sess as the handle, the saved parameter values to have to exactly match the current graph when restored.)  
> saver = tf.train.Saver(max_to_keep=7, keep_checkpoint_every_n_hours=0.5)  

### checkpoints and summary  
You save the model to checkpoints because the Variables in the model, including neural network weights and biases and the global_step counter, keep changing during the training process. The structure of the model doesn't change. The saved checkpoints allow you to load the trained model for serving and to resume training later.

Supervisor帮助我们处理一些事情 
（1）自动去checkpoint加载数据或初始化数据 
（2）自身有一个Saver，可以用来保存checkpoint 
（3）有一个summary_computed用来保存Summary 
所以，我们就不需要： 
（1）手动初始化或从checkpoint中加载数据 
（2）不需要创建Saver，使用sv内部的就可以 
（3）不需要创建summary writer








