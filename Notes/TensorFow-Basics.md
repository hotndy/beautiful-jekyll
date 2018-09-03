---
layout: post
title: "Tensorflow Basics"
---

- [Saving and restoration of Tensorflow Models - checkpoint](#ckpt)  

## <a name="ckpt"></a> Saving and restoration of Tensorflow Models - checkpoint
### What is a Tensorflow model 
Tensorflow model primarily contains the network design or graph and values of the network parameters that we have trained. Hence, Tensorflow model has two main files:  
* **Meta graph**: This is a protocol buffer which saves the complete Tensorflow graph; i.e. all variables, operations, collections etc. This file has .meta extension.  
* **Checkpoint file**: This is a binary file which contains all the values of the weights, biases, gradients and all the other variables saved. This file has an extension .ckpt. However, Tensorflow has changed this from version 0.11. Now, instead of single .ckpt file, we have two files:  
> mymodel.data-00000-of-00001  
> mymodel.index  

Along with this, Tensorflow also has a file named _checkpoint_ which simply keeps a record of latest checkpoint files saved.  

### Saving a Tensorflow model
Let’s say, you are training a convolutional neural network for image classification. As a standard practice, you keep a watch on loss and accuracy numbers. Once you see that the network has converged, you can stop the training manually or you will run the training for fixed number of epochs. After the training is done, we want to save all the **variables** and **network graph** to a file for future use. So, in Tensorflow, you want to save the graph and values of all the parameters for which we shall be creating an instance of **tf.train.Saver()** class.
```python
saver= tf.train.Saver()
```
Remember that **Tensorflow variables are only alive inside a session**. So, you have to save the model inside a session by calling save method on saver object you just created.
```python
saver.save(sess, 'my-test-model')
```
Here, _sess_ is the session object, while _‘my-test-model’_ is the name you want to give your model. Let’s see a complete example:
```python
import tensorflow as tf
w1 = tf.Variable(tf.random_normal(shape=[2]), name='w1')
w2 = tf.Variable(tf.random_normal(shape=[5]), name='w2')
saver = tf.train.Saver()
sess = tf.Session()
sess.run(tf.global_variables_initializer())
saver.save(sess, 'my_test_model')

# This will save following files in Tensorflow v >= 0.11
# my_test_model.data-00000-of-00001
# my_test_model.index
# my_test_model.meta
# checkpoint
```
If we are saving the model after 1000 iterations, we shall call save by passing the step count:
```python
saver.save(sess, 'my_test_model',global_step=1000)
```
This will just append ‘-1000’ to the model name and following files will be created:  
> my_test_model-1000.index  
> my_test_model-1000.meta  
> my_test_model-1000.data-00000-of-00001  
> checkpoint  
