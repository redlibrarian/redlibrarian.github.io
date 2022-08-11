---
layout: post
title: Predicate and Dialectical Logic
date: 2019-06-20
categories: article
tags: featured
image: /assets/images/mandolin.jpg
---

(Full disclosure: I'm neither a philosopher nor a logician. What follows
is my own inadequate and incomplete understanding of predicate and
dialectical logic.)

I was going to call this post "Classical and Dialectical Logic", and to
begin with the syllogism, that form of logical argument which can take
many forms, but which follows the basic format: major premise - minor
premise - conclusion. For example:

>All humans are mortal<br />
>All Greeks are humans<br />
>All Greeks are mortal<br />

The syllogism explicitly does not concern itself with the truth of
either of the premises, simply that the conclusion necessarily
(logically) follows from the combination of the major premise and the
minor premise. In the 19th Century, this kind of reasoning was
superseded by first-order or predicate logic, coming out of the work of
Gottlob Frege, but predicate logic still retains some of the flavour of
the syllogism.

Predicate logic begins with sets of propositions made on a particular
domain. The propositions take the form "there exists an x such that x
is a...". The part of the proposition "x is a..." contains the predicate
relationship, familiar to us in the terms of Linked Data triples:
subject - predicate - object. For example, in Linked Data we might make
the following propositions:

>Jane Austen is an author (predicate here is "is")<br />
>Jane Austen wrote Pride and Prejudice (predicate here is "wrote")

As with the syllogism, we can infer from these two propositions a
conclusion:

>Pride and Prejudice has_author Jane Austen

This conclusion (called an "inference" in linked data and similar
conceptual systems) follows necessarily from the propositions.
Similarly, in predicate logic, the *modus ponens* is also logically
valid, and can be thought of as the modern form of the syllogism:

>if p then q<br />
>p (is true)<br />
>therefore q<br />

These logical systems, both classical and predicate, are based on a few
foundational principles:

* The principle of identity (A is A; A = A)
* The principle of non-contradiction (A is not not-A)
* The principle of the excluded middle (Either A is true, or not-A is
true, and there is no third option)

We use this kind of logic formally in math and science and even parts of
librarianship all the time, but we also use it informally so often that
the three principles of classical logic form an unconscious fabric of
our intellectual engagement in the world. When I go to the grocery store
I know there is a thing called milk that I want to buy and that milk is
milk (principle of identity), milk is not orange juice (principle of
non-contradiction), and that I either buy milk or I don't (excluded
middle). For many things in the world this kind of logical approach
works because many things have a more-or-less stable identity (milk is
milk).

But there are many things in the world that we deal with
materially and intellectually which do not have a stable identity, whose
identity changes in two ways: over time, and in relationship to other
things. Actually, when we look closer, milk is an interesting example.
Milk is milk in relationship to mammals, but is it still milk in
relationship to soy beans, almonds, or oats? Colloquially it remains
"milk", but according to certain regulations in the EU for example,
non-mammal "milk" is not milk. Milk also changes over time, eventually
becoming not-milk in the nutritional sense (i.e. it goes bad). So even
seemingly stable identities start to break down when we look at them in
particular ways.

I think of this kind of like the laws of Newtonian physics: at an
everyday level and a particular human-scale they work fine, but with a
different perspective they break down, lose their coherence, and have to
be replaced by different laws.

If, when we look carefully, predicate logic is inadequate to account even for something as simple as *milk*, how much less adequate is it for dealing with the messy realities of human life and society? What is the identity of abstract concepts ("freedom", "democracy")? Political formations? Gender and sexuality? The stable comfortable binaries of predicate logic (A or not-A, man or woman, and no third option) break down completely in many of these cases.

One of the different perspectives on logic that takes relationality and
change over time into account is the dialectical logic developed by
Hegel in the early 19th century. I am drastically over-simplifying
Hegel's logical theory here, but in general, what Hegel argued was as
follows:

Every identity automatically implies its own negation (if there's something called
milk there must also be something [or many things] that is not milk).
The presence of milk and not-milk at a given moment is unstable,
dissonant, and this instability sets change in motion.
The motion of things involves the mutual adjustment of milk and not-milk
until something that is different from either comes into being.

A good example might be as follows:

>There is milk and there is acid (not-milk)<br />
>Putting the milk in contact with the acid produces an unstable
situation<br />
>The unstable situation leads to the milk curdling and the production of
a third thing: buttermilk

Now, two things are important to bear in mind about Hegel's dialectical
logic. In the first place it is an *idealist* theory, which means that
Hegel considered thought and being as the same thing, so that mental or
intellectual operations were the same as operations in the real world.
He would not likely have used an example like buttermilk, but instead
used, for example, particular ideas or political categories (like the
State) to illustrate his logic. In the second place, Hegel's dialectic
is *teleological*: he predicts a time when all contradications (that is,
the confrontation of a thing with its negation) are resolved in a
higher-order perfection. For example, he saw human political history as
the working out of various contradictions, and that the achievement of
a perfect state (which he equated with the Prussian state of the 19th
century) meant the end of political change, that is, the end of history.
We are unable to take such teleological theories seriously anymore, but
this doesn't mean that the dialectical process has become obsolete.
Rather, it means that the chain of dialectical reconciliation simply
goes on: change is permanent.

In terms of idealism, it was Marx who "set Hegel right side up" by
coming up with a materialist version of dialectical logic. In other
words, Marx sees not only intellectual or mental constructs as subject
to the dialectical process, but everything in existence. Engels
formulated the laws of this "dialectical materialism" in his book *Dialectics of Nature*:

1. The Law of Unity and Conflict of Opposites (i.e. things enter into
   contradiction with other things).
2. Over time, quantitative changes become qualitative changes.
3. The Law of the Negation of the Negation (i.e. the negation of the
   milk is the acid, the negation of the acid is the buttermilk).

Now, when Marxists talk about the dialectic, there is often an idea that
they are rejecting predicate or classical logic. However, as I've said,
predicate logic fits with many everyday, real-world situations.
However, there are many cases in which predicate logic becomes a barrier
to understanding; generally cases which involve relationality and change
over time. Relationality is different from a predicate relationship. In
dialectical logic, the act of writing Pride and Prejudice *changes* Jane
Austen, a change which cannot be represented by making the proposition
"Jane Austen wrote Pride and Prejudice" or even recording new predicates
which indicate how she changed in the writing. In a very real sense Jane
Austen becomes not-Jane Austen through the writing of Pride and
Prejudice.

By thinking dialectically we are able to keep track of relationality
(the relation of Jane Austen to Pride and Prejudice affects both of
them) and change over time (Jane Austen after P&P is not identical to
Jane Austen before P&P), but we are also able to keep track of "the
negation of the negation". Dialectical logic requires that we constantly
search for the higher unity of any pair or set of contradictions. When,
for example, people argue for one or another electoral system
(proportional representation or first-past-the-post, etc), dialectical
logic requires that we see *all* of those alternatives as part of a
larger unified category (elections, or representative democracy), which
leads us to think about contradictions and negations in *those*
categories, and so on. This is why in dialectical thinking the totality
is so important. It is impossible to really understand, say, electoral
reform in isolation from all the other institutions of representative
democracy, which leads us to think about all our other political and
legal institutions, which leads us to think about broad relations of
power, which leads us to see how electoral reform fits into the totality
we can understand as society or (in Marxist terms) a mode of production.

For many people predicate logic is the only logic, because it is easily
representable symbolically, which means it was easy to formalize and
eventually automate. Computers are the automation of predicate logic - a
bit is either 1 or 0 and there is no third option - and all our
algorithms bear the traces of predicate logic (["All doctors are men; this gym member is a
doctor; therefore this gym member is a man"](https://www.thejournal.ie/gym-sexism-2002500-Mar2015/)). But
predicate logic has very real limitations, which can be overcome by the
application of dialectical logic. (I'm also a fan of applying non-logic
or irrationality to problems, but that's a different post).

The usefulness of dialectical logic becomes more and more apparent the
more we think in those terms. Whenever we see something proposed as a
binary opposition (either/or), we should suspect that those things are
more related than is being let on. Whenever we see something being
looked at in isolation, we should suspect that the larger context will
be instructive. Whenever we see something posited as unchanging and
eternal (capitalism, for example, or gender, or language), we should suspect that
those identies are much less stable over time than is being let on.
Sometimes there is an intellectual reason for sticking with predicate
logic, but more often than not there is a political reason, and so
dialectical logic (especially in a Marxist context) helps to look at the
bigger picture to see who benefits from insisting on stable identities
and isolated analysis. This in itself should suggest that predicate
logic and dialectical logic cannot be thought of as two stable, isolated
systems, but interrelated ones in productive contradiction with each
other. Only predicate logic sees the division between the two logical
systems as strictly defined, sees each system as isolated,
self-sufficient, and incompatible.

People - especially engineers and computer scientists - tend to really
like predicate logic as a way of understanding the world because it is
unambiguous and stable. Predicate logic is comforting and comfortable.
But the world, and not just the social world, but the natural world as
well, is not unambiguous and it is unstable. It is constantly changing,
adapting, reconciling contradictions and producing new contradictions.
Hiding from that ambiguity and instability behind predicate logic may be
comforting, but it has particular social and political effects, and
these effects are generally pernicious precisely because they are not in
line with the way the social or the material world actually works.

Addendum: I should add that what I said above about algorithmic systems
being being conditioned by predicate logic is also true of knowledge
representation systems in general. If predicate logic underpins how we
intellectually relate to the world, then it underpins how we *know* and
how we represent knowledge. Many of our social relationships get reified
first as stable identities and then in our KR systems. Many of the
problems identified with classification systems like Dewey and LCSH come
down to the reification of particular racist, sexist, and colonial
identities through predicate logic.

NOTE: Two books which I found really helpful on the relationships
between predicate logic, dialectical logic, and materialism are:

Richard Norman and Sean Sayers, *Hegel, Marx, and the Dialectic*
(Harvester Press, 1980).

John Bellamy Foster *Marx's Ecology: Materialism and Nature* (Monthly
Review Press, 1999).

