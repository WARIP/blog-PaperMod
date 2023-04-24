---
title: "Embedding sequences of symbols in a smooth manifold"
date: 21-04-2023
# weight: 1
# aliases: ["/first"]
tags: ["draft","math-thoughts"]
author: ["Me"]
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Thinking of representing text-like data in a smooth manifold"
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

We can look at $S^\mathbb{N}$, the set of all sequences of symbols from some set of symbols $S$.
Each element could represent a knowledge of some kind, e.g. text.
Our main motivation here is to embed the (metric) space of sequences inside a Riemannian manifold, preserving the distances (hence finding an isometry). A use for that would be to allow learning through gradients on this manifold. Also, it is just interesting to think about it.
We would like to look at the metric which give a smaller distance to sequences which are the same up to a point. Therefore, we may look at the metric space $X = S^\mathbb{N}$ and $d((x_k),(y_k)) = 2^{-min(l:x_l \neq y_l)}$. It is a complete metric space.
If $|S| = 2$, it is actually homeomorphic to the cantor set, but the homeomorphism doesn't preserve distances.
Probably there is no such an isometry, because of the following argument. Let us denote by $[a_1,...,a_k]$ the set of all sequences containing $a_1,...,a_k$ as their first symbols. Then, for any $\gamma \in [0]$, $[1] \subseteq S(\gamma,1)$, and in the same way, for any $\rho \in [1]$, $[0] \subseteq S(\rho, 1)$. This already sounds a little bit "fishy"- infinitely many spheres intersection contains the same half-full-measure set. Morevoer, it should be proben but they probably intersect transversely, which implies that the intersection should lower the dimension of the manifold (looking at each such sphere as a manifold).

<!-- What is nice is that we can embed it quite natuarlly in a manifold.
If $|S| = 1$, then we have $|X| = 1$, which can be viewed as a $0$-dimensional manifold (which is not very interesting).
If $|S| = 2$, then we can see that $(X,d)$ is homeomorphic to the interval $I = [0,1]$ with the eucllidean metric, therefore it can be viewed as a $1$-dimensional Riemannian manifold.
And what about $|S| = 3$? Continuing the pattern, we would like to embed it in a $2$-dimensional manifold. And it appears like we can do it- Look at the Sierpinski triangle, and encode each point in it with a sequence of numbers from $0,1,2$, where each digit represents the proximity to some outer vertex of the traingle, at each resolution. Here is the first time we see that it is only embedded in a mnifold but not a manifold in itself. A short explanation for why isn't it a manifold, is that its hausdorr dimension is not 2.
In general, denoting $|S| = n$, we can embed it inside a "Sierpinski triangle"-like set, created in the same manner as a Sierpinski traingle but with $n$ vertices, which is embedded in $\mathbb{R}^{n-1}$. -->



