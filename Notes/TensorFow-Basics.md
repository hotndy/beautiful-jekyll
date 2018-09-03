---
layout: post
title: "Tensorflow Basics"
---

- [Saving and restoration of Tensorflow Models - ckpt](#ckpt)  

## <a name="ckpt"></a> Saving and restoration of Tensorflow Models - ckpt

Tensorflow model primarily contains the network design or graph and values of the network parameters that we have trained. Hence, Tensorflow model has two main files:  
* **Meta graph**: This is a protocol buffer which saves the complete Tensorflow graph; i.e. all variables, operations, collections etc. This file has .meta extension.  
* **Checkpoint file**: This is a binary file which contains all the values of the weights, biases, gradients and all the other variables saved. This file has an extension .ckpt. However, Tensorflow has changed this from version 0.11. Now, instead of single .ckpt file, we have two files:  
> mymodel.data-00000-of-00001
> mymodel.index  

Along with this, Tensorflow also has a file named _checkpoint_ which simply keeps a record of latest checkpoint files saved.
