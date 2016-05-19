---
layout: post
title: "Functional Programming: An Attempt at an Explanation"
date: 2016-05-18
categories: introduction
tags: featured
image: /assets/images/mandolin.jpg
---

After making a workshop proposal to the [Access
Conference](http://accessconference.ca), I began
thinking of how I would approach explaining functional programming to
programmers who "just don't get it". When I first looked into functional
programming, it made my head hurt - it was a different way of
approaching programs. It took me several years before I finally got what
FP was, and how I could think about working with it. Since the Access proposal was rejected
this year, I thought I would try to get some of these ideas down here.
This blog post isn't for experienced programmers, especially not for
programmers who already know FP, or LISP, or
[Clojure](https://clojure.org), etc, etc. It's an
attempt to give a sense to people who do some coding in a procedural or
object-oriented language of how FP works, and some of the things you can
do in an FP idiom.

**Those Parentheses**

First off, I want to tackle the question of the parentheses. Many people
new to FP will find themselves faced with something like 

~~~clojure
(defn word-count [x]
  (let [words (vec (str/split (str/replace (str/lower-case x) #"[\W]+" " ") #"\s+"))]
      (reduce conj {} (for [y words]
      {y (count (filter #{y} words))}))))
~~~

and get really intimidated. What's with all the parentheses? The first
thing I should say is that you quickly get used to working with the
parentheses. The second thing is that they aren't conceptually
difficult. In Ruby you might make a function call like this:

~~~ruby
# Ruby
square(5)  # 25
~~~

See, there are two parentheses. They come after the function name, and
surround the argument. In Clojure you would write:

~~~clojure
;; Clojure
(square 5) ;; 25
~~~

There are still only two parentheses, only this time you put *both* the
function name and the argument inside them. Let's try chain two
functions together:

~~~ruby
# Ruby
divide_by_two(square(5)) # 12.5
~~~

~~~clojure
;; Clojure
(divide_by_two (square 5))  ;; 12.5
~~~

In both cases, you have four (two pairs of) parentheses, only in Ruby
they come after the function name and surround the argument, while in
Clojure, they surround both the function name and the argument. This can
lead to some interesting behaviour. In both Ruby and Clojure, operators
are functions. The "+" function takes two arguments, adds them together
and returns a result. For the sake of argument, let's rewrite that as a
"plus" function in Ruby:

~~~ruby
# Ruby
def plus(first, second)
  first+second
end

plus(5, 4) # 9
5 + 4 # 9
~~~

These two functions calls ("plus" and "+") do exactly the same thing,
but their syntax is different (with the "+" function, the function name
goes *between* the two arguments). In Clojure, the two functions would have
exactly the *same* syntax:

~~~clojure
;; Clojure
(defn plus [first second]
  (+ first second))

(plus 5 4) ;; 9
(+ 5 4) ;; 9
~~~

So what we see in Clojure is that a) everything that's not a primitive
is a function and b) functions always have the same syntax. This makes
it really easy to understand what a program is doing and follow the
chain of successful function calls. Which brings me to the last thing
I'll cover in this post - how does a functional program work?

**How can you build a program out of functions?**

In object-oriented programming, the terms *function* and *method* are
often used interchangeably, especially among people who have come from,
for example, a procedural language like C. A mathematical function maps one value to another through a mathematical transformation. In programming, a function can either return a value (like a mathematical function does) or it can have a side-effect (e.g. print to the screen or cause a change in program state) or both. A method is a function that is attached to an object in an object-oriented language. In FP, we try as far as possible to write *pure* functions, that is, functions which only return a value (i.e. that don't have side-effects) and *always* return a value (even if the value is "nil").

So for example, our "square" function might be defined
like this:

~~~ruby
# Ruby
def square(num)
  num*num
end

square(4)  # 16
~~~

~~~clojure
;; Clojure
(defn square [n]
  (* n n))

(square 4) ;; 16)
~~~

Given the number 4, the square function will *always* return the number
16, because the function is defined only with reference to the values
passed to it. In procedural and object-oriented languages, we're allowed
to write functions that might look outside themselves for some data, so
for example we might write:

~~~ruby
# Ruby
def check_weather_and_date(date)
  "Today's date is #{date} and the temperature is #{@temperature}"
end
@temperature = "30 Celsius"
check_weather_and_date("March 1") 
  # "Today's date is March 1 and the temperature is 30 Celsius"

@temperature = "-5 Celsius"
check_weather_and_date("March 1") 
  # "Today's date is March 1 and the temperature is -5 Celsius"
~~~

We can see right away that, due to it's reliance on the variable
@temperature, we can pass the same argument ("March 1") to the
"check_weather_and_date" function and it will return different results.
The @temperature variable is part of the program's *state*, and because
state can change independent of the function, it makes functions very
difficult to test and understand. 

In functional programming, we try to avoid state as much as possible. We
make sure that we write functions that return the same value every time,
making them very easy to understand and test. And because we always
write *functions* as opposed to *methods*, we know that our functions
will always return values. This allows us to build smaller functions up
into larger units through *composition*:

~~~clojure
;; Clojure
(def author "SAM")
(reverse (clojure.string/lower-case author " WROTE THIS") 
  ;; siht etorw mas
~~~

That's a pretty trivial example, but here's an example of a working
rna-transcription function in one line, using only a composition of
simple functions:

~~~clojure
;; Clojure

(defn to-rna [dna]
  (clojure.string/join (map {\G \C \C \G \A \U \T \A} dna)))
~~~

Through function composition, you can end up writing very sophisticated,
powerful programs building up from very simple functions that you chain
together, secure in the knowledge that all your functions a) don't
depend on state and b) always return a value. Because functions always
return a value, you can chain functions together so that they take the
return value of one function as the input of another.

I've only scratched the surface here, and haven't talked enough about
side-effects and state, the lack of variables and variable assignment, or control
structures and recursion, but hopefully this attempt to demystify
functional programming will be useful.
