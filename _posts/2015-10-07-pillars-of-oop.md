---
layout: post
title: The Pillars of OOP
modified:
excerpt: It's all about delicious…
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

Don't look at me that way, I'm not crazy. Pie really does have everything to do with OOP, object-oriented programming. 

It's the conceptual base that makes C++ (and Java, Python, Ruby, Simula, etc) what they are, OOP languages. So if you're like me, you learned what the three (or four, depending on who you talk to; but if I added the forth, I couldn't run with this whole pie joke...) pillars of OOP are: polymorphism, inheritance, and encapsulation.

Let's go over 'em one-by-one.

**Note!** Some people may argue that the principles of SOLID (**S**ingle responsibility, **O**pen-closed, **L**iskov substitution, **I**nterface segregation and **D**ependency inversion) are the true pillars of OOP & OOD (Object-Oriented Design). I’m not here to argue for or against, but PIE is a typical textbook explanation of OOP that most people are familiar with. Perhaps I’ll do a post on the SOLID principles in the future.
{: .notice} 

#### Polymorphism

![Image of pie](http://www.mrlamont.com/uploads/1/7/0/2/17021682/833771300.gif)
{: .image-pull-right}

You’ve probably been bashed over the head enough times (assuming your a CS student or software dev) to know that polymorphism is greek for "many forms." What does this mean exactly? Well, it means in OOP languages that a single type or class can take many forms. Referring to the image on the right, imagine we have a base class named `Animal`. From `Animal` we can derive several classes (called… derived classes): `Dog`, `Cat`, and `Duck`. These are called… derived classes and they inherit (another piece of the “pie”… ha) any shared abilities from `Animal` (such as `speak()`), such that a `Dog` is-a `Animal`. You could modify the `speak` function of `Dog`, `Cat`, and `Duck` so that they make their respective sounds (“Meow, etc). 

Now, say you had an array of `Animal`s and you decided to add a `Duck` object, a `Dog` object, and a `Cat` object (you can do this because all three of type `Animal`). If you were to iterate through the array and make a call to each object’s `speak()` function, you’d get what you’d expect: “Meow,” “Woof,” “Quack.” It doesn’t matter if it’s a `Dog` or a `Duck`, it’s guaranteed that if the object is of type `Animal` it has a `speak()` function that is callable. That’s the power of polymorphism.

Here’s a code example:

{% highlight cpp %}
#include <iostream>
#include <vector>

class Animal
{
public:
    Animal(){}
    ~Animal(){}

    virtual void speak() { std::cout << "Noise"; };
};

class Dog : public Animal
{
public:
    Dog(){}
    ~Dog(){}

    void speak() { std::cout << "Woof!"; }
};

int main() {
    std::vector<Animal*> v;
    v.push_back(new Animal());
    v.push_back(new Dog());

    for (auto a : v)
    {
        a->speak();
	std::cout << endl;
    }
}
{% endhighlight %}

#### Inheritance

So we mentioned inheritance above, and for a good reason. If `Dog`, `Cat`, or `Duck` couldn’t *inherit* from `Animal`, we would’t have been able to accomplish what we just did. 

Inheritance comes in two flavors: single and multiple. An example of *single inheritance* is a class that inherits from a single base class - above, `Dog` only inherits from `Animal`. You can probably guess what *multiple inheritance* means - a class that inherits from multiple base classes (e.g. `Child` inherits from `Father` and `Mother`).
