
### Exponential Moving Average (E)
When training a model, it is often beneficial to maintain moving averages of the trained parameters. Evaluations that use averaged parameters sometimes produce significantly better results than the final trained values.   
shadow_variable = decay * shadow_variable + (1 - decay) * variable
> ema = tf.train.ExponentialMovingAverage(decay=0.99)  
> update_losses = ema.apply([discrim_loss, gen_loss_GAN, gen_loss_L1])  

### control_dependencies
It is not a conditional. It is a mechanism to add dependencies to whatever ops you create in the with block. More specifically, what you specify in the argument to control_dependencies is ensured to be evaluated before anything you define in the with block. 
