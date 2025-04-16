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
![Alt text](./assets/images/CPU_time.png)
![Alt text](/assets/images/CPU_time.png)

This wasn't the only thing that could be done to speed up processing time however.

# Batch Maker
To train a model a data loader is made. This object contains the images to be used for training as well as a validation set of images which is used to be compared agaisnt to check the accuracy of the model. When processing the data set the model goes thorugh an epoch, which is one full rotation through each image. If there are 10 images in a data set then one epoch is 10 images processed. In the example code 3 epochs are completed. But not all 10 images are going to be inspected at once. A batch is a subset of data that the model processes first then adjusts its internal weighting to better match the images it sees. A batch size of 1 would mean that for a set of 10 images, in one epoch, 10 checks and reweighting occurs. 
 ```tsql
dls = DataBlock(
    blocks=(ImageBlock, CategoryBlock), 
    get_items=get_image_files, 
    splitter=RandomSplitter(valid_pct=0.2, seed=42),
    get_y=parent_label,
    item_tfms=[Resize(192, method='squish')]
).dataloaders(path, bs=64)
 ```

Now back to making this program faster. Increasing batch size would mean decreasing the number of stops for weighting and make image processing faster. And that is what I did. Starting with a batch size of 16, the batches were continously doubled to 256. To start the speed increased. Processing time was down and everything was good. But then an interesting relationship was observed. As batch size incrceased, error rate follow suit. Proceeeding the training of the model was fine tuning to improve the accuracy. And as the model got less accurate, ore time was spent fine tuning until increasing batch size past 64 lead to increases in training time. 
