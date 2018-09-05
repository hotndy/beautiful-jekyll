---
layout: page
title: "Tensorflow-Datasets and piplines"
---

[](#top)
- [The TensorFlow Dataset framework – main components](#main)

Consuming data efficiently becomes really paramount to training performance in deep learning. This is an important topic which isn’t covered very well in most TensorFlow tutorials – rather, these tutorials will often use the `feed_dict` and `placeholder` method of feeding data into the model. This method of feeding data into your network in TensorFlow is inefficient and will likely slow down your training for large, realistic datasets. Why is this framework better than the `feed_dict` method that is so commonly used? Simply, all of the operations to transform data and feed it into the model which can be performed with the Dataset API i.e. reading the data from arrays and files, transforming it, shuffling it etc. can all be automatically optimized and paralleled to provide efficient consumption of data.  

## <a name="main"></a> The TensorFlow Dataset framework – main components
The TensorFlow Dataset framework has two main components:
- The **Dataset**  
- An associated **Iterator**  
The **Dataset** is basically where the data resides. This data can be loaded in from a number of sources – existing tensors, numpy arrays and numpy files, the `TFRecord` format and direct from text files. Once you’ve loaded the data into the Dataset object, you can string together various operations to apply to the data, these include operations such as:  
- `batch()` – this allows you to consume the data from your TensorFlow Dataset in batches  
- `map()` – this allows you to transform the data using lambda statements applied to each element    
- `zip()` – this allows you to zip together different Dataset objects into a new Dataset, in a similar way to the Python zip function
- `filter()` – this allows you to remove problematic data-points in your data-set, again based on some lambda function  
- `repeat()` – this operation restricts the number of times data is consumed from the Dataset before a tf.errors.OutOfRangeError error is thrown  
- `shuffle()` – this operation shuffles the data in the Dataset  
There are many other methods that the Dataset API includes. The next component in the TensorFlow Dataset framework is the **Iterator**. This creates operations which can be called during the training, validation and/or testing of your model in TensorFlow.

