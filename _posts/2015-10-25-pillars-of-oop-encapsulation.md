---
layout: post
title: Encapsulation
modified:
excerpt: The Third Pillar of OOP or: Hands off!
tags: [object oriented design, oop, what is a oop, what is are the three pillars of object oriented design, encapsulation, polymorpish, inheritance, oop in c++, PIE, three pillars of oop, tutorial on OOP, programming, programming languages]
comments: true
image:
    feature: encapsulation.png
    credit: Ocean's Eleven
    creditlink: http://www.imdb.com/title/tt0240772/
---

<figure>
    <a href="http://36.media.tumblr.com/0c6c8236de5828bee63c5f16774a27aa/tumblr_nbebqw8xgs1rig09go1_1280.jpg"><img src="http://36.media.tumblr.com/0c6c8236de5828bee63c5f16774a27aa/tumblr_nbebqw8xgs1rig09go1_1280.jpg"></a>
    <figcaption>"A well encapsulated car class."</figcaption>
</figure>

Previously, I talked about inheritance in [part one]({% post_url 2015-10-07-pillars-of-oop-polymorphism %}) and inheritance in [part two]({% post_url 2015-10-14-pillars-of-oop-inheritance %}), and now for the grand finale *drum roll* encapsulation! So encapsulation might be the hardest for those just learning about OOP to envision, beause you might think, "Well, why would I not want to make all of *class X* public for the world to see? I want to show off my awesome code!" Well, I'm sure your code is awesome, but that doesn't mean that anyone should be able to peer into code and make modifications! Their modifications might make your awesome code, not awesome... and we don't want that.

#### Encapsulation or: You don't need to know that!

So what is encapsulation? Here's an example: your smartphone. You own one, right? You know how to use it, download apps, play funny vines, check Facebook, and once in a while, maybe, make a phone call. Do you how to program the kernal? Probably not. You only know what you need to operate the phone, but not any of that technical nonsense! So, encapsulation is a form of *information hiding*, just like how the manufacturer of your smartphone is *hiding* all the technical wizardry that makes your smartphone work. The technical definition of encapsulation is:

> The hiding of implementation details to users through the means of shackling data and functions that modify the data, thus keeping both from interference and misuse from the outside. This is usually obtained using a class structure.

When it comes to programming, sometimes you want to hide the details of some class you are writing, say 'Porsche 911'. You're proud of this class you've just written, and you don't want anyone to just change the implementation details! Someone might change the 'horsepower' from 560 to 9001!, and the next person to 'drive()' the car might get into an accident - and we don't want that. Encapsulation could help us prevent this mishap:

{% highlight cpp %}
#include <iostream>

class Porsche911
{
public:
Porsche911() { car_color = "Black"; }"
Porsche911(std::string color) { car_color = color; }
~Porsche911() {}

void drive() { std::cout << "VROOOOOM!"; };
void print_color() { std::cout << "Car color: " << car_color; }
void print_horsepower() { std::cout << "Horsepower: " << horsepower; }

private:
static const unsigned int MAX_SPEED  = 194;
static const unsigned int HORSEPOWER = 560;
static const unsigned int NUM_WHEELS = 4;
static const unsigned int NUM_DOORS  = 4;

std::string car_color;
};

int main() {
    Porshe911 my_porsche("Blue");
    my_porsche.drive();
}
{% endhighlight %}

In the example above, there are a few encapsulated bits: 'MAX_SPEED', 'HORSEPOWER', 'NUM_WHEELS', 'NUM_DOORS', and 'car_color'. No matter how hard a user of the 'Porsche911' class tried, he wouldn't be able to because the previously mentioned variables (the one's in CAPS being constant variables) were declared as **private** variables - they cannot be accessed or modified outside of the class. So no matter how many 'Porsche911's someone created, each and everyone of them with have the same horsepower, max speed, and number of wheels and doors. If we wanted to allow the user to change some of these attributes (like set the horsepower to 9001), we could add a few *setter* methods that set these attributes, but let's refrain from that - we don't want any car accidents.

A rule of thumb: encapuslate data you don't want the world to see or is unnecessary for the user of the class to know.
{: .notice}


Well, that was the last piece of the PIE! *ba dum tss* Delicious, wasn't it? Hopefully, I've done a decent job at introducing the three pillars of object-oriented programming: polymorphism, inheritance, and encapsulation. 'Til next time!'

 
