---
layout: post
title: Inheritance
modified:
excerpt: The Second Pillar of OOP
tags: [object oriented design, oop, what is a oop, what is are the three pillars of object oriented design, encapsulation, polymorpish, inheritance, oop in c++, PIE, three pillars of oop, tutorial on OOP, programming, programming languages]
comments: true
image:
    feature: pillars_of_oop.png
    credit: F.M. Schmitt
    creditlink: http://www.fmschmitt.com/travels/spain/cordoba_province/cordoba-mosque/FirstExpansion.html
---

<figure>
    <a href="http://www.epicurious.com/images/articlesguides/seasonalcooking/winter/key-lime-pie.jpg"><img src="http://www.epicurious.com/images/articlesguides/seasonalcooking/winter/key-lime-pie.jpg"></a>
    <figcaption>”Delicious PIE has everything to do with Object-Oriented Programming.”</figcaption>
</figure>

Back for some more PIE? Good. This time, let's talk about...

#### Inheritance - “Luke, I am your father.”

So we mentioned inheritance in [part one]({% post_url 2015-10-07-pillars-of-oop-polymorphism %}) of this series, and for a good reason. If `Dog` couldn’t *inherit* from `Animal`, we would’t have been able to accomplish what we just did   - which was storing `Dog` in an array of `Animal`s.

So what does inheritance do for us? Well, it allows us to create classes (called a derived, child, or subclass) using other classes (called a base, parent, or super class). This creates an **is-a** relationship - a derived class (`oHuman`, `oPet`, `oDog`, `oCat`) **is-a** base class (`oAnimal`). On the flip side, a `oHuman` **is not a** `oPet`. 

<figure>
    <a href="http://www.derekyu.com/tigs/forums/tutorials/gmtut/gmtut-008.png"><img src="http://www.derekyu.com/tigs/forums/tutorials/gmtut/gmtut-008.png"></a>
    <figcaption>"The tree of life."</figcaption>
</figure>

This makes it easier for us to reuse code (because good programmers are lazy) and create software that is flexible and easily maintainable. For example, take a gander to the image on the right. Imagine that we’re creating a game involving walking humans, dogs, and cats. We did our market research and found that walking animals aren’t what the hip, cool kids are looking for nowadays - they want [flying animals](http://i.ytimg.com/vi/QH2-TGUlwu4/hqdefault.jpg). Well, there’s two ways of doing this: 1) adding flight capability to each class (`oHuman`, `oDog`, and `oCat`), or 2) adding `flight = true` to our parent class (`oAnimal`), have the change trickle down to it’s child (and grandchildren) classes, and be on our merry way. What would you chose? 1 or 2?

So you chose #2, [you must be a software developer.](https://bintrayblog.files.wordpress.com/2013/10/lazyness.jpg) Inheritance comes in two flavors: single and multiple. An example of *single inheritance* is a class that inherits from a single base class - above, `oDog` only inherits from `oPet`. You can probably guess what *multiple inheritance* means - a class that inherits from 2 or more base classes (e.g. `Child` inherits from `Father` and `Mother`).

Here’s a code example of multiple inheritance:

{% highlight cpp %}
#include <iostream>

class Father
{
public:
    Father(bool burb){ can_burb = burb; }
    ~Father(){}

    virtual void burb() { if (can_burb) std::cout << "BUUUURB!"; };

    bool can_burb;
};

class Mother
{
public:
    Mother(bool fly){ can_fly = fly; }
    ~Mother(){}

    virtual void fly() { if (can_fly) std::cout << "FLYING!"; };

    bool can_fly;
};

class Child : public Father,
	      public Mother
{
public:
    Child(bool burb, bool fly)
        : Father(burb),
          Mother(fly){}
    ~Child(){}
};

int main() {
    Child c(false, true);
    c.fly();
    c.burb();
}
{% endhighlight %}

Onward to encapsulation!

 
