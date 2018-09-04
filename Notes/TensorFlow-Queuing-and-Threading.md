---
layout: post
title: "Tensorflow Queueing and Threading"
---

- [TensorFlow queuing and threads – introductory concepts](#intro)   
    
One of the great things about TensorFlow is its ability to **handle multiple threads and therefore allow asynchronous operations**.  If we have large datasets this can significantly speed up the training process of our models. This functionality is especially handy when reading, pre-processing and extracting in mini-batches our training data.   

The particular queuing operations/objects we will be looking at are FIFOQueue, RandomShuffleQueue, QueueRunner, Coordinator, string_input_producer and shuffle_batch, but the concepts that I will introduce are common to the multitude of queuing and threading operations available in TensorFlow.
 
## <a name="intro"></a> TensorFlow queuing and threads – introductory concepts
We know from our common day experience that certain tasks can be performed in parallel, and when we do such tasks in parallel we can get great reductions in the time it takes to complete complex tasks.  The same is true in computing – often our CPU will get stuck waiting for the completion of a single task, such as waiting to read in data from a file or database, and it blocks any other tasks from occurring in the program.  Needless to say, this impacts performance and doesn’t utilize our CPUs effectively.

These types of issues are tackled in computing by using threading.  Threading involves multiple tasks running asynchronously – that is when one thread is blocked another thread gets to run.  When we have multiple CPUs, we can also have multi-threading which allows different threads to run at the same time.  Unfortunately, threading is notoriously difficult to manage, especially in Python.  Thankfully, TensorFlow has come to the rescue and provided us means of including threading in our input data processing.

In fact, TensorFlow has released a performance guide which specifically recommends the use of threading when inputting data to our training processes.  Their method of threading is called Queuing.  Often when you read introductory tutorials on TensorFlow (mine included), you won’t hear about TensorFlow queuing.  Instead, you’ll see the following feed_dict syntax as the method of feeding data into the training graph:

sess.run(train_step, feed_dict={x: batch_xs, y_: batch_ys})
Here data is fed into the final training operation via the feed_dict argument.  TensorFlow, in its performance guide, specifically discourages the use of the feed_dict method.  It’s great for tutorials if you want to focus on core TensorFlow functionality, but not so good for overall performance.  This tutorial will introduce you to the concept of TensorFlow queuing.

What are TensorFlow queues exactly?  They are data storage objects which can be loaded and de-loaded with information asynchronously using threads.  This allows us to stream data into our training algorithms more seamlessly, as loading and de-loading of data can be performed at the same time (or when one thread is blocking) – with our queue being “topped up” when required with new data to ensure a steady stream of data.  This process will be shown more fully below, as I introduce different TensorFlow queuing concepts.

The first TensorFlow queue that I will introduce is the first-in, first-out queue called FIFOQueue. 
 
       
    
    
## <a name="thread"></a> Working with restored models
**QueueRunner**: When TensorFlow is reading the input, it needs to maintain multiple queues for it. The queue serves all the workers that are responsible for executing the training step. We use a queue because we want to have the inputs ready for the workers to operate on. If you don't have a queue, you will be blocked on I/O and performance will degrade.

**Coordindator**: This is part of tf.train.Supervisor. It's necessary because you need a controller to maintain the set of threads (know when main thread should terminate, request stopping of sub-threads, etc).
