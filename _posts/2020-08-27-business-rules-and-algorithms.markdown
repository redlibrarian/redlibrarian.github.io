---
layout: post
title: Business Rules and Algorithms
date: 2020-08-27
categories: article
tags: featured
image: /assets/images/mandolin.jpg
---

NOTE: I've written previously about algorithmic bias from a Marxist
perspective
[here](https://redlibrarian.github.io/article/2019/03/11/algorithmic-bias-fragment-machines.html)

What does "algorithmic bias" mean at the level of computer science
classes or writing code? When I took computer science classes, the basic
tendency of what was taught was that procedures are the encoding of
algorithms. Admittedly that was many years ago, but nothing I've read in
computer science literature since then indicates a change. To write a computer program to solve a problem (i.e. really,
to perform a task) you break the task down into component parts and
write those parts out as steps connected by various kinds of flow logic. Flow logic can include decision logic, but it basically means any point at which the operating "direction" of the program changes. The program, with its procedures and flow logic, contains one or more (often many) algorithms written out as code. Every decision the programmer makes - from the initial analysis of the problem to be solved, to the way larger steps are broken up into smaller ones, to the form and content of flow logic and decision points, are places where "algorithmic bias" get inserted.

I should back up here, though, and say that I don't think "bias" is the
right term. It implies, to my mind, the existence of some kind of
neutral, unbiased code that is then swayed or corrupted, prejudiced one
way or another. This kind of code is an impossibility: the encoding of
decision points always abstracts from reality, and as in every
abstraction, some elements of reality are given more weight in the
abstraction than others. Additionally, "bias" implies an individual
relationship to the world, one that is incorrect (or unconscious) and
which can be corrected. But that could only be the case if capitalism
was not racist, sexist, heteronormative, etc, and racism, sexism,
heteronormativity were then mistakes, rather than produced by racial capitalist
social relations themselves. Bias suggests that racism and sexism are
individual mistakes to be corrected by bringing them inline with the
non-racist or non-sexist world, rather than reflections of the racism
and sexism of capitalism itself. 

At the software level, then,  "bias" goes along with the idea that
there is some kind of non-algorithmic code, to which algorithms (or
worse, "an algorithm") can be added or not. In the wake of the grades
fiasco in the UK recently, the Guardian ran a headline that read:
"Councils scrapping use of algorithms in benefit and welfare decisions".
One line in the story read as follows: "The use of artificial
intelligence or automated decision-making has come into sharp focus
after an algorithm used by the exam regulator Ofqual downgraded almost
40% of the A-level grades assessed by teachers." There are two things
going on here. One is the idea that there are non-algorithmic and
algorithmic computer programs, and the other is that algorithms have
agency. These two positions reflect bourgeois ideology first of the
possibility of neutrality (i.e. non-algorithmic software) and second of
the [self-determining agency of
technology](https://redlibrarian.github.io/article/2017/05/14/franklin-real-world-of-technology.html), rather than technology being
the product of social forces and relations themselves. In both senses,
capitalist social structures are let off the hook too easily.

Neither of these is the case, and I think journalists are doing a real
injustice by framing things in this way. As I wrote in ["Ruthless
Criticism of All that
Exists"](https://era.library.ualberta.ca/items/048f1970-8324-41aa-a993-bace2b9257c2),
the idea that there is some kind of non-algorithmic code is wrong. When
Twitter introduced its relevance-sorted tweets a number of years ago,
people complained that the "algorithmic" Twitter feed was worse than the
previous one (sorted by most-recent). The idea was that the
most-recent-first sort order, because it was the original, had been
changed, had been made algorithmic. But most-recent-first sorting is
just as much an algorithm as relevancy-sort. There are two reasons, I
think, why most-recent-sort seemed some how neutral, unbiased, and
"non-algorithmic": in the first place it was the original, and UX
designers know that a long-standing feature gains the appearance of
natural, or unmarked (to use a term from semiotic which will become
important in a minute). A change to a UX element - the change from one
algorithm to another - seems to *introduce* something extra, which is
why changes to user interface often provoke anger until the new UX
element becomes acceptable as normal. The other reason I think
most-recent-sort *seemed* non-algorithmic is that the algorithm it
encodes is straightforward and commonplace: we all understand a
chronological ordering. On the other hand, relevance-sorting is
mysterious and esoteric - anyone who has looked at the Solr index's
relevance configuration file knows just how many weighted settings there
are to control a relevancy-sort. So the more easily understood algorithm
appears non-algorithmic compared to the more complex and myesterious
(black-box) kind of algorithm.

So, the first thing to understand is that all software is composed (and
*only* composed) of algorithms. This ultra-simple piece of Ruby code
encodes two algorithms:
{% highlight ruby %}
def sum_of_three_numbers(a, b, c)
  return a + b + c
end

puts sum_of_three_numbers(2, 6, 8)
=> 16

{% endhighlight %}

The algorithms are as follows: "To find the sum of three numbers take each
number in turn and add them together" and "Find the sum of 2, 6, and 8
and print the result". Algorithms may be complex, but they are not
esoteric - they are the basic building blocks of computer programming.

I said above that I didn't like the term bias, as it implied some kind
of unbiased algorithm. In reality, because an algorithm is an
abstraction, and so necessarily selective, algorithms always privilege
*some* aspect of reality over others. I think this may lie at the heart
of programmers' unwillingness to accept algorithmic bias: they don't
understand that their algorithms are always abstractions and that
abstractions always privilege some aspect of reality over others.

Now, programmers can either develop the algorithms they need on their
own - writing a bubble sort, for example, to implement a sorting
algorithm, or they can receive the already-abstracted rules of the
algorithm from someone else. These are the "business rules" that often
come from an employer or parent organization and that have to be
implemented in a computer system. Programmers turn these business rules
into algorithms and data, and encode them in software. So now we can see
that the selective abstraction of reality occurs both when the
programmer writes code and when the organization develops business
rules. Bias - or really, the marked and unmarked structures of
preference, value, exploitation, and power - enter the program via these
two vectors.

In semiotics, there's the concept of marked and unmarked parts of a
binary pair. The unmarked part is the one that is taken for granted,
normal, default, unremarkable - in racial, patriarchal capital, the
unmarked elements have significant social power: white, male,
cisgendered, neurotypical, etc, etc. Any reference to the opposite value
of the binary pair is *marked* because it sticks out, it seems unusual,
abnormal, wrong. All of this makes sense only against particular
backgrounds and contexts. (I learned about this in the course of my
music degree, where unmarked elements compose the "normal" musical
background while marked elements are stylistically significant, but the
social background is even more complex and acculturating). 

Algorithmic bias - whether it comes from the programmer or from the
business rules - tends to arise (but not always) from the encoding of
the unmarked element of the pair without considering the marked element
*or the social and political context*.
This is a social problem, not simply a programming problem. When, in a
concrete example that made the news a number of years ago, the following logic is encoded as part of an algorithm:
{% highlight ruby %}
if (title == "doctor") then (gender = "male")
{% endhighlight %}

This is due to the unmarked privilege of masculinity, and the
association of masculinity with authority. The bias is not necessarily
*added in* to the algorithm - though it *does* have to be made explicit
within it, at some point - but arises from the social situation and position of the programmer
or whoever develops the business logic in particular structures of
privilege, domination, and power. Note that it is not simply that the
logical statement written above is wrong, but that the programmer who
encodes it does not see it as wrong, even in the face of their own
empirical experience. Ideology trumps the positivism of fact.

There are two things, then, that might help remedy this situation among
software developers. One is the recognition of the causal power of
social structures to determine seemingly pure and impersonal
("scientific" or "mathematical") processes like writing code. This is
the very granular level at which the problem must be addressed. The
other is the broader social question of structures of power, the
*structuration* of individuals, the dialectic of structure and agency.
This, indeed, is a problem not restricted to engineers or computer
programmers, but connects with issues of ideology and political
understanding, of social theory, and the individualism and "freedom" of bourgeois
capitalism.

There's obviously a lot more detail that should be gone into here,
especially with respect to the data question (positivism implies that
data are "facts about the world" that are simply gathered, but the same
selective abstraction and construction of structures of oppression
occurs in data as well. What are the consequences for linked data
ontologies?), but also with the ways in which decision points and other
flow logic which - as opposed to the if/then statement above - do not
seem to explictly encode markedness or privilege, in fact do so. But
this post is long enough already. I may revisit some of these more
specific elements later on. In the meantime, if you haven't already,
definitely read Safiya Noble *Algorithms of Oppression*, Marie Hicks
*Programmed Inequality*, and Ruha Benjamin *Race After Technology*. 
