---
layout: post
title: Pointers & References
modified:
excerpt: "They're not as bad as you think!"
tags: [pointers, what is a pointer, what is a reference, pointers and references in c, pointers and references in c++, pointers as function parameters, pointers and arrays, tutorial on pointers, pointers in c, pointers in c++, c, c++, programming, programming languages]
comments: true
image:
    feature: pointer_post.png
    credit: fir0002
    creditlink: www.flagstaffotos.com.au
---

{% include _toc.html %}

#### Don't Be Afraid
[The stuff of nightmares.](https://alice961994.files.wordpress.com/2014/11/futurama-fry-stress.png) 

That was the expression of the majority of my classmates when our professor finished his lecture on pointers in my *Intro to C class* during my freshman year of college. I can tell you I've seen it on the faces of many entry-level software engineers as well.

For some people, the concept of pointers is difficult to grasp, herculean almost, and is a common reason why many students loathe C/C++ and jump on the Java or C# bandwagon ("Hurrah! No pointers!") because they'll never have to deal with a pointer or memory management again (Java and C# use references in leu of pointers). 

If you're afraid of pointers, don't be. Let's clear the air with my friends * and &, they're good people.

#### What are Pointers?
>In C/C++, pointers are variable types that stores the address of non-pointer variables of the same type. 

So why would we want a variable that only stores addresses? Memory. We would like our programs to use the least amount of memory where it is not feasible to make copies of everything. Take the following piece of code:

{% highlight cpp %}
void add_one(int num)
{
    num = num + 1;
}

void main()
{
    int val = 1;
    add_one(val);
    std::cout << "Val: " << val;
}
{% endhighlight %}

What do you think is the output of our small program above? If you said "2," you would be incorrect - it's still 1. "But we passed in val as a parameter to add_one!," you may say, and you're absolutely correct. The problem is, is that `add_one` recieved a **copy** of `val` - `val` was *passed-by-value*.

When a variable is *passed-by-value* to a function, this what happens: the value of `val` is copied to a temporary location, and this location is passed to `add_one` in the form of `num`. Since `add_one` recieved a copy of `val`, it cannot change `val` in any way.
