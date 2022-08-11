---
layout: post
title: "Marx, Clojure, and Values"
date: 2017-10-29
categories: article
tags: featured
image: /assets/images/mandolin.jpg
---

*NOTE: I imagine there must be a way to connect "values" in programming
with Marx's theory of value, but I'm not sure what that is, and it's
beyond the scope of this post.*

My friend [Kyle](https://twitter.com/stungeye) let me know about
[this post](http://www.lispcast.com/clojure-and-types) on "Clojure vs.
The Static Typing World", which was a reflection on Rich Hickey's
keynote at Clojure/conj 2017. Kyle drew a particular passage to my
attention: "Rich talked about types... as concretions, not abstractions. I very much agree with him on this point, so much so that I didn't know it wasn't common sense."

>But, on further consideration, I guess I'm not that surprised. People
>often talk about a Person class representing a person. But it doesn't.
>It represents information about a person. A Person type, with certain
>fields of given types, is a concrete choice about what information you
>want to keep out of all of the possible choices of what information to
>track about a person. An abstraction would ignore the particulars and
>let you store any information about a person. And while you're at it,
>it might as well let you store information about anything. There's
>something deeper there, which is about having a higher-order notion of
>data.

This brought to mind a passage by Marx in the
[*Grundrisse*](https://www.marxists.org/archive/marx/works/1857/grundrisse/),
where he discusses his methodology. This passage has been commented on
and discussed many times since the publication of the *Grundrisse*, but
it seems to me that by connecting some of these ideas (political economy
and data/software) we might be able to think through some of the aspects
of immaterial labour and value in the works of, for example, Maurizio
Lazzarato, Michael Hardt and Antonio Negri. In the 1857 Introduction,
Marx writes that

>The concrete is concrete because it is the concentration of many
>determinations, hence unity of the diverse. It appears in the process
>of thinking, therefore, as a process of concentration, as a result, not
>as a point of departure, even though it is the point of departure in
>reality and hence also the point of departure for observation and
>conception. (p. 101).

For Marx the concrete, that which is represented by a class or another
non-primitive datatype, is what we begin with, what we see around us. We
see a _Person_ or a _Car_ or we are faced with a _User_. The process of
analysis allows us to break apart (*ἀνάλυσις*, to unravel) these
concrete phenomena into the abstract qualities or values that make them
up. In this sense the abstractions *determine* the form of the concrete
thing. My height is 5'4" - this is an abstract value that is one
determinant of my concrete being; I am a _Person_ with a _height_ of
164.5cm.

Values do not change; they are immutable. 5'4" does not become a
different value when I represent it in a different form (164cm). This
doesn't mean that units of measurement are a- or trans-historical; the
Greek, Roman, Chinese, French and English "foot" do not refer to the
same absolutel length - but the length encoded in 5'4" in 2017 is an
unchanging value. 

> 42 doesn’t change. June 29th 2008 doesn’t change. Points don’t move,
> dates don’t change, no matter what some bad class libraries may cause
> you to believe. Even aggregates are values. The set of my favorite
> foods doesn’t change, i.e. if I prefer different foods in the future,
> that will be a different set.

This immutability of value is one of the cornerstones
of Clojure. As Chas Emerick, Brian Carper, and Christoph Grand wrote in *Clojure Programming*:

>Most programming languages, either through idiom or explicit design,
>encourage the use of mutable state, whether within the guise of objects
>or not. Functional programming languages tend to encourage the use of
>immutable objects—referred to as values—to represent program state.
>Clojure is no different in this respect.

In some ways the idea of immutable state would seem to support standard
formal logic (what Engels calls "metaphysical" logic). _A_ is always _A_
and is never _not-A_. But Hickey's recognition of concretions as the
"concentrations of many determinations" allows us to recognize the
dialectical logic embedded within the Clojure view of types. The
concretion, the *making concrete*, occurs at a particular moment in
time. The Clojure documentation
[refers](https://clojure.org/about/state) to *identity* (i.e. _A_ = _A_)
as an "entity that has a state, which is its value at a point in time".
So we have, in a sense a "synchronic" view of state, where state is not
changing historically, but is a sequence of static, immutable snapshots
in succession (this is similar to the Saussurean view of language which
informed Structuralism). In this view, we started with the concrete
phenomenon -- _A_ or _Person_ -- and then we broke it down into its
component values (height, for example). But we don't *work* with the
abstractions, just as in the real world I don't appear as a height with
brown hair, I appear as a person. By working back up from the
abstractions to the concretions we can ensure the correctness of our
modeling (does this type interact with other types as they would in the
real world).

And the real world *does* change, it *is* mutable. The Clojure view of
state, then, does allow for a dialectical unfolding of identities over
time. 

>Identities are mental tools we use to superimpose continuity on a world
which is constantly, functionally, creating new values of itself.

State at one moment can contradict state at another moment, in the
sense that the total state changes over time, and Clojure allows for
working safely with this kind of contradiction. Indeed, it is precisely
the immutability of the abstractions (values) that provide the ability
for a program's state to change safely over time; a very dialectical
view of the running of software over time.

There is, naturally, a danger in believing the world to always be
synchronic, that is, ahistorical; this is precisely Marx's argument in
the *Grundrisse*, that the classical economists did the work of analysis
to come up with abstractions, but then stopped there: with a view of the
world that they believed to be true, unchanging, and transhistorical. Marx's solution is to extend the methodology to return again to the concrete (this is the the method of presentation of *Capital*, for example).  But the post I began with does a good
job, I think, identifying a mitigating strategy, which is the pragmatism
of solving real-world problems. If we want to set up a model of the way
the world works or the problem we want to solve in software, that is
only half the solution. The model must *work* in the real world; in many
ways, software should conform to Marx's famous 11th thesis on Feuerbach,
which is quoted only too often today: "The philosophers have only interpreted the world, in various ways; the
point is to change it." Useful software is effective software.

All of Rich Hickey's talks are fantastic - to find out more about his
idea of programming with values, it's worth watching his 2012 Keynote
["The Value of
Values"](https://www.infoq.com/presentations/Value-Values).
