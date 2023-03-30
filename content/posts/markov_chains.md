---
title: "Markov chains, defined in a measure theoretic sense"
date: 28-03-2023
# weight: 1
# aliases: ["/first"]
tags: ["draft","measure-thoery","ergodic-thoery"]
author: "Me"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "We will see a measure theoretic definition of markov chains.
This will prepare us to explore in the following posts (if those will be written) the conditions for ergodicity and weak mixing, with connection to graph theory and applications."
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
rtl: true
math: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/aviro2000/blog-PaperMod/content/posts"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link

---
In general, we may have a sequence of states, one at each time step. We can model this dynamic as being with "short memory" - traversing from some state at time $t$ to another state at time $t+1$ has some probability depending on the first and second state (by that order), without also taking into account the entire history. From this need came the notion of Markov chains. 
We will look more into the properties of markov chains and define this object through the lens of measure theory.

This blog-post is heavily based on chapter 1.5.4 from [Omri Sarig's lectures notes on Ergodic Theory](https://www.weizmann.ac.il/math/sarigo/sites/math.sarigo/files/uploads/ergodicnotes.pdf)- you may check it for better explanations and a rigorous presentation of the material, and on many other aspects of ergodic theory as well.

Let us look at time as discrete ($\mathbb{N}$). We can think of an event/state happening at each time, where the event is one of a finite set of possible events (denoted by $S$). 
A very natural question would be to ask "What is the probability of an event $a \in S$ happening at time $t = t_1$?". But we are interested in more than that- we want also to ask questions like "What is the probability of an event $a \in S$ happening at time $t = t_1$ and an event $b \in S$ happening at time $t = t_2$?".

We can also add the assumption that there is some dynamic of change between states, which does not depend on time. For example, when if there are some physical laws involved, this allows us to learn from current data about the dynamics that happened in the past, and will happen in the future. Mathematically speaking, we would like the answer to the first question presented above to be the same for every $t_1$, and the answer for the second question to depend only on $t_2 - t_1$. 

Now we will translating our wishes to a measure theoretic setting, with defining the set of events, probability measure and the time invariance property mentioned. Later, we will discuss the ergodicty and (strong) mixing properties of this setting.

Our set of states is a finite set $S = [N]$, the *alphabet*. Not every sequence of $2$ states is possible to happen one after the other. This information is encoded in a matrix $A = (s_ij)_{S \times S}$ composed of $0$s and $1$s, which is the *transition matrix*. Looking at $S$ as nodes of a directed graph, and $A$ defines the possible edges.
 ![graph](https://i.imgur.com/KNcGfqi.png)

We consider the set of possible sequences, which can be seen as infinite walks on the graph, or as moving along the time axis from a state to another state, according to the transition matrix $A$, on an infinite graph made of copies of the graph deined by $A$.

![infinite_graph](https://i.imgur.com/VVakMo9.png)

This set of sequences is defined as $\Sigma_A^+ = \lbrace\vec{x} = (x_1,x_2...,) : s_{x_i x_i+1} = 1\rbrace$. 
Now we would like to say what are the "events" for whom we have a probability of happening, where an event is actually a subset of $\Sigma_A^+$.
The events mentioned in the beginning are a kind of events we would like to have, e.g. of the form $\lbrace\vec{x} \in \Sigma_A^+ : x_{t_0} = a\rbrace$ and $\lbrace\vec{x} \in \Sigma_A^+ : x_{t_0} = a, x_{t_1} = b\rbrace$.
We would start by including sets of the form $\lbrace\vec{x} \in \Sigma_A^+ : \forall i \in \[m\]: x_{i} = a_i\rbrace$ for $m \in \mathbb{N}$ a finite set and $\lbrace a_i \rbrace_{i=1}^{m} \subseteq \Sigma_A^+$.
These are called *cylinder* sets, and are denoted shortly by $\[a_0 ... a_j ... a_{m}\]$. 
The cylinder sets will generate our sigma algebra. Actually, it would be very nice if this sigma-algebra was a Borel sigma algebra of some topology on $\Sigma_A^+$. Luckily for us, it is!
This space could be viewed as endowed with the product topology (with the topology on $S$ being the discrete topology). Equivalently, we can view this as the topology of the metric space $\Sigma_A^+$ with the metric $d(\vec{x},\vec{y}) = 2^{-min\lbrace k: x_k \neq y_k\rbrace}$. We will denote this sigma algebra by $\mathcal{B}$.

Now we would like to define the appropriate probability.
Actually using conditional probabilities, we would like to have for the cylinder sets:
$$\mathbb{P}(\[a_1,a_2..,a_m\]) = \mathbb{P}(a_1) \cdot \mathbb{P}(a_2|a_1) \cdot ... \cdot \mathbb{P}(a_m|a_{m-1},...,a_1)$$

We will assume that our process has memory for only 1 timestep, which yields:
$$\mathbb{P}(\[a_1,a_2..,a_m\]) = \mathbb{P}(a_1) \cdot \mathbb{P}(a_2|a_1) \cdot ... \cdot \mathbb{P}(a_m|a_{m-1})$$

Because our the cylinder sets generates the sigma algebra, this formula will allow us to define the probability measure on every set from the sigma algebra. What we need is $\mathbb{P}(a_{j+1}|a_j)$ and $\mathbb{P}(a_j)$ for every $i,j$.l
This will be given to us (together with $S$ and $A$), by a matrix $P$ and a vector $\vec{p}$.
They will satisfy the properties we would like them to satisfy according to $P_{ij} = \mathbb{P}(a_j|a_i)$ and $p_i = \mathbb{P}(a_i)$. 

For $\vec{p}$ we would like to have:

- $\sum_{i \in S} p_i = 1$
- $p_i \geq 0$ for every $i \in S$

Such a vector $\vec{p}$ is called a *probability vector*.

For $P$ we would like to have:
- $P_{ij} \geq 0$ for every $i,j \in S$
- Compatibility with $A$- $A_{ij} = 0 \implies P_{ij} = 0$ for every $i,j \in S$
- $\sum_j P_{ij} = 1$ for every $i \in S$ ($\sum_{j \in S}\mathbb{P}(i|j) = 1$)




