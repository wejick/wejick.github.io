---
author: wejick
comments: true
date: 2016-04-04 15:32:43+00:00
layout: post
link: http://blog.ggiovani.com/function-template/
slug: function-template
title: Function Template
wordpress_id: 75
categories:
- Programming
tags:
- c++
- meta programming
- template
---

It’s been a while since I wrote about technicall stuff. This time I write about very basic feature of C++, function template. What I found intimidating at the first time learning C++ were memory management and template, so it’s normal if you say it’s not easy.
With function template you can create one function for different data type.

Normally to handle different data type we write different function or do overloading, lets create simple sizeOf function.

```C++
size_t sizeOf(int n)
{
 return sizeof(n);
}
size_t sizeOf(char n);
{
 return sizeof(n);
}
size_t sizeOf(const char* n);
{
 return sizeof(n);
}
int main(int argc, char **argv) {
 std::cout << sizeOf(40);
 std::cout << sizeOf('p');
 std::cout << sizeOf("petruk");
}
```

Look, they use same implementation therefore those code is not good.
we could rewrite the code above using function template.

```C++
template<typename T>
size_t sizeOf(T n)
{
 return sizeof(n);
}
int main(int argc, char **argv) {
 std::cout << sizeOf<int>(40);
 std::cout << sizeOf<char>('p');
 std::cout << sizeOf<const char*>("petruk");
}
```

Now we save a lot of lines of code with function template.

The structure of function template is really simple :

```C++
template<typename T>
[return type/it could be T] ([parameter / it could be T])
{
[implementation]
}
```

Any data type you put at T would replace all available T.

For example when you write :

```C++
sizeOf<int>(40)
```

virtually you write :

```C++
size_t sizeOf(int n)
{
 return sizeof(n);
}
```

However you must remember that template is not just simple text processing like preprocessor or macro.
