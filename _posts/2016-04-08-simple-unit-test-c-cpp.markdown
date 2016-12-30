---
author: wejick
comments: true
date: 2016-04-08 02:06:50+00:00
layout: post
link: http://blog.ggiovani.com/simple-unit-test-c-cpp/
slug: simple-unit-test-c-cpp
title: Simple unit test in C / C++
wordpress_id: 81
categories:
- Programming
tags:
- c++
- unit test
- unit testing
---

Honestly I never familiar with unit testing and never have project which require TDD. However as other developer I realize that sooner or later this is a must. Lately unit testing become my main curiosity especially in C and C++. I find many framework to do unit testing, in my case this is not a good thing. I couldn't find the essence of unit testing when reading about unit testing with common framework.<!-- more -->

After reading some unit testing example I decided to do unit testing in most minimal way. I came up with this macros :

```c
#define START_TEST(X)        printf("\n\n== TEST %s",X);
#define TEST_NAME(X)         printf("\n%s",X);
#define ASSERT_EQUAL(X,Y)    if(X==Y) printf(" PASS"); else printf(" FAIL!");
#define ASSERT(X)            if(X) printf(" PASS"); else printf(" FAIL!");
```

I know this is far from enough, but it really help me to understand unit testing.

This is the example how to use it :

```C++
START_TEST("Data Validation")
isRegisterPass = true;
try
{
 StubSingleton::GetInstance()->Register(testItemXml.GetName(),testItemXml.GetContent(),testItemXml.GetType());
}
catch(...)
{
 isRegisterPass = false;
}
TEST_NAME("Data Validation : Register XML item")
ASSERT(isRegisterPass)
TEST_NAME("Data Validation : Retrieve JSON item")
ASSERT_EQUAL(testItemJson.GetContent(),StubSingleton::GetInstance()->Retrieve(testItemJson.GetName()))
```


Simple right

Actually I don't know whether the test I wrote is good or bad, but it just do what I need to know.
