---
layout: page
title:  "Neural Networks (part 2)"
date:   2019-10-10 12:00:00 -0400
categories: blog
mathjax: true
comments: true
---
<p>
So in my previous post we used a rather longwinded analogy to arrive at a function that given binary inputs could make a simple yes or no decision based on the importance of each input to the overall thought process. I called this function a perceptron, a type of artificial neuron.

<span class="image center"><img src="/assets/perceptron.png" alt="" /></span>

This perceptron takes in 3 inputs, x1, x2, x3 and computes the output based on the weights provided, w1, w2, and w3. The output of the perceptron is dependent on the sum of the products of each input Xn and its weight Wn. If the sum is greater than a threshold value, then the perceptron outputs 1. Otherwise, if the sum is less than that threshold, the perceptron outputs 0.

$$\begin{array}{cc}
  \{ & 
    \begin{array}{cc}
      output = 1 & \text{if sum of} & x_{n}w_{n} = x_{1}w_{1} + x_{2}w_{2} + x_{3}w_{3} +... > \text{threshold} \\
      output = 0 & \text{if sum of} & x_{n}w_{n} = x_{1}w_{1} + x_{2}w_{2} + x_{3}w_{3} +... <= \text{threshold}\\
    \end{array}
\end{array}$$

The dot dot dots are great and all, but this isn't a very concise definition of the perceptron's decision making, so let's use vector notation to simplify the expression a little bit.

Let x = [x1, x2, x3] be the input vector and w = [w1, w2, w3] be our weight vector.

$$\begin{array}{cc}
  \{ & 
    \begin{array}{cc}
      output = 1 & if & x.w > threshold \\
      output = 0 & if & x.w <= threshold \\
    \end{array}
\end{array}$$

One conclusion that we can draw from this model of a perceptron is that the decision made depends heavily on the magnitude of the threshold value. The larger the threshold, the more biased our decision becomes towards either 1 or 0. In fact, that's what the threshold is commonly known as, the bias of the perceptron. Let's rearrange the equations above a little more:

$$\begin{array}{cc}
  \{ & 
    \begin{array}{cc}
      output = 1 & if & x.w - b > 0 \\
      output = 0 & if & x.w -b <= 0 \\
    \end{array}
\end{array}$$

So how powerful is a perceptron, exactly? 
<br><br>
To answer this question, we need to discuss a concept called a NAND gate. I'll go in depth in a future blog post, but the basics are as follows: in Boolean logic, there is an operator called NAND. It takes in 2 binary inputs, and only returns false if both inputs are true; it's the complement of AND. What's very cool about NAND is that every other function in Boolean logic can be represented using combinations of NAND gates; this is called functional completeness. Any computation can be represented as a series of NANDs. Furthermore, a NAND gate can be modeled using a perceptron.

<span class="image center"><img src="/assets/NANDperceptron.png" alt="" /></span>

If you examine this perceptron, it will only return 0, or false, if both x and y are equal to 1, or true. Otherwise the perceptron will always output 1, or true. This is exactly the definition of an NAND gate. If anything a computer can do can be represented by a series of NANDs, and NAND gates can be modelled by a perceptron, that leads us to the realization that a combination of perceptrons can handle any computation that a computer can accomplish! That's really powerful, but simultaneously not that powerful, because that doesn't get us any closer to making a computer make intelligent decisions.

<span class="image center"><img src="/assets/network.png" alt="" /></span>

Here we have a network of perceptrons. If we have accepted the basic premise that perceptrons can take evidence and weigh it up to arrive at decisions, it makes sense that a group of such neurons could make more complex decisions with more factors. Generally, networks of perceptrons contain a series of layers, each layer having a different set of perceptrons with their own biases and weights. In this example, the network has 3 layers; the first column is the input layer, the last column is the output layer, and everything in between are called hidden layers. 
<br><br>
What makes a neural network tick is that we can train networks to figure out what weights result in the greatest number of correct classifications, making slight adjustments to fine-tune our model. I'll talk about machine learning algorithms like these in a future post as well.
</p>