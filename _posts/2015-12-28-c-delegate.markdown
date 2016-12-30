---
author: wejick
comments: true
date: 2015-12-28 13:38:02+00:00
layout: post
link: http://blog.ggiovani.com/c-delegate/
slug: c-delegate
title: 'C# delegate : function pointer in steroid'
wordpress_id: 31
categories:
- Programming
---

C# delegate is very interesting, on C++ we know about pointer to function and how it helps us at many cases like creating callback mechanism. C# doesn't have such luxuries with pointer, however it has delegate to fill this gap.
I couldn't write without my bias as C++ programmer, but I'll try to make sure it's also easy for other dev to understand.

C# delegate allows us to threat function/method like usual variable, or we could also say it is variable with function as its content.<!-- more -->

# C# delegate example

Here is simple example :
```C#    
    public void Print(string message) // let's say we have this function
    {
    System.Console.WriteLine(message); 
    }
    public delegate void DoSomethingWithString(string someString); // Here we declare delegate with same return value and argument as Print function

    // Create printMessage object as DoSomethingWithString delegate
   
    DoSomethingWithString printMessage;
    printMessage = Print; // Assign the new delegate object with Print function 
    printMessage("Hello this is from delegate"); // This will call Print function 
    
    // output 
    Hello this is from delegate
```

# Multicast Delegate

In C# we can call more than one function from single delegate object. Let's continue from the last example :

```C#    
    public void PrintSecond(string message) // let's say we have this second function
    {
    System.Console.WriteLine("Second "+message); 
    }
    
    printMessage += PrintSecond; // append printMessage with second function
    printMessage("Hello this is from delegate"); // when invoked all functions will be called in order
   
    // output Hello this is from delegate
    Hello this is from delegate
    Second : Hello this is from delegate
```

# Using delegate as function argument

The awesome thing of delegate is we could pass it as argument . Lets continue from above example :

```C#    
    // let's say we have this new function, it takes DoSomethingWithString as argument
    void lets(DoSomethingWithString function1, string message)
    {
    function1(message);
    }
    
    lets(printMessage,"Hi"); // pass printMessage as argument to lets
    
    // output
    Hi
    Second : Hi
```

I hope you can understand it
