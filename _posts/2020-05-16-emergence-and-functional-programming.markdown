---
layout: post
title: Functional Programming and Emergence
date: 2020-05-16
categories: article
tags: featured
image: /assets/images/mandolin.jpg
---

It's been a while since I've written a blog post on technology or
programming, but this week I returned to some legacy code I wrote when I
arrived at University of Alberta and inherited a programming project.
The details of the project are unimportant; what I found interesting
returning to it after all these years was the effect of the intervening
years. When I initially wrote the application, I had just gotten the
Ruby language firmly in my head - it was, and still is, the language I
know best, though these days I'm very rusty. I read Sandi Metz' now-classic
*Practical Object-Oriented Design in Ruby*, as well as David West's
*Object Thinking*, which is language-agnostic, but alongside POODR
really helped me think about object-oriented design. 

When I took
computer science back in the mid-90s, learning Pascal and Motorola 64000
assembly, we were taught structured imperative design: break your
programs up into functions for ease of reasoning, but basically you're
giving commands to a processor one at a time. When I tried to grok
object-oriented programming through C++ and Java, I got a bit lost
(later, I ended up doing a fair amount of Java web programming at
University of Ottawa, which helped, but I relied so heavily on the IDE
that I don't feel I *learned* very much). So anyway, increased
familiarity with Ruby, plus POODR and *Object Thinking* made me finally
grasp OO-design, so that's what I built my programs in.

The basic idea of OO design is that there are *things* that exist in
your application, and those things interact. It's a very ontological way
of thinking about software, and is often said to rely on *nouns* rather
than *verbs*. Those things, called objects, are defined as classes, which
have properties and behaviours, and can inherit and pass on those
properties/behaviours to classes higher and lower in the taxonomy. When
your program runs, those classes get instantiated in memory, and are
considered *objects*. Objects have methods which, naively, if you
learned structured imperative programming like I did, you would think of
as functions operating on the data stored in the object as properties.
POODR does a great job explaining why this way of thinking is wrong:
those "functions" (really methods) are better off being thought of as
mechanisms for sending or receiving *messages* between objects. They are
the public interface of interacting and interrelating objects.

One thing OO design does is changes the idea of program flow. In
imperative programming, you tend to think of a program as beginning,
issuing some commands to the computer or manipulating some data, then
ending. OO design allows you to think about an ecosystem of interrelated
data objects that don't necessarily have a teleology, but exist in
memory as members of an interconnected whole.

After writing my OO programs, I became interested in functional
programming (a third paradigm to add to imperative and object-oriented),
and so I learned Clojure. Again, FP had been *really really hard to
grok*, but at some point, working with Clojure, I figure it out. Coding
in FP is mentally a very different process than designing in OO. With
OO, you try to design as much as you can upfront. Using something like
the Unified Modeling Language (UML) you might plan out all your objects,
their properties and behaviours, in advance, on index cards or
something. All the behaviour of the application is, essentially,
predetermined. In some sense, OO is deterministic; where indeterminacy comes in (and is often the cause of bugs) is with the mutability of data. With FP, you don't design in that way. You think of the
simplest data manipulations and you start with those. You construct the
simplest functions that do a single well-defined thing, and once some of
those are built, then you use them to construct more complex functions,
etc, etc. The end result is, to my mind, a much simpler and more elegant
complete program, but it's one that relies less on up-front design and
more on *emergence*.

I've written about emergence on the blog before - the idea that new
properties or behaviour emerge in a higher level of organization than
exist at a lower level. A static example is water, which has different
properties than either hydrogen or oxygen on their own. A more dynamic
example would be ant colony behaviour, which emerges from but is not
reducible to the behaviour of individual ants. The patterns formed by
cellular automata are another example of emergence. Emergence is often a
characteristic of "complex systems".

Functional programming design can be considered emergent in the sense
that the complexity of the program emerges from but is not reducible to
the individual functions. But it's emergent in another way, in that FP
has this idea - which comes, I think, from Smalltalk - that you can and
should be able to interact with a running program. Because pure functions in
FP have no side effects and data is immutable, modifying a running
program is in some senses much safer than it would be in the
interconnected ecology of predetermined object behaviour. Changing a
function in a running system changes the *emergent* behaviour of the
whole, the way changing the rule for a cell in a cellular automaton
would produce a different pattern.

Anyway, I returned this week to a program I had written as orthodox OO
about a decade ago to redesign a significant chunk of (fragile) functionality. Since learning Clojure, functional programming had so deeply entered my programming mind, that the simplest way to approach the problem (which is essentially a complex data transformation project with lots of insonsistency and edge cases) was the functional approach. Luckily, despite mostly being used in an OO context, Ruby lends itself well to functional style. In the end I wrote a functional-flavoured (not strictly functional, as I used a lot of non-functional elements to save time and energy) Ruby program to cover the redesigned part of the original program, wrapped it in a module, and mixed it into the original, larger code base.


I don't know that this story has any deeper significance, more than just
as an example of continued learning, observation, and understanding what
you're doing. Habits of thought and perspectives change, and its good to
take some time occasionally to take a look at your work from outside to
see how and why that's happening. In many ways over the years I've gone
from being comfortable with change to actively craving it. The
quarantine lockdown has been difficult in that respect, as I tend to
like change. All these days of the same structure and pattern is hard to
take.
Perhaps that's why I've embraced FP over the determinism of OO; I'm not
someone who likes to do a lot of up-front design - I'd rather dive in
and let the end result emerge from the work itself.

I can see this in the way I write, too, come to think of it. I don't
plan or outline; I might jot down a few notes, but really, I just start
writing and see where it takes me. The text emerges from the momentary
thoughts I have at any given point. This means I have to rewrite a lot,
and I end up going through a lot more drafts than I would, I think, if
the text was more predetermined through upfront planning and outlining.
There's something intuitive, performative, improvisatory in this way of working that I enjoy (there's a
connection here, I think, with Gadamer and hermeneutics as well). Not to
say that other approaches are wrong. As the motto of the Vulcans goes,
there is "infinite diversity in infinite combinations". Uniformity is
death. 
