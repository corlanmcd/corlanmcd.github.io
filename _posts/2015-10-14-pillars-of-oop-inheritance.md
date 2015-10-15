---
layout: post
title: The Pillars of OOP
modified:
excerpt: Part II - Inheritance
tags: [object oriented design, oop, what is a oop, what is are the three pillars of object oriented design, encapsulation, polymorpish, inheritance, oop in c++, PIE, three pillars of oop, tutorial on OOP, programming, programming languages]
comments: true
image:
    feature: pillars_of_oop.png
    credit: F.M. Schmitt
    creditlink: http://www.fmschmitt.com/travels/spain/cordoba_province/cordoba-mosque/FirstExpansion.html
---

#### It's all about delicious… PIE!

<figure>
    <a href="http://www.epicurious.com/images/articlesguides/seasonalcooking/winter/key-lime-pie.jpg"><img src="http://www.epicurious.com/images/articlesguides/seasonalcooking/winter/key-lime-pie.jpg"></a>
    <figcaption>”Delicious PIE has everything to do with Object-Oriented Programming.”</figcaption>
</figure>

Back for some more PIE? Good. This time, let's talk about...

#### Inheritance

So we mentioned inheritance in [part one](/_posts/2015-10-07-pillars-of-oop-polymorphism.md) of this series, and for a good reason. If `Dog`, `Cat`, or `Duck` couldn’t *inherit* from `Animal`, we would’t have been able to accomplish what we just did   - which was evoking `speak()` in three different flavors of `Animal`.

![Image of inheritance](http://www.derekyu.com/tigs/forums/tutorials/gmtut/gmtut-008.png)
{: .image-pull-right}
So what does inheritance do for us? Well, it allows a derived (or child) class to share the same characteristics as it’s base (or parent) class.  Inheritance comes in two flavors: single and multiple. An example of *single inheritance* is a class that inherits from a single base class - above, `Dog` only inherits from `Animal`. In the image to the right [source(http://forums.tigsource.com/index.php?topic=3630.0), you get the idea (although `Dog` inherits from `Pet`). 

You can probably guess what *multiple inheritance* means - a class that inherits from multiple base classes (e.g. `Child` inherits from `Father` and `Mother`). 
