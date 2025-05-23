---
layout: post
title: Understanding Machine Learning
category: Computer Science
date: 2024-04-05
---

What is even learning? Learning is applying past and current experience and using it to make and informed prediction about some information we do not already know. For example, human learn how to answers questions on the final exam, or predict how crabby we will feel after staying up all night, or learn when they've had too much to drink.<!-- more -->

#### Rats vs Pigeons

To help us characterize learning, let's see some real world examples. Rats exhibit **bait shyness**, a trait that lets rats learn to avoid poisonous foods. Given food of a new look or smell, rats eat will eat in very small quantities. If they experience sickness, they stop eating it. They learn to associate the sickness with the look and smell of the food. Learning is very useful for survival.

We contrast this against the pigeon. In an experiment by B.F. Skinner, pigeons were fed at variable times independent of the behavior of the pigeons. But somehow the pigeons started repeating the same action (pecking or turning their head) over and over again. We'll call this **pigeon superstition**. The pigeons learned a nonsensical association between their behavior and receiving food.  Now, learning is just wasting energy. 

#### Generalization & Inductive Bias

When is learning useful and when it is useless? Let's define some terms. **Generalization** is how well we make the right prediction in the real world based on past and current experiences. **Inductive bias** are the assumptions we make on how we make the prediction (i.e. what's the algorithm we follow).

The rats try to predict what food is poisonous or not. The pigeons try to predict what action brings food. We see that the rat's bait shyness generalizes better than the pigeon's superstitions. So what biological mechanisms let this happen? If we revisit the rats, repeating the experiment replacing poison for electrical shocks, the rats don't learn at all which foods lead to electrical shocks. There's biological instinct that tells the rats to only focus on the nauseous feelings, and in this case, nature is right. In contrast, the pigeons do not have such a biological instinct and confuse pecking and turning with receiving food. So the rats have a high inductive bias.

|              |  **inductive bias** | **generalization** |
| **rats**     |        high         |        good        |
| **pigeons**  |        low          |        bad         |

It is not always the case generalization positively correlates with inductive bias. For example, if the rats snuck into someone's house and started eating their food, the home owners might find out and exterminate the rats. The rat's bait shyness was not enough to generalize to human kitchens.

And, for example, if the pigeons were being fed by a machine that rewarded them for repeatedly pecking or nodding, then the pigeons would be generalizing well.

#### Machine Learning

Why do we need a machine to learn? We are interested in automating tasks that humans would normally do. For example, answer general questions, flag spam emails, and read the text captured in a photo. We are also interested in doing tasks that humans can't do easily. For example, generating videos and images from prompts, detecting anomalies in big data, predicting how different proteins fold. 

There are many paradigms for machine learning. Today, we will study what's known as **supervised statistical batch learning with a passive learner**. That means the learner is given a training dataset of past inputs and results, and then must predict given new inputs. While we have observed a relationship between bias and BLANK, how do we know this holds in general? When does a model overfit or underfit? To talk about this we need some formal system of mathematics on ML to talk about.

#### A Formal Setting with Papayas

We are stranded on a tropical island where papayas are regularly eaten. We've never seen a papaya before, so we are not sure how to tell if a papaya is yummy or not. We decide that we will judge the yumminess based on the color, which ranges from dark green to orange, red and dark brown, and the softness ranging from solid to mushy. We buy a sample of papayas from the market to try out. Our goal is to learn what makes a yummy papaya in this market. Our first step is to come up with a formal model for this situation.

First, let's call the features of papaya $$i$$ the **input features** $$\vec x_i=(x_{\mathsf{color}}, x_{\mathsf{softness}})$$. Say we can measure softness and color over the range over $$[0,1]$$. We call the **feature space** $$\mathcal{X} \triangleq [0,1]^2$$. So $$\vec x_i \in \mathcal{X}$$. We may model $$\mathcal X$$ as a unit square and $$\vec x_i$$ is  point in the square. We can also use papaya $$i$$ and $$\vec x_i$$ interchangeably.

Let's call the papaya $$i$$'s yumminess the **label** $$y_i$$ where $$y_i=1$$ if it is yummy and $$y_i=-1$$ if it is not. We call the **label space** $$\mathcal Y\triangleq \{\pm 1\}$$, and $$y_i\in\mathcal Y$$.

Say we have $$m$$ papayas. Our small sample of papayas is our **training set** $$D\triangleq ((\vec x_1,y_1),\ldots (\vec x_m, y_m))$$. 

Suppose we have a learning algorithm $$A$$. Given $$D$$, it outputs a **hypothesis** $$h:\mathcal X\to\mathcal Y$$, a function that is able to predict if a papaya is yummy based on its color and softness. We denote $$h\triangleq A(D)$$. We say $$h\in \mathcal H$$ for some **hypothesis space** $$\mathcal H$$ which we will not worry about right now.

Finally, we need a way for evaluate if $$h$$ predicts yumminess well. We use a **loss function** $$L: \mathcal Y\times  \mathcal Y \to [0,1]$$ where $$L(\hat y, y)=0$$ if $$\hat y= y$$ and $$L(\hat y, y)=1$$ if $$\hat y\neq y$$. This loss function detects mismatches between the predicted label $$\hat y$$  and the true label $$y$$. To obtain the loss of a hypothesis $$h$$ over a set $$S=((\vec x_1,y_1),\ldots,(\vec x_n,y_n))$$, we define the **empirical loss of $$h$$ over $$S$$**:

$$
\begin{gather*}
    L_{h}(\vec x, y) \triangleq L(h(\vec x), y) \\
    L_{h}(S) \triangleq \frac{1}{n} \sum_{i=1}^n L(h(\vec x_i), y_i).
\end{gather*}
$$

Notice the empirical loss counts the proportion of misclassifications $$h$$ has on $$S$$. We can define the **training loss** $$L_h(D)$$. But how do know if $$h$$ generalizes well? We can define the **generalization loss** too. If $$\mathbb D$$ is the set of all papayas in the market, we have $$L_h(\mathbb D)$$. 

#### Learning with Axis-Aligned Papayas

While our initial definition that learning strives to minimize $$L_h(\mathbb D)$$, we need to get more precise. Let's investigate this by attempting to characterize a concrete setting. Suppose there are infinitely many papayas and that $$\mathbb D$$ is a uniform distribution over $$[0,1]^2$$. Further, suppose the yummy papayas are exactly the centered square of area $$\frac{1}{2}$$ as depicted below.

INSERT IMAGE

Since the yummy papayas form a rectangle, let's create a learner that returns a rectangular hypothesis. We restrict $$\mathcal H_{\mathsf{rect}}$$ to the set of axis-aligned rectangular classifiers, that is if $$h\in\mathcal H_{\mathsf{rect}}$$ there is a rectangle $$R$$ in $$[0,1]^2$$ for which

$$
\begin{gather*}
    h(\vec x) = \begin{cases}+1 & x \in R \\ -1 & x\notin R\end{cases}.
\end{gather*}
$$

Let's try to see how we would implement an algorithm $$A_{\mathsf{rect}}$$ that tries to find an $$h\in\mathcal H_{\mathsf{rect}}$$ that generalizes well. Given $$D$$ as input, we draw the smallest rectangle around all the yummy papayas in $$D$$. We can see that it's possible to code up this algorithm. What's the problem?

This algorithm, $$A_{\mathsf{rect}}$$ does not always work. With some non-zero probability, $$D$$ could be not even close to looking uniform. Suppose that all the yummy and non-yummy papayas are clumped in $$\alpha\times\alpha$$ squares for small $$\alpha>0$$. Then we would draw an $$\alpha\times\alpha$$ square around the yummy papayas, and $$L_h(D)=0$$ while $$L_h(\mathbb D) = 0.5 - \alpha^2\approx 0.5$$.

To combat this, we can increase the size of the dataset, but the above can still happen with very small probability. We need to adjust our success parameters to say that we achieve good generalization _on average_. One way to enforce this is to introduce a small **confidence parameter** $$\delta>0$$ where we want $$A_{\mathsf{rect}}$$ to return an $$h\in \mathcal H_{\mathsf{rect}}$$ that minimizes the generalization loss with probability at least $$1-\delta$$. So $$L_{h}(\mathcal D)=0$$ with probability $$1-\delta$$. 

While we know that there exists an axis-aligned rectangle that achieves $$0$$ generalization loss, can our algorithm actually find it? If $$D$$ has a vague decision boundary, this will be impossible. To account for this, we add a small **error parameter** $$\varepsilon>0$$ where we want $$L_h(\mathbb D) \leq \varepsilon$$.

We can make this slightly more general. For axis-aligned rectangles, there exists an $$h\in\mathcal H_{\mathsf{rect}}$$ which achieves $$0$$ generalization loss. In general, this may not be the case. (e.g. we take a circle hypothesis space.) If no hypothesis perfectly generalizes, then no matter what's our algorithm, the outputted hypothesis will have loss lower bounded by $$\min_{h\in\mathcal H} L_h(\mathbb D)$$ which is greater than $$0$$. Now our approximation error guarantee fits $$L_h(\mathcal D) \leq \min_{h\in\mathcal H} L_h(\mathbb D) + \varepsilon$$. 

We can now state the proper definition of learning. **Probably approximately correct learning** (PAC learning) is defined as follows. An algorithm $$A$$ is an $$(\varepsilon,\delta)$$-PAC learner if over the randomness of selecting $$D\subseteq\mathbb D$$ of size $$m$$ and $$h=A_{\mathsf{rect}}(D)$$, then $$L_h(\mathbb D) \leq \varepsilon$$ with probability at least $$1-\delta$$.

Finally, recall that $$m$$ needs to be sufficiently large so $$D$$ is representative of $$\mathbb D$$. We call $$m(\varepsilon, \delta)$$ the **sample complexity** if it is the smallest size of $$D$$ to maintain $$(\varepsilon,\delta)$$-PAC learning.

#### Analyzing Axis-Aligned Papayas

For what sample complexity is $$A_{\mathsf{rect}}$$ an $$(\varepsilon, \delta)$$-PAC learner? In particular, I'm interested when $$\varepsilon=0.01$$ and $$\delta=0.1$$ so we can produce a hypothesis that only misclassifies $$1\%$$ in general with relative good confidence. We can estimate sample complexities with a simulation. We find the minimum number of samples we need to take to obtain confidence $$\delta$$ and error $$\varepsilon$$:

| $$\varepsilon$$ | $$\delta$$  | $$m(\varepsilon,\delta)$$ | $$\frac{\sqrt{2}\ln(11/\delta)}{\varepsilon}$$ |
| $$0.1$$         | $$0.1$$     | $$63$$                    | $$67$$       |
| $$0.01$$        | $$0.1$$     | $$667$$                    | $$663$$       |
| $$0.1$$         | $$0.01$$    | $$96$$                    | $$100$$       |
| $$1/3$$         | $$1/3$$    | $$12$$                    | $$15$$       |

Sample complexity scales inversely with $$\varepsilon$$ and logarithmically with $$1/\delta$$. In other words, if we want to scale the failure probability down, we only need to add a little bit more data. And if we want to scale the approximation error down, we need to scale the amount of data up by the same amount. So is that the solution? Just add more data?

#### When axis-aligned rectangles don't work

It was obvious to us that an axis-aligned rectangle was the right shape for the decision boundary, but when does it fail? We've already identified if $$m$$ is too small, the rectangle it finds will be too small. We can also consider if the $$\mathbb D$$ has a different decision boundary. Suppose it is a diamond of area $$1/2$$. Then we won't be able to get close to $$0$$ generalization error with an axis-aligned rectangle. Maybe $$\min_{h\in\mathcal H_{\mathsf{rect}}} L_{h}(\mathbb D_{\mathsf{diam}})=0.25$$. This is called underfitting. It's when the learner can't generalize well. To combat underfitting, we can do the following:

1. Add more training samples. We need a sufficient size to be representative of $$\mathbb D$$.
2. Decrease inductive bias by expanding the hypothesis class. We could consider rotated rectangles which we would get a similar (slightly worse) guarantee as the original problem.
3. Add more features to each papaya. Color and softness may not be enough, maybe we need to factor in smell to properly determine a papaya's yumminess.

All good things in moderation. It can be expensive to expand the training set: it costs money to buy papayas. 

If we add on too many features, the learner may find nonsensical relationships in the training data which don't generalize well. This is known as the **curse of dimensionality**. 

If we expand the hypothesis class too much, we may find hypotheses that have low training loss but high generalization loss. For example, let us expand $$\mathcal H$$ to the set of all functions from $$[0,1]^2$$ to $$\{\pm 1\}$$. Let $$h_D$$ be the hypothesis that memorizes $$D$$. That is,

$$
h_D(\vec x) = \begin{cases}+1 & (\vec x, +1)\in D \\ -1 & (\vec x, -1)\in D \\ -1 & \text{otherwise}\end{cases}.
$$

So $$L_{h_D}(D)=0$$. However, on infinite market $$\mathbb D$$, $$h_D$$ will only correctly classify the $$m$$ papayas in $$D$$ and all of the non-yummy papayas. So $$L_{h_D}(\mathbb D)=0.5$$. You might as well flip a random coin.

This phenomenon is called **overfitting**. This is when the model memorizes the training set too well, and so does not generalize well. This happens when the model has low inductive bias, a small amount of training data, or too many features. To combat overfitting, we can do the following:

1. Increase the size of $$D$$. If $$D$$ contained a quarter of all papayas, then the memorizer can do as good as $$L_h(\mathcal D) = 0.25$$.
2. Reduce the number of features. Keep the most important ones.
2. Restrict the hypothesis class $$\mathcal H$$. We should go back to axis-aligned rectangles or similar.

Again, everything in moderation. It can be expensive to collect more data. Remove too many features and our learner might not have enough information to make an informed prediction. And restrict the hypothesis class too much, it will be hard to find hypotheses that fit complex distributions.

#### Bias-Variance Tradeoff

Let's recap what we know so far. 

|                   |  **inductive bias**   | **\# training data** | **\# features**   | **generalization**    |  **training loss**   |
| **overfitting**   |         low           | small             | many               |    bad               |  good                 |
| **underfitting**  |        high           | big               | few               |    bad               |  bad                  |
| **just right**    |          medium       |  not too small              | sufficient               |   good               |  either               |

Let's finish what we started. For convienence, let $$L_{\mathcal H}(\mathbb D)\triangleq  \min_{h'\in\mathcal H} L_{h'}(\mathbb D)$$. For each hypothesis $$h\in\mathcal H$$, we can decompose the loss as 

$$
L_h(\mathbb D) =L_{\mathcal H}(\mathbb D) + \varepsilon_{\mathsf{approx}}
$$

for some approximation error $$\varepsilon_{\mathsf{approx}} \geq 0$$. With PAC learning, we characterize that the learner achieves some small error with high probability. A different way to characterize the learner is to look at the average generalization loss over randomness in training sets $$D$$. Let's interpret the equation above over the randomness of $$D$$.

We call $$L_{\mathcal H}(\mathbb D)$$ the **bias**. It's the absolute best that the learner can do given $$\mathcal H$$. Bias increases the more restricted and simple $$\mathcal H$$ is.

We call $$\varepsilon_{\mathsf{approx}}$$ the **variance**. This is the approximation error introduced by running $$A$$ on different datasets. When bias is low, variance is high. When $$\mathcal H$$ is complex, the optimal hypothesis might be extremely hard to find, so due to computational resources the learner must settle for worse approximation errors. Also, variance is high when the datasets are too small. Even if someone had unlimited computational power, they wouldn't have enough information about $$\mathbb D$$ to get close to optimal.

When bias is high, variance is low. When we make strong inductive biases on what our hypothesis looks like, it necessarily reduces the variation in output. This is known as the **bias-variance tradeoff**. We can model this as graphs of over hypothesis class complexity and number of training samples.

INSERT IMAGE OF LOSS OVER COMPLEXITY OF H and TRAINING SAMPLES


#### What is happening with LLMs.

At the end of 2022, OpenAI released ChatGPT, a **Large-Language Model** (LLM) that can talk like a human, answer complex queries, and basically knows the entire internet. Everyone was amazed. OpenAI gained over 100 million users within 2 months. Now, we even more competitors like Gemini and DeepSeek, and so much other amazing AI technology for image or video generation. 

We are experience the rise of **generative** machine learning. The goal of the generative learner is to learn the distribution $$\mathbb D$$ and generate inputs from that. Instead of trying to predict which papaya is yummy, the learner describes the distribution of yummy or not yummy papayas. This is essential for ChatGPT to generate responses because human language is so complex, we cannot simple label one sentence as the "right response", The right response is a distribution over the right sentences.

So, can we use our new tools of machine learning to break down why ChatGPT is did so well?

The heart of ChatGPT is that it is built out of **transformers**. Transformers allow the words of a sentence to interact with each other in complex ways through an **attention mechanism**. While ML models in the early 2010s had a few million parameters, GPT3 has 175 billion parameters, and GPT4 has 1 trillion parameters allegedly. $$\mathcal H$$ is extremely large and complex. Which mean bias is low.

To get variance low, OpenAI did two things. First thing, OpenAI trained ChatGPT huge datasets that scraped the internet. Hundreds of billions of sentences. With a training set so large, it is possible $$D$$ has enough information for ChatGPT to generalize well. 

Variance can be low if OpenAI can find a way to train the model efficiently. And they did. Transformers take advantage of the power of GPUs which can do thousands of the same simple operations in parallel. In addition, you can split the model to run in parallel over hundreds of GPUs.

With ChatGPT, OpenAI pushed for the best sweet spot in the bias-variance tradeoff. And with enough training data and compute, they actually pulled it off. Only, they technically cheated because they finetuned ChatGPT using human feedback, but that's for another day.

#### Summary
This was an introduction to machine learning. You can start to see how the mathematical formulation can be used to prove things about machine learning. Machine learning is exetremely applicable. We can reason about it both in theory with math and in practice by running scripts. This stuff is useful to explain where current technology is moving and what principles we can use to develop better ML models. 


_**Acknowledgements:** The first half is adapted from Chapters 1 & 2 of [Understanding Machine Learning](https://www.cs.huji.ac.il/~shais/UnderstandingMachineLearning/) by Shai Shalev-Schwartz and Shai Ben-David. Introduction of PAC Learning is inspired from [CS 4850 Probability, Vectors, and Matrices in Computing](https://www.cs.cornell.edu/courses/cs4850/2025sp/). Discussion on BV Tradeoff are adapted from [CS 4780 Introduction to Machine Learning](https://www.cs.cornell.edu/courses/cs4780/2023fa/). Finally, discussion on LLMs is contributed from [CS 4782 Introduction to Deep Learning](https://www.cs.cornell.edu/courses/cs4782/2025sp/) and [Wikipedia](https://en.wikipedia.org/wiki/OpenAI#). This article will be adapted for the corresponding Splash @ Cornell for Spring 2025._

_**Image References:** from x, y, z_