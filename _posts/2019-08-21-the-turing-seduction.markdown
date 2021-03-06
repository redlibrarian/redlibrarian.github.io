---
layout: post
title: The Turing Seduction
date: 2019-08-21
categories: article
tags: featured
image: /assets/images/mandolin.jpg
---

*Or, why there's no such thing as machine intelligence.*

In his seminal paper on machine intelligence, *Computing Intelligence
and Machinery* (1950), Alan Turing replaces the question "can machines
think?" with the more tractable question of what would happen if a
machine took the place of one of the human beings in what he calls "the
imitation game":

>The new form of the problem can be described in terms of a game which we call the
'imitation game." It is played with three people, a man (A), a woman (B), and an
interrogator (C) who may be of either sex. The interrogator stays in a room apart front the
other two. The object of the game for the interrogator is to determine which of the other
two is the man and which is the woman. He knows them by labels X and Y, and at the
end of the game he says either "X is A and Y is B" or "X is B and Y is A." The
interrogator is allowed to put questions to A and B... (433).

By answering only the questions put to them by the interrogator, the
idea is that either human being could "imitate" the "other" gender
(Turing's description of the game is rife with gender stereotypes).
Turing's test of machine intelligence is whether a machine could
imitate either of the human players to such an extent as to fool the
interrogator. In the course of his paper, Turing dismisses various
objections to the validity of this idea, while stating that:

> The original question, "Can machines think?" I believe to be too
meaningless to deserve discussion. Nevertheless I believe that at the end of the century
the use of words and general educated opinion will have altered so much that one will be
able to speak of machines thinking without expecting to be contradicted. I believe further
that no useful purpose is served by concealing these beliefs. The popular view that
scientists proceed inexorably from well-established fact to well-established fact, never
being influenced by any improved conjecture, is quite mistaken. Provided it is made clear
which are proved facts and which are conjectures, no harm can result. Conjectures are of
great importance since they suggest useful lines of research.

In 1956, seduced by Turing's conjecture, a group of eminent computer
scientists gathered at Dartmouth College, New Hampshire, and formulated
the first artificial intelligence research project. [The proposal](https://web.archive.org/web/20070826230310/http://www-formal.stanford.edu/jmc/history/dartmouth/dartmouth.html) for the
Dartmouth meeting was to "proceed on the basis of the conjecture that
every aspect of learning or any other feature of intelligence can in
principle be so precisely described that a machine can be made to
simulate it". In this way, Turing's conjecture was enshrined within
computer science research where it remains to this day.

The mention of "learning" in the Dartmouth proposal is significant, not
only because we live in an age of "machine learning", "deep learning",
"reinforcement learning", and so on, but because it echoes one of the
more curious statements in Turing's original paper. "We normally
associate punishment and rewards with the teaching process", Turing
writes, which is a position unlikely to be (openly) supported by many
teachers, and perhaps says more about the British school system in the
1920s. But this, too, has been enshrined in the various schools of
reinforcement learning, where an unacknowledged utilitarianism holds
sway.

If rewards and punishment are the consequentialist form of artificial
intelligence "learning", another form which we can call deontological is
based on the understanding and application of rules. The idea that rules
can cover the rich expanse of human behaviour is just as hard to swallow
as the idea that rewards and punishment do, and Turing admits as much:

>It is not possible to produce a set of rules purporting to describe what a man should do in
every conceivable set of circumstances. One might for instance have a rule that one is to
stop when one sees a red traffic light, and to go if one sees a green one, but what if by
some fault both appear together? One may perhaps decide that it is safest to stop. But
some further difficulty may well arise from this decision later. To attempt to provide
rules of conduct to cover every eventuality, even those arising from traffic lights, appears
to be impossible. With all this I agree.

For computing machines, however, rules (or the instruction set) are the very basis of their functionality, and the order in which these rules must be followed (the algorithm) is unchangeable. Turing writes:

>The idea of a learning machine may appear paradoxical to some readers. How can the
rules of operation of the machine change? They should describe completely how the
machine will react whatever its history might be, whatever changes it might undergo. The
rules are thus quite time-invariant. This is quite true. The explanation of the paradox is
that the rules which get changed in the learning process are of a rather less pretentious
kind, claiming only an ephemeral validity.

For Turing, the ability to depart from the algorithm is the hallmark of
machine intelligence and its ability to learn:

> Intelligent behaviour presumably consists in a departure from the completely
disciplined behaviour involved in computation, but a rather slight one, which does not
give rise to random behaviour, or to pointless repetitive loops.

Symbolic artificial intelligence (like Linked Data systems, for example) which seek to encode all the rules for a given domain (i.e. an ontology) thus attempt to show that Turing's objection to a complete set of rules can be overcome through the method of logical inference. In other words, the domain can infer new rules from the logical combination of rules already provided by human programmers/data modelers. In this way, symbolic AI seeks to overcome Dreyfus' objection not only that the *amount* of knowledge required for intelligence is too large to be symbolically represented, but that there are kinds of knowledge which are not symbolically representable at all.

Connectionist artificial intelligence, of which machine learning is a
particular kind, seeks to leverage Turing's observation that to exhibit
intelligence a machine needs to be able to free itself from the rules
encoded by a human programmer. In a neural network, for example, a human
programmmer sets the initial strengths of the neuronic connections, but
the machine is able to adjust those strength in order to achieve the
machine's goal (perception, classification, etc.). However, Dreyfus's
objection to connectionist AI points out that not only does a human
being assign the machine a goal, but a human being is the only thing
that can judge the machine's success or failure. If a machine produces a
particular scent, only a human being has the cultural and aesthetic
knowledge to tell whether that scent is a perfume or a noxious odour. In
this way, connectionist AI simply offloads the knowledge that symbolic
AI seeks to encode onto a human programmer/user.

Furthermore, the ability to a computer programme to change itself, to
depart from its encoded rules, is not evidence of any kind of
intelligence, as Turing would "presume", but is a well-understood
property of certain kinds of programming languages that are by-no-means
considered "intelligence". This property is called "homoiconicity",
which means that the code and the data share a single representation.

In non-homoiconic languages, though it might be more appropriate to
refer to homoiconic situations rather than languages, code and data can  take various forms. Consider the following pieces of ruby code:

<pre><code>

2+2  # function with two arguments, function in the middle
-5.abs  #method called on a number class, function after the "."
print "this is a string"  # function called with one argument, function
at the beginning

a_hash = {a: "b", c: "d", e: "f"}  # hash created by assignment
another_hash = Hash.new  # hash created by constructor
another_hash[:a] = "b"  # assign values to the hash

</code></pre>

So we have different syntax conventions at play in Ruby, different
*representations* of the code. Sometimes the function names are at the
beginning, sometimes in the middle, sometimes they are methods attached
to a class instance with the dot operator. Sometimes there are
assignments, sometimes there are curly braces. There are multiple ways of
representing the data as well. All these different ways make it
difficult (if not impossible) for *code to read and write itself*, i.e.
for a programming language to treat its own code as data.

Now, consider Clojure, which is a kind of LISP, the language invented in
1958 by John McCarthy, one of the Dartmouth attendees:

<pre><code>

(+ 2 2)  #function with two arguments, function in first position
(Math/abs -5)  #function with one argument, function in first position
(print "this is a string") #function with one argument, function in
first position
(var a_hash {:a \b, :c \d, :e \f})  # function call to create a hash and
bind it, function in first position
(var another_hash (hash-map :a \b, :d \d, :e \f)) # create a hash using
the explicit hash-map function; both function calls (var and hash-map)
are in first position in their respective forms

</code></pre>

In clojure, all this code takes the same form: a list of data elements
between two parentheses, with the function always in the first position.
These forms can be nested, but the first element is always a function
call (unless prefixed by a single quote, which tells the interpreter not
to interpret the list). These lists of data within parentheses are
called "forms" in Clojure, but more generally *s-expressions* (symbolic
expression). Because all data and code in Clojure (and in LISPs more
broadly) are represented in the same form, there is no *functional*
difference between code and data: any piece of code can treat any other
piece of code as data to be created, read, updated, or deleted. LISPs
like Clojure operationalize Turing's idea of the way the rules governing
a machine can change: with homoiconicity, code (re)writing itself is
trivial. (This is the idea behind Clojure macros, a core piece of
functionality in the language).

So, if we leave aside the cognitive objections (like Dreyfus') and the
moral objections of someone like Joseph Weizenbaum, who argued that even
if machine intelligence is possible and achieveable, there should be
some activities, functions, and behaviours that we reserve for humans;
if we leave those objections aside, can we not say that machine
intelligence is a possibility because homoiconicity gives us what Turing
defines ("presumably") as the basis of intelligent behaviour, i.e. that it "consists in a departure from the completely
disciplined behaviour involved in computation." 

I think not. Homoiconicity is not magic; it is a well-understood property of
computer languages, and it has been around since at least 1958. It's
just code. That
"presumably" of Turing's gives no indication of actually being true.
However, Turing's arguments, both at the deontological level of rules
and at the pragmatic level of self-modifying code, has been very
seductive not only for computer scientists, but for journalists,
governments, and other policy makers. There's a "conspiracy of hype"
around AI - which began with calling it "artificial intelligence" rather
than something more prosaic - a conspiracy to which computer scientists,
journalists, and governments are all party, because they all benefit
from the hype. The mystification of, say, machine learning (which is
really nothing more than a self-modifying program plus statistics),
benefits researchers looking for grants, journalists looking for
sensational stories, and governments looking to invest in technology and
discipline labour. The phenomenon of "Explainable AI" is part of this
mystification - but that's for a later conversation I need to have with Mike Ridley.

When I participated in an AI and Society Summer Institute put on by the
Alberta Machine Intelligence Institute in June, I wasn't really shocked
that the critiques of Dreyfus and Weizenbaum were absent. I was shocked,
however, by the lack of any critique of AI at all. Machine intelligence
was taken for granted, not as a metaphor or mystification, but as a
common-sense truth. Once taken for granted, the idea of machine
intelligence leads to many things, many of them bad. The idea of machine
intelligence itself needs debunkers; if the debunkers are proven wrong
in the long run, it can only improve the field of AI. But if we are
right...

EDIT: I just realized that the paragraphs on symbolic and connectionist
AI aren't explicit about their relationship to self-modifying
programmes. Both symbolic and connectionist AI have ways to self-modify
to a limited extent: the ability to automatically infer new statements from existing
ones (in symbolic AI), and the ability to automatically modify neuronal
weights (in connectionism). The criticism that self-modification in
itself does not lead to intelligence is not negated by this limited
ability, just as it is not negated by the existence of homoiconicity.

*Update: August 24, 2019*

In a discussion on Twitter, Kyle Geske
([@stungeye](https://twitter.com/stungeye)) and Dave Mayo
([@pobocks](https://twitter.com/pobocks)) both mentioned that
homoiconicity is not required for self-modifying code. Homoiconicity
may make the self-modification of code easier in some respects, but
plenty of languages are capable of some kind of self-modification that
don't display homoiconicity. In that case, then, the examples of
homoiconicity above should be read as illustrative examples of the ways
in which code can be treated as data, and thus lead to self-modifying
programmes, rather than the canonical example of self-modifying code as
such.
