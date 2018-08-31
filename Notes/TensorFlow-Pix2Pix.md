---
layout: page
title: "Tensorflow-Pix2pix"
---

### Exponential Moving Average (EMA)
When training a model, it is often beneficial to maintain moving averages of the trained parameters. Evaluations that use averaged parameters sometimes produce significantly better results than the final trained values.   
shadow_variable = decay * shadow_variable + (1 - decay) * variable
> ema = tf.train.ExponentialMovingAverage(decay=0.99)  
> update_losses = ema.apply([discrim_loss, gen_loss_GAN, gen_loss_L1])  

### Training supervisor
A training helper that checkpoints models and computes summaries.  

> tf.train.Supervisor (newer version tf.train.MonitoredTrainingSession)  

The Supervisor is a small wrapper around a Coordinator, a Saver, and a SessionManager that takes care of common needs of TensorFlow training programs.

### Exporting and Serving Models with TensorFlow
Saver adds operations that allow us to save and restore the model’s parameters by using binary files called checkpoint files, mapping the tensor values to the names of the variables. (Here take note that the the saving use sess as the handle, the saved parameter values to have to exactly match the current graph when restored.)  

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
  

### control_dependencies

TF可以**协调**多个数据流，在存在依赖的节点下非常有用，例如节点B要读取模型参数值V更新后的值，而节点A负责更新参数V，所以节点B就要等节点A执行完成后再执行，不然读到的就是更新以前的数据。这时候就需要个运算控制器 

> tf.control_dependencies(self, control_inputs)  
> **Arguments**：control_inputs: A list of 'Operation' or 'Tensor' objects which must be executed or computed before running the operations defined in the context. (*note* control_inputs is a list)  
> **Return**: A context manager that specifies control dependencies for all operations constructed within the context.  

Example  
> with tf.control_dependencies([a, b, c]):
>       # 'd' and 'e' will only run after 'a', 'b', and 'c' have executed.  
>       d = ...  
>       e = ...  
  
### tf.train.Supervisor
