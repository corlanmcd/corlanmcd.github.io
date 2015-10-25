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
    <a href="http://36.media.tumblr.com/0c6c8236de5828bee63c5f16774a27aa/tumblr_nbebqw8xgs1rig09go1_1280.jpg"><img src="http://36.media.tumblr.com/0c6c8236de5828bee63c5f16774a27aa/tumblr_nbebqw8xgs1rig09go1_1280.jpg"></a>
    <figcaption>"A well encapsulated car class."</figcaption>
</figure>

Previously, I talked about inheritance in [part one]({% post_url 2015-10-07-pillars-of-oop-polymorphism %}) and inheritance in [part two]({% post_url 2015-10-14-pillars-of-oop-inheritance %}), and now for the grand finale *drum roll* encapsulation! So encapsulation might be the hardest for those just learning about OOP to envision, beause you might think, "Well, why would I not want to make all of *class X* public for the world to see? I want to show off my awesome code!" Well, I'm sure your code is awesome, but that doesn't mean that anyone should be able to peer into code and make modifications! Their modifications might make your awesome code, not awesome... and we don't want that.

#### Encapsulation or: You don't need to know that!

So what is encapsulation? Encapsulation is the concept in which we shackle data with functions that modify said data in a structure such as a class. When you encapsulate something, you're hiding some part of your class (be it functions or variables) as to prevent misuage from the **outside** (outside of your class).

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

 
