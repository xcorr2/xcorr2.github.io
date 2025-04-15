---
layout: post
title: "test"
date: 2025-04-14
excerpt: GPU v CPU, and how does batch size effect time to train a model?
---

Fastai proved many things, one of them being that you don't need high end computing power and an all nighter in a computer lab to perform deep learning. The deep-learning library allows even a low level laptop to perform some form of image processing. 
But that doesn't mean we can't give it a nudge. That same low level laptop would likely utilises a CPU. It does the job, functioning as the brains of the laptop but is very linear. Processes occur in sequential order. 

# The good stuff
GPU can handle the same operations as a CPU but can do so in parallel. No more are the days of singlular computations. GPUs can compute several operations at the same time and accelerate processing time dramatically. Fastai gives the capacity to 
achieve image processing on a CPU but doesn't mean the joys of a GPU can't be experienced. 

# But was it a bird though?
A bird recogniser was tested on both a GPU and CPU. It would scrape images of birds and woodland landscapes and try to determine whether each image was a bird or landscape compared to one singular referecne image of each. The results were not surprising. 
The CPU took multiple minutes to train the model while the GPU took less than 30 seconds.  
![Alt text](/assets/images/GPU_time.jpg)
![Alt text](/assets/images/CPU_time.jpg)


 ```tsql
 SELECT *
 FROM sys.tables
 WHERE [name] = 'SomeTable'
 ```
