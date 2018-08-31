
### Exponential Moving Average (E)
When training a model, it is often beneficial to maintain moving averages of the trained parameters. Evaluations that use averaged parameters sometimes produce significantly better results than the final trained values.   
shadow_variable = decay * shadow_variable + (1 - decay) * variable
> ema = tf.train.ExponentialMovingAverage(decay=0.99)  
> update_losses = ema.apply([discrim_loss, gen_loss_GAN, gen_loss_L1])  

### control_dependencies

TF可以协调多个数据流，在存在依赖的节点下非常有用，例如节点B要读取模型参数值V更新后的值，而节点A负责更新参数V，所以节点B就要等节点A执行完成后再执行，不然读到的就是更新以前的数据。这时候就需要个运算控制器 

> tf.control_dependencies(self, control_inputs)  
> arguments：control_inputs: A list of 'Operation' or 'Tensor' objects which must be executed or computed before running the operations defined in the context. (*note* control_inputs is a list)  
> return: A context manager that specifies control dependencies for all operations constructed within the context.  

其实用法很简单，只有在 control_inputs被执行以后，上下文管理器中的操作才会被执行。例如

It is not a conditional. It is a mechanism to add dependencies to whatever ops you create in the with block. More specifically, what you specify in the argument to control_dependencies is ensured to be evaluated before anything you define in the with block. 


### tf.train.Supervisor
