---
author: wejick
comments: true
date: 2016-10-07 12:28:38+00:00
layout: post
link: http://blog.ggiovani.com/javascript-code-optimization/
slug: javascript-code-optimization
title: Javascript Compiler and Code Optimization
wordpress_id: 119
categories:
- Programming
tags:
- javascript
- optimization
---

JavaScript Compiler optimization in browser is quite unique, it has to take account of many things C compiler doesn't have to aware. I will talk about general condition in browser environment which has different needs than node.js environment.

![javascript compiling](http://imgs.xkcd.com/comics/compiling.png)

In nature JavaScript is interpreted language and that's slow compared to compiled language. There are numerous techniques for JavaScript optimization like Ahead Of Time compilation and Just In Time compilation. The problem is those two need more time and resource, with JIT being the worst although the generated code is the fastest. Another bad news is AOT or JIT can also failed to generate right machine code, like wrong type inference (will talk about it later).

In browser environment startup latency should be as small as possible for good user experience. However there are cases where fast execution is more favorable than fast start up time, like on games or long running code. Or even we need something in between like moderate startup time and not so faster than interpreted performance. Startup time is not only the metric, allocating cpu and memory for short lived code is not a good decision too.<!-- more -->

### Stop talking Javascript Bullshit

At this point you now understand why I said the condition is unique. So how browsers tackle this issue? Most modern browser available on the market provide 2 until 4 mode of how they run javascript with each mode could be really different approach not only different level of optimization. I will talk about 3 mode approach : intrepetation, Just In Time Compilation with minimal optimization (Baseline) and Just In Time Compilation with full optimization. You see the pattern, the first has fastest startup time, the last has fastest execution time.

Browser has to decide which mode to use for each code it runs at runtime, the question is how they decide it?

In many modern browser like Webkit, Chrome and Firefox at the first time the code runs on top interpreter, then after some instructions it uses baseline compiler. After some many instructions it runs using more sophisticated JIT compiler to get the most optimized machine code to run.

Baseline compiler focuses on how to generate optimized machine code from each instruction individually, and it will try to optimize the generated code each cycle from feedback from previous cycle. But Why ? For example variable in javascript could be anything, lets say var A = 10 could be int or could even be a long.

After many cycles of execution browser would decide to use more optimized JIT, which compile the code with assumption collected from baseline compiler. There will be many assumption, like our last int and long example. How if the assumption is wrong, like at some cases var A is float? it would stop the execution then kick the baseline again.

The real question is how much many instruction is? Webkit will switch to baseline after 6 function execution of the function and 66 time function execution on the baseline it will switch to next tier compiler. For Firefox the number are more vague with multiple time execution to baseline then hundreds times execution to next tire compiler.

For me the coolest thing about failing back from optimized JIT to baseline JIT is how the browser able to transfer the stack state. This process involve smart copying and reconstructing the stack to allow resuming the execution.

### What can we do

I am not good at making conclusion, at least by knowing how the browser runs the code we know what to do. Like be discipline by using 1 type for each variable, use local variable and don't have too deep call stack. You can read two last link in the reading material for good javascript practice to get more from your browser.

Reading material :
[https://blog.mozilla.org/javascript/2014/07/15/ionmonkey-optimizing-away/](https://blog.mozilla.org/javascript/2014/07/15/ionmonkey-optimizing-away/)
[https://developer.mozilla.org/en-US/docs/Mozilla/Projects/SpiderMonkey](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/SpiderMonkey)
[https://webkit.org/blog/3362/introducing-the-webkit-ftl-jit/](https://webkit.org/blog/3362/introducing-the-webkit-ftl-jit/)
[http://desalasworks.com/article/javascript-performance-techniques/](http://desalasworks.com/article/javascript-performance-techniques/)
[http://archive.oreilly.com/pub/a/server-administration/excerpts/even-faster-websites/writing-efficient-javascript.html](http://archive.oreilly.com/pub/a/server-administration/excerpts/even-faster-websites/writing-efficient-javascript.html)
