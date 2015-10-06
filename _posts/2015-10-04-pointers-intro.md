---
layout: post
title: Pointers & References
modified:
excerpt: A super brief introduction.
tags: [pointers, what is a pointer, what is a reference, pointers and references in c, pointers and references in c++, pointers as function parameters, pointers and arrays, tutorial on pointers, pointers in c, pointers in c++, c, c++, programming, programming languages]
comments: true
image:
    feature: pointer_post.png
    credit: fir0002
    creditlink: www.flagstaffotos.com.au
---

{% include _toc.html %}

#### Don't Be Afraid.
[The stuff of nightmares.](https://alice961994.files.wordpress.com/2014/11/futurama-fry-stress.png) 

That was the expression of the majority of my classmates when our professor finished his lecture on pointers in my *Intro to C class* during my freshman year of college. I can tell you I've seen it on the faces of many entry-level software engineers as well.

For some people, the concept of pointers is difficult to grasp, herculean almost, and is a common reason why many students loathe C/C++ and jump on the Java or C# bandwagon ("Hurrah! No pointers!") because they'll never have to deal with a pointer or memory management again (Java and C# use references in leu of pointers). 

If you're afraid of pointers, don't be. I’ll introduce you to my friends, * (pointer) and & (reference). They're good people.

Note! Pointers & References can be a lengthy topic! This is only a brief introduction. Perhaps I’ll expand this post in the future.
{: .notice} 

#### Why Pointers?
Take the following piece of code:

{% highlight cpp %}
void add_one(int num)
{
    num = num + 1;
}

int main()
{
    int val = 1;
    add_one(val);
    std::cout << "val: " << val;

    return 0;
}
{% endhighlight %}

What do you think is the output of our small program above? If you said "2," you would be incorrect - it's still 1. "But we passed in val as a parameter to add_one!," you may say, and you're absolutely correct. The problem is, is that `add_one` received a **copy** of `val` - `val` was *passed-by-value*.

When a variable is *passed-by-value* to a function, this what happens: the value of `val` is copied to a temporary location, and this location is passed to `add_one` in the form of `num`. Since `add_one` received a copy of `val`, it cannot change `val` in any way.

Instead, without pointers and references, you’d have to write the following:

Without pointers and references, you’d have to write:

{% highlight cpp %}
int add_one(int num)
{
    int new_num = num + 1;
}

int main()
{
    int val = 1;
    val = add_one(val);
    std::cout << "val: " << val;

    return 0;
}
{% endhighlight %}

<figure>
	<a href="http://ericleschinski.com/videos/this_is_sparta_300.png"><img src="http://ericleschinski.com/videos/this_is_sparta_300.png"></a><figcaption><a href="http://ericleschinski.com/videos/this_is_sparta_300.png" title=“King Leonidas, sire, what are pointers?”>”King Leonidas, sire, what are pointers?” “Hmmm….”</a>.</figcaption>
</figure>

#### What are Pointers?
>In C/C++, pointers (e.g. int *x) are variable types that stores the address of non-pointer variables of the same type - they point to the location in memory of that non-pointer variable.

So why would we want a variable that only stores memory addresses? Performance. Pointers allow you to refer to the same space in memory from multiple locations.This means you can modify the value stored in that memory space (where the non-pointer variable existed) and have that change visible in other parts of your program. This is helpful when playing with large objects. In our previous code example, we copied *by value* an integer - 4 bytes of data. What if we wanted to pass a `struct` that contained 500 integers? That’s *4 x 5 = 2000* bytes of data that’s copied! Instead of copying the 2000 bytes, we can pass a pointer, typically 4 bytes with most compilers. To show you how you’d go about using a pointer, let’s modify the original code example.

{% highlight cpp %}
void add_one(int *num)
{
    *num = *num + 1; // use the dereference operator (*) to
		     // “point-to” the value in the memory 
		     // address stored in the pointer num.
}

int main()
{
    int val = 1;
    int *val_ptr = &val; // get the “address-of” val

    add_one(val_ptr);
    cout << "address: " << val_ptr << endl;           // memory address
    cout << "value pointed to:" << *val_ptr << endl;  // value stored at memory address
    cout << "value of val: " << val;

    return 0;
}
{% endhighlight %}

First, notice that we used the **address-of operator (&)**. Using the address-of operator, we can capture the location in memory of `val`, store this memory location in `val_ptr`, and pass this memory location to `add_one`, just like we did before. Unlike before, however, `add_one` now takes in an *integer pointer*. If you tried to pass in `val`, you’d get a compiler error, since an integer is not a pointer to an integer. Even though we passed a pointer, we’re still passing-by-value; the pointer is copied. But! Remember, a pointer is only refers to a location in memory, and in this case, having a copy doesn’t matter, we can still access the value at that location using the dereference operator (*). `*` is C++ for “the value pointed to by…” In this case, the line `*num = *num + 1` is equivalent to saying, “the value-pointed-to-by num (which is 1) equals to the value-pointed-to-by num plus 1,” and so we get 2! Since we changed the value pointed to at this address, which both `num` and `val_ptr` point to, we can access this value outside of `add_one`. Cool, huh? 

Note! If you pass a pointer, you’re still passing-by-value!
{: .notice} 

So you’re probably wondering…

#### What are References?
>In C++ (C doesn’t have references), a reference (e.g. &x) is the “second name” of an existing variable. This second name refers to the address in memory of that variable.

References are cool. *Super cool*. Take a look at this:

{% highlight cpp %}
void add_one(int &num) // num is a reference of val;
{		      
    num = num + 1;     
}

void main()
{
    int val = 1;
    add_one(val);
    std::cout << "val: " << val;
}
{% endhighlight %}

[Feel like this?](http://i.kinja-img.com/gawker-media/image/upload/s--rpTuqXKR--/1460683416091749291.jpg) I know. For the most part, pointers and references are very similar in C++ (most C++ compilers implement references as pointers[^1]), but have the following differences:
* References can’t be reassigned, pointers can (infinitely).
* References are not allowed to be set to NULL, pointers can.
* You can’t take the address of a reference, with pointers you can.
* You can’t perform arithmetic with references, with pointers you can.

[^1]: <http://yosefk.com/c++fqa/ref.html>

I bet you’re wondering, “Are we still passing-by-value?” Nope! We are **passing-by-reference**! which means we are passing the address of the object, no copying necessary (not even a pointer).

On a side note, it’s valuable to mention that the address-of (&) and dereference (*) operators cancel each other out. 
Using `int val = 1`, `int *ptr1 = val`, and `int *ptr2 = &(*ptr)`, `*ptr2` also equals 1. `int *ptr2 = &(*ptr)` is C++ for “`ptr2` is an integer pointer that (equals) points to the address in memory where the the pointer `ptr1` points to.”
{: .notice} 


#### Who Wins?
So when do you use a pointer, or reference? I like how [Klaim](http://stackoverflow.com/a/7058373) from StackOverflow (great site) puts it:

>Use reference wherever you can, pointers wherever you must.
Avoid pointers until you can't.
The reason is that pointers make things harder to follow/read, less safe and far more dangerous manipulations than any other constructs.
So the rule of thumb is to use pointers only if there is no other choice.