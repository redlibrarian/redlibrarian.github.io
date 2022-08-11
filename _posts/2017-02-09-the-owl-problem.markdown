---
layout: post
title: "The Owl Problem: Composition and Abstraction"
date: 2017-02-09
categories: article
tags: featured
image: /assets/images/mandolin.jpg
---

One of the complaints about programming tutorials is that they have the
same problem as drawing tutorials, which [John
Fink](https://twitter.com/adr) refers to as "the owl problem".

<img
src="http://i1.kym-cdn.com/photos/images/facebook/000/572/078/d6d.jpg"
/>

Essentially, the problem is that the tutorials give you a couple of
simple, manageable steps, and then expect you to fill in the gaps
between those and the finished project. The same problem exists in a lot
of online instrument tutorials, and I've heard it discussed as a problem
with expertise: "experts" skip over steps that they unconsciously know,
so they aren't necessarily good at explaining things. You want something
explained by someone who isn't an expert, someone for whom the missing
steps still need to be consciously held in mind.

Anyway, I started thinking about the owl problem, and wondered if part
of the problem isn't *thinking too big*. When we decide to write a
software application, we usually have the end result in mind, which
might include all the functionality and use-cases (drawn, say, from user-stories) that can be gathered together. In Agile development, we aim for a "minimum viable product", but this is still a functioning application worth showing to stakeholders. In other words, a minimum viable product is still an owl. With expert programmers this might not be much of a problem: they can fill in the blanks between a user-story and a finished feature, but in terms of learning to code, this way of thinking may not be the best way.

Over the last year or two I've gotten into functional programming with
[Clojure](https://clojure.org), which is a LISP. I've written
[before](https://redlibrarian.github.io/introduction/2016/05/18/functional-programming.html) on
how working with a LISP requires a different way of thinking about
programming, especially if you're coming from a procedural or
object-oriented background. It occurred to me that some of the lessons
I've learned from functional programming might be a way to help with the
owl problem.

*Abstraction*

As [SICP](https://mitpress.mit.edu/sicp/) tells us, abstraction is one
of the most powerful tools programmers use. The more abstract a
procedure is, the more flexible, understandable, and reusable it is. In
object-oriented programming, abstraction is one of the first concept you
come across. OO tutorials often have you think about a concrete object,
like a car. You know what components a car has, so you split the car up
into multiple components (doors, wheels, windows, etc). You're told not
to worry about the implementation of the components right now - those
implementations are hidden (encapsulated) and the component itself is an
abstraction. So, you might start with the car (in this case, this is the
owl), and you might break it down to components or features, but you put
off the concrete implementation of each component. You put off actually
writing implementation code until you have to (thus avoiding, for
example, premature optimization).

(In procedural programming, at least when I was taking computer science
courses, the method was again to start with a programme that was *too
big* or *too long* and look for area where you could extract a function
or method, encapsulating well-defined pieces of code. This is the
opposite of starting from individual functions and *building up*.)

*Composition*

Functional programming starts from the other direction. Basically, the
idea is not to worry about what your end result is going to be.
Obviously you know you're going to build a car or drawn an owl, but you
don't need to think about things at that level at first. Think about the
concrete implementations of a feature. A door needs to open, so you
write the code that opens a door. A wheel needs to rotate, so you write
the code that rotates a wheel. Later on, when you have written a bunch
of these pieces of code you can combine them into larger units of
functionality (composition).

NOTE: I'm simplifying here for the argument. In fact the switch between
different levels of abstraction and both the encapsulation/abstraction
and composition of functions/methods happens all the time, and
organically, while you're working on a program. But again, this comes
with a experience, for a beginner, it might be worth while thinking
about encapsulation and composition as mutually exclusive.

To take an example: in the library world we have link resolvers. These
basically take an incoming URL which contains some metadata, parses the
URL to extract the metadata, queries a knowledge base, selects (or
constructs) an outgoing URL and sends a user to a licensed resource.

Now, with the owl problem, we would be thinking about a minimum viable
product that includes all of this functionality. In an OO tutorial, you
might design the application with abstractions where those features
should be, deferring their implementation. With FP, however, you might
start at the bottom: given one URL, output a different URL. (In Clojure,
one of the advantages to thinking in this way is that you're always
thinking about data and data transformations, rather than other kinds of
functionality). You can write this fairly simply in Clojure:

```clojure
# takes an input URL, looks up the target in a target collection, and
# appends the parameters to the new target URL

(def lookup_table #collection of URLs)

(defn transform_url [url]
  (let [[target params] (clojure.string/split url #"\?")]
    (str (lookup_table target) "?" params)))
```

But a function is just a piece of code that takes in a value and returns
a value, meaning you can write functional code in, say, Ruby:

```ruby
LOOKUP_TABLE = #collection of urls

def transform_url(url)
  target, params = url.split("?")
  "#{LOOKUP_TABLE[target]}?#{params}"
end
```

Now, obviously writing any one of these functions doesn't give you the
minimum viable product (owl), but you can work on these functions
independently, making them as simple as possible, and then *compose*
them into functions of higher-level functionality.

One benefit to this way of working is testability. Pure functions
(functions with no side effects) are trivially easy to test: given a
value a, produce value b. Even if you have to introduce a side effect,
the side effect's behaviour is kept distinct from the value transforming
function, again making things easier to test.

So, from the perspective of dealing with the "owl problem" for beginning
programmers, I think a functional approach has much to offer in terms of
thinking about composition and abstraction. Once a lot of the mechanics
of this way of coding are taken care of, then higher level components or
features might become easier to design and write, leading to the
capability of a novice programmer to tackle more object-oriented or
procedural ways of coding.
