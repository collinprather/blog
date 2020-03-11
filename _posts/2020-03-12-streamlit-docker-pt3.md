---
title: "Deploying web apps with Streamlit, Docker, and AWS - part 3"
toc: true
comments: true
layout: post
hide: false
search_exclude: false
description: "Using docker-compose to add a Postgres database to our web app."
categories: [docker, AWS]
---

This is part 3 of 3. Make sure to read through [part 1](https://collinprather.github.io/blog//docker/aws/2020/03/10/streamlit-docker-pt1.html) and [part 2](https://collinprather.github.io/blog//docker/aws/2020/03/11/streamlit-docker-pt2.html) before you continue!

# Introducing docker-compose

Suppose we want our users to be able to access some data like this

introduce this data and explain how it comes from my example!

|    |    CRIM |   ZN |   INDUS |   CHAS |   NOX |    RM |   AGE |    DIS |   RAD |   TAX |   PTRATIO |      B |   LSTAT |   PRICE |
|---:|--------:|-----:|--------:|-------:|------:|------:|------:|-------:|------:|------:|----------:|-------:|--------:|--------:|
|  0 | 0.00632 |   18 |    2.31 |      0 | 0.538 | 6.575 |  65.2 | 4.09   |     1 |   296 |      15.3 | 396.9  |    4.98 |    24   |
|  1 | 0.02731 |    0 |    7.07 |      0 | 0.469 | 6.421 |  78.9 | 4.9671 |     2 |   242 |      17.8 | 396.9  |    9.14 |    21.6 |
|  2 | 0.02729 |    0 |    7.07 |      0 | 0.469 | 7.185 |  61.1 | 4.9671 |     2 |   242 |      17.8 | 392.83 |    4.03 |    34.7 |
|  3 | 0.03237 |    0 |    2.18 |      0 | 0.458 | 6.998 |  45.8 | 6.0622 |     3 |   222 |      18.7 | 394.63 |    2.94 |    33.4 |
|  4 | 0.06905 |    0 |    2.18 |      0 | 0.458 | 7.147 |  54.2 | 6.0622 |     3 |   222 |      18.7 | 396.9  |    5.33 |    36.2 |

but we don't want to have to mess with csv's

