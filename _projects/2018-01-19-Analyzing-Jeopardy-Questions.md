---
layout: post
title: "Analyzing Jeopardy Questions"
date: 2018-01-19
categories: [data_science]
image: "https://dl.dropboxusercontent.com/s/4nynbr1p7g2g25v/jeopardy.jpg?dl=0"
excerpt: "An opportunity to use data cleaning skills, build simple functions and apply the Chi Square Test on a dataset of Jeopardy questions"
---

This was an early exercise that came up in the Dataquest Data Science course. The objective was to draw some insights on how best to prepare for an appearance on the quiz show Jeopardy.

It proved to be an opportunity to apply some fundamental **data cleaning and preparation** skills that comprise the beginning of a analysis exercise. I also got to write some simple text **functions using loops and dictionaries**. Finally, there is nice application of the **chi square test**.

The dataset is a CSV file of jeopardy questions. I clean up column names. Remove unnecessary spaces from text fields, extract numbers from text fields containing dollar signs and points, and formatted dates.

The analysis work had two parts.

First, to explore weather questions repeat involved creating and applying a function to a series in a dataframe. It wasn't especially sophisticated. The function loops though each key term in a question and looks to see what percentage of key terms in a given question have occurred as key terms in previous questions. Key terms are words longer than five characters which eliminates matching lots of conjunctions and articles like *a, or, the, and* etc. Turns out nearly 70% of key terms in any given question have appeared before.

Second, the question was whether some key terms appear more frequently (than chance) in high value questions vs. low value questions. The posited idea is that you could focus on the terms that are associated with higher value in your preparation. Yeah. It's a bit of a stretch. Luckily this is just an learning exercise. The method is to take a key term and compare how frequently it appears in all questions. And compare that to how frequently it appears in low value and high value questions. The [chi square statistic][chisq] allows you to ascertain whether the difference between an observed frequency and an expected frequency is due to chance or is statistically significant relying on the chi square distribution. The distribution assumes that the data is independent and normally distributed.

Evaluating the likelihood of each term requires us to loop through the entire dataset 3 times: once to establish population frequency, again for frequency amongst high value questions, and then for low value questions. Obviously pretty tedious, so we only look at five key terms. And the finding there is that those terms aren't more or less prevalent in high and low value terms. So not much learning there.

[chisq]:https://en.wikipedia.org/wiki/Chi-squared_test

What did I learn?
- Preparing data for analysis can be the most time consuming part of a project.
- If you are going to be on Jeopardy, studying the questions that have come before is a good idea.
- The usefulness of the Chi Square goodness of fit test

[Link to Project on Github](https://github.com/sgsen/dataquestLearning/tree/master/jeopardyQuestionsAnalysis)
