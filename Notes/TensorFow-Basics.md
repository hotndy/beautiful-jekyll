---
layout: post
title: "Tensorflow Basics"
---

- [Saving and restoration of Tensorflow Models - checkpoint](#ckpt)
  - [What is a Tensorflow model](#what)
  - [Saving a Tensorflow model](#saving)
  - [Importing a pre-trained model](#import)  

## <a name="ckpt"></a> Saving and restoration of Tensorflow Models - checkpoint
### <a name="what"></a> What is a Tensorflow model 
Tensorflow model primarily contains the network design or graph and values of the network parameters that we have trained. Hence, Tensorflow model has two main files:  
* **Meta graph**: This is a protocol buffer which saves the complete Tensorflow graph; i.e. all variables, operations, collections etc. This file has .meta extension.  
* **Checkpoint file**: This is a binary file which contains all the values of the weights, biases, gradients and all the other variables saved. This file has an extension .ckpt. However, Tensorflow has changed this from version 0.11. Now, instead of single .ckpt file, we have two files:  
> mymodel.data-00000-of-00001  
> mymodel.index  

Along with this, Tensorflow also has a file named _checkpoint_ which simply keeps a record of latest checkpoint files saved.  

### <a name="saving"></a> Saving a Tensorflow model
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
Let’s say, while training, we are saving our model after every 1000 iterations, so _.meta_ file is created the first time(on 1000th iteration) and we don’t need to recreate the _.meta_ file each time(so, we don’t save the .meta file at 2000, 3000.. or any other iteration). We only save the model for further iterations, as the graph will not change. Hence, when we don’t want to write the meta-graph we use this:
```python
saver.save(sess, 'my-model', global_step=step, write_meta_graph=False)
```
If you want to keep only 4 latest models and want to save one model after every 2 hours during training you can use max_to_keep and keep_checkpoint_every_n_hours like this.
```python
#saves a model every 2 hours and maximum 4 latest models are saved.
saver = tf.train.Saver(max_to_keep=4, keep_checkpoint_every_n_hours=2)
```
**Note, if we don’t specify anything in the tf.train.Saver(), it saves all the variables**. What if, we don’t want to save all the variables and just some of them. We can specify the variables/collections we want to save. While creating the tf.train.Saver instance we pass it a list or a dictionary of variables that we want to save. Let’s look at an example:
```python
import tensorflow as tf
w1 = tf.Variable(tf.random_normal(shape=[2]), name='w1')
w2 = tf.Variable(tf.random_normal(shape=[5]), name='w2')
saver = tf.train.Saver([w1,w2])
sess = tf.Session()
sess.run(tf.global_variables_initializer())
saver.save(sess, 'my_test_model', global_step=1000)
```
This can be used to save specific part of Tensorflow graphs when required.

### <a name="import"></a>Importing a pre-trained model:
If you want to use someone else’s pre-trained model for fine-tuning, there are two things you need to do:

a) Create the network:
You can create the network by writing python code to create each and every layer manually as the original model. However, if you think about it, we had saved the network in .meta file which we can use to recreate the network using tf.train.import() function like this: saver = tf.train.import_meta_graph('my_test_model-1000.meta')

Remember, import_meta_graph appends the network defined in .meta file to the current graph. So, this will create the graph/network for you but we still need to load the value of the parameters that we had trained on this graph.

b) Load the parameters:
We can restore the parameters of the network by calling restore on this saver which is an instance of tf.train.Saver() class.



with tf.Session() as sess:
  new_saver = tf.train.import_meta_graph('my_test_model-1000.meta')
  new_saver.restore(sess, tf.train.latest_checkpoint('./'))
1
2
3
4
 
with tf.Session() as sess:
  new_saver = tf.train.import_meta_graph('my_test_model-1000.meta')
  new_saver.restore(sess, tf.train.latest_checkpoint('./'))
After this, the value of tensors like w1 and w2 has been restored and can be accessed:



with tf.Session() as sess:    
    saver = tf.train.import_meta_graph('my-model-1000.meta')
    saver.restore(sess,tf.train.latest_checkpoint('./'))
    print(sess.run('w1:0'))
##Model has been restored. Above statement will print the saved value of w1.
1
2
3
4
5
6
 
with tf.Session() as sess:    
    saver = tf.train.import_meta_graph('my-model-1000.meta')
    saver.restore(sess,tf.train.latest_checkpoint('./'))
    print(sess.run('w1:0'))
##Model has been restored. Above statement will print the saved value of w1.
So, now you have understood how saving and importing works for a Tensorflow model. In the next section, I have described a practical usage of above to load any pre-trained model.
