---
layout: post
title: "Tensorflow Queueing and Threading"
---

- [Working with restored models](#working)   
    
## <a name="thread"></a> Working with restored models
**QueueRunner**: When TensorFlow is reading the input, it needs to maintain multiple queues for it. The queue serves all the workers that are responsible for executing the training step. We use a queue because we want to have the inputs ready for the workers to operate on. If you don't have a queue, you will be blocked on I/O and performance will degrade.

**Coordindator**: This is part of tf.train.Supervisor. It's necessary because you need a controller to maintain the set of threads (know when main thread should terminate, request stopping of sub-threads, etc).
