---
author: wejick
comments: true
date: 2016-07-15 13:52:59+00:00
layout: post
link: http://blog.ggiovani.com/then-in-javascript/
slug: then-in-javascript
title: Javascript Promise
wordpress_id: 105
categories:
- Programming
tags:
- javascript
- promise
---

I always wondering what it means by 'then' in javascript, no body care to discuss it.

Just found out that before 'then' we need to learn about promise. So what is promise?

So it is part of modern javascript's nature which run anything asynchronously, so no one know what will happen. Promise gives us interface to handle the future.

For example, read comments :

// I have this function which have time out to simulate the asynchness

```javascript
function succesOrNot(result)
{
    // creating new promise
    var promise = new Promise(function (resolve, reject) {
    // we simulate success case here
    if (result)
    {
        resolve('you are good boy'); // promise use resolve to tell the succesfulness
    } 
    // we simulate failed case here
    else
    {
        reject('no yet boy'); // promise use reject to tell failness
    }
    
    // to simulate async
    window.setTimeout(function () {
    }, Math.random() * 1000);
    });
    // return the promise here
    return promise;
}

// we call above function, with true so it will call resolve
// give 'then' with two callback function 
succesOrNot(true).then(
    function (successMessage) { // first callback handles success
        alert(successMessage);
    },
    function (failMessage) { // second callback handle failed
        alert(failMessage);
    }
);
```

The example above is quite self explainig, hope you're doing well.

More info about promise :

[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
