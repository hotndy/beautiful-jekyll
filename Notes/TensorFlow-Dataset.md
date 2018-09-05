---
layout: page
title: "Tensorflow-Datasets and piplines"
---

[](#top)

Consuming data efficiently becomes really paramount to training performance in deep learning. In a previous post I discussed the TensorFlow data queuing framework. However, TensorFlow development is always on the move and they have now created a more streamlined and efficient way of setting up data input pipelines. This TensorFlow Dataset tutorial will show you how to use this Dataset framework to enable you to produce highly efficient input data pipelines. This is an important topic which isn’t covered very well in most TensorFlow tutorials – rather, these tutorials will often use the feed_dict and placeholder method of feeding data into the model. This method of feeding data into your network in TensorFlow is inefficient and will likely slow down your training for large, realistic datasets – see a discussion about this on the TensorFlow website. Why is this framework better than the feed_dict method that is so commonly used? Simply, all of the operations to transform data and feed it into the model which can be performed with the Dataset API i.e. reading the data from arrays and files, transforming it, shuffling it etc. can all be automatically optimized and paralleled to provide efficient consumption of data.

In this TensorFlow Dataset tutorial, I will show you how to use the framework with some simple examples, and finally show you how to consume the scikit-learn MNIST dataset to create an MNIST classifier. As always, the code for this tutorial can be found on this site’s Github repository.
