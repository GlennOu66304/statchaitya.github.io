---
title: "Tensorflow: What, Why and Where?"
date: 2018-04-05
tags: [Artificial Intelligence]
excerpt: "Neural networks, AI, Scalability"
author_profile: false
read_time: false
---

# <center> TensorFlow - What, Why and Where? </center>

Most, if not all Data Scientists, have hit a phase of stagnancy when it comes to writing Data Science Code. We have repetitively trained, tested and inferred thousands of models locally, coding them in R and Python. It is inevitable that at some point or the other, the need for prototyping using scalable technologies will increase. Enter the world of **Spark** and **TensorFlow**, two scalable technologies for creating machine learning models in the era of Big Data. While **Spark** has found popularity in developing traditional ML systems due to its intuitive syntax, **TensorFlow** is used to develop large scale deep learning systems because it leverages array like structures (tensors).

This post looks at What TensorFlow is, Why is it effective and What are a few business use cases of it.

## <center> What is TensorFlow? </center>

TensorFlow is an open-source software library which is used to run deep learning experiments. It was developed by Google Brain team for internal Google use.

## <center> Why TensorFlow? </center>

Because *it is opensource*

Because *it is Scalable/Distributed and also runs on mobiles*

* TensorFlow is a suite of software tools including a very strong Python API which enables data scientists to **create models
in a local Python environment and scale them using the same locally developed code. Cool isn't it?**. TensorFlow can run on
*clusters* as well as on *multiple CPUs/GPUs on the same machine* as well as runs on *mobiles* which makes it flexible. The scalability is a result of **TensorFlow's programming paradigm in which problems are modelled as graphs** which leads to massively parallel operations.

Because *it comes with additional support tools*

* 'tensorflow' programming language is a part of a 'Suite of Software' which is made available to us. In tensorflow, all elements of code are nodes and edges of a graph. When the project gets complicated i.e. the graph gets complicated, we can use **TensorBoard** to visualize the graph and hence visualize the workings of our code. It is a very useful debugging tool.
* The main advantage of tensorflow is that we can easily scale and productionalize our locally developed code. Another tensorflow suite tool called as **TensorFlow Serving** lets us do this in a very straightforward way.
* So combining these multiple tools along with the **Strong Python API**, tensorflow becomes a very powerful framework for building Deep Learning Neural Networks.

## <center> Where is tensorflow used? </center>

TensorFlow has and will continue to find use cases as we progress in the era of Deep Learning and Big Data. Following is a summary of some interesting projects where TensorFlow is put to use



1. **Language Understanding**
* Smart Systems are only going to get smarter as the years go on. Every year new breakthroughs are happening in the fields like AI and IoT. It is not hard to believe that smart assistants might very soon become an essential part of our lives like Cell Phones.
* TensorFlow finds usecases in Voice Recognition, speech-to-text and language modelling problems which in a combined way contribute to Language Understanding of smart systems.



2. **Image Recognition**
* The most explored and effective usecase of Deep Learning is Image Recognition.
* Applications like face recognition, image search, motion detection, machine vision and photo clustering can be developed using TensorFlow.



3. **Text-based applications**
* Text-based applications is another extensive area where deep learning is used and is very effective.
* Applications for as Sentiment Analysis, threat detection from comments, fraud detection from comments, language detection and text summarization can be developed using TensorFlow.





In the next article we will explore the basic functionality of TensorFlow's Python API, its computational graph model as well as strategies on how to intuitively think about TensorFlow's computational graph model and get comfortable with it.
