---
title: "thinking about the optimal economy"
date: 05-02-2023
# weight: 1
# aliases: ["/first"]
tags: ["draft","thoughts"]
author: "Me"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "We will the optimal economy in an abstract setting, with examples"
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
We are people, with needs. Each one can act as he (or his biological circuits) wishes, based on some dynamic. I am a person, also with some needs, and I would wish that other people actions will be aligned with my needs. Moreover, we can include also programmable agents into the discussion. So what are exactly my needs? And even given some vague sense of them (and taking into account the whole uncertainty that concerns them), how do I have them aligned as possible?
First of all, given that other people could be similar to me in this way of thinking (even without these specific verbalization), each one would like this same thing. Now there is a question of comparing. A For each person, two ways/mechanisms can be compared in some specific time. It is also very likely that there is a partial order- not every two mechanisms are comparable. But we would wish that relative to any person, for any mechanism there is a mechanism which is comparable and better for that person. So each person has a sequence of states $s = (s_t)_t \in \Omega^T$ ($T$ discrete), and let's say that there is some "utility/hapiness" function $h:\Omega \to \mathbb{R}$, so we may say that $s \leq s^*$ if there is a 1-1 map $\sigma: T \to T$ such that for any $t \in T$, $h(s_t) \leq h(s^*_{\sigma(t)})$.