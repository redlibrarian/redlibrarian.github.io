---
layout: post
title: "Some Thoughts from #lodlamto"
date: 2016-05-14
categories: introduction
tags: featured
image: /assets/images/mandolin.jpg
---

*Apologies for the length - there's been a lot to think about the last
few days. This is an initial, provisional attempt to formalize some
thoughts that came out of #lodlamto*

At the end of an interesting workshop on SPARQL at the
[#lodlamto](http://www.library.yorku.ca/lodlamto/) conference on Thursday, I
overheard two software developers talking about how unintuitive SPARQL
was to people with SQL experience (because SPARQL queries and SQL
queries are “false friends”). The two developers came to the conclusion
that SPARQL could safely be ignored because “no one industry is using
it”. I’ve come across this idea before – mostly from non
library-technology people who hear about linked data technologies from
someone in the library world. Linked data seems overengineered, counterintuitive,
and too heavy for most purposes. Now, most of us know about
non-library-specific linked data applications (like Google’s knowledge
graph, for example), but I got to wondering whether it was true that
linked data was not being used in applications outside the library
world. I put the question out on Twitter, and followed it up with the
“is it us?” question: are library technologists/metadata people obsessed
with linked data even though it’s not a widely used concept/technology,
or are other technology areas missing what seems obvious to us?

A few people chimed in with, I think, enough examples of linked data use
outside libraries and search engines to prove that linked data **is** being
adopted where it makes sense. But that’s an important distinction: it
seems clear after looking at the examples, that linked data satisfies a
particular data need, which is not a requirement for many technology
projects. And I think this cleared up for more (at least to a certain
extent) the boundaries of linked data as an approach to a problem.
Libraries, search engines, and social networks all have problems that
can be solved by linked data, but not all problems are best approached
from a linked data perspective. 

[Ron Houk](https://twitter.com/foafron) pointed out the Gnome project is using linked data
and SPARQL at least in some parts of its
[workflow](https://wiki.gnome.org/Projects/Tracker/Documentation/Examples/SPARQL/InSupport). 
[Mark Matienzo](https://twitter.com/anarchivist) suggested biomedical
informatics, [Steven Folsom](@sf433) pointed me to an ISWC2015 keynote
on [“Semantics and Inference Processing in Finance”](http://iswc2015.semanticweb.org/keynote-michael-atkin) 
and then what might be the most intriguing example of linked data use outside of
libraries, the linking of data to track those involved in [human
trafficking](https://news.usc.edu/81360/internet-search-tool-takes-on-human-traffickers/).
More technical information on the DIG project can be found [here](https://usc-isi-i2.github.io/papers/szekely15-iswc.pdf).

**Exploration in addition to Answers**

What I think is really interesting about all these examples, and what
connects to recent developments in the field of my day job (library
discovery systems) is that a graph is not meant to be simply an
aggregate of knowledge presented statically, it’s essentially meant to
be explored. In the discovery world, this idea takes the form of user
expectations moving from searching for and finding an item, to users
finding a set of results and exploring and doing more different kinds of
things with the results. In a sense, we’re talking about adding more
research and exploration to our systems, rather than just providing an
interface to a surrogate record. Karen Coyle has talked about this, most
recently in her SWIB15 talk, [Mistakes Have Been Made](https://www.youtube.com/watch?v=d0CMuxZsAIY). One thing that the
examples above makes clear is that the point of linked data is not
simply displaying some representation of the linked datasets, but
providing a data structure that allows for exploration and discovery
without requiring exploration and discovery connections to be made
explicitly by human beings (which is the case, for example, in the
authority structures of a library catalogue). 

At #lodlamto a lot of the benefit of linked data was exposed through the
kind of research question not easily answered by current relational
databases (e.g. “who was a fresco painter in Florence in 1344”, “how
many churches were renovated in Germany after the Second World War”).
The problem with these is not that they are more sophisticated than what
we might think of as a standard SQL query, but that that they remain
static: we query a graph and get back an answer (even if the answer is a
set of solutions). This is obviously a use case, but it is far from the
most interesting one, in my perspective. 

What linked data should give us is the ability to use a single static
query like those listed above as a transient point in the more fluid
exploration of the data in question. This functionality is mirrored in
the multiple patterns that can be included in a single SPARQL query.
While these graph queries can give us the answers to quite complex
static questions, but it also opens the way to using graph queries in a
more extensible and fluid way. 

So the publication or aggregation of linked data isn’t an end in itself.
What is important to libraries, to social networks, or to the DIG
project, is being able to start at any node or set of nodes (which is
likely the result of a query) and then being able to move from node to
node and graph to graph without any explicit linking by human beings,
thus making the possibilities of exploration potentially unlimited,
precisely because every linked data publisher can work independently, as
long as the data they publish is open, and reuses existing ontologies as
much as possible. 

**The Data Question**

One important concern here is not simply that we will reproduce the
existing problems libraries have in their data infrastructure in terms
of siloization, non-standard practices, and unwillingness or technical
inability to share, but that we will end up reproducing more subtle
problems in new (and hence less detectable ways). For example, the
critiques of controlled vocabularies Hope Olson performs in *The Power to
Name*, the critique of representation in authority and other kinds of
records Jordan Claire and Myron Groover spoke about at #lodlamto, and
Allana Mayer wrote about in ["Linked Open Data for Artistic and Cultural
Resources”](http://www.journals.uchicago.edu/doi/pdfplus/10.1086/680561), and the
recent debates around LCSH subject headings, all indicate problems with
the existing method of creating data within particular networks of power
and domination. That linked data has the capability not only of allowing
subaltern voices to be heard (“anyone can say anything about any topic”)
and also makes adding or modifying vocabulary terms much cheaper than it
is now, does not alter the fact that, living as we are within the same
networks of power and domination but now with linked data, we will have
to guard against and understand how to mitigate the very real coercive
force of such power when it comes to data, metadata, and vocabulary
control. One argument against vocabulary and ontology work being done in
isolation is the temptation to create a new vocabulary rather than reuse
existing ones; another argument can be made that the isolation of
vocabulary groups may have a tendency to reproduce the worldview of the
smaller group, leading to the same problems we have in, for example,
LCSH today. 

**The Interface Question**

In addition to the data problem, something similar exists with respect
to user interfaces. What I worry about is that one of the reasons it’s
difficult for some people both inside and outside libtech to see the end
result of linked data, is that our interfaces and our “understanding” of
user expectations and workflows are lagging behind our data,
infrastructure, and tools. If we use linked data technologies to drive a
standard library OPAC interface then we are doing our users a
disservice, as well as squandering the capabilities of open linked data.
Another concern is that work in linked data is currently being done
institution-by-institution, which involves a lot of duplication of
effort, code, data, etc. Instead, we should try to come up with the
relevant shared standards, tools, and techniques, to not reinvent the
wheel, and to allow each institution to focus on what they do that is
*actually* differently from all the rest, and move all of us forward
together. As with vocabulary and ontology development, this requires a
much closer working relationship between all institutions and
organization than hitherto exists. Any initiative in Canada around
linked data must be as open, transparent, and inclusive as possible.

**The User Question**

I’ve said before that one of the things many libraries are very bad at
is requirement gathering. Recognizing that user assessment and usability
testing is a subset of requirement gathering, it follows that many of us
are very bad at that too. Listening to [Alan
Harnum](https://twitter.com/waharnum) talk
about the immediate value to his users of the work he does, based on an
actual relationship with the users in question, is extremely edifying.
But Alan no longer works in libraries. There are many areas in which
libraries would do well to look outside the profession for guidance, and
requirement gathering/user assessment is certainly one of them. 
  
The connection to linked data, to my mind, is that without a close
relationship with the users of our tools and interfaces, it will be
nearly impossible for us either to let people know about the new
possibilities of a linked data infrastructure, or to understand what our
users actually need and want from us, or to recognize if an when we have
satisfied their needs. The end result, of course, is business as usual,
and the same inadequate tools and interfaces that libraries have had to
live with for a long time. Linked open data and open source software
give us the ability to go beyond the limits of an outdated data model
and shoddy vendor-supplied tools and interfaces. We shouldn’t squander
the opportunity. 


**Openness, Publication and Consumption**

But even a focus on building tools and interfaces may not be the best
place to put our energy. We are increasingly aware that the main library
interfaces are being bypassed by many users, who prefer to search for
resources on the open web, then use more-or-less transparent library
tools (e.g. the library proxy) to gain access to licensed resources. We
ought to be taking a hard look at the time, effort, and energy we put
into applications that may not even be used. 

More importantly, like government organizations, libraries no longer
need to have a monopoly on their applications. It is currently extremely
difficulty to expose library data efficiently, either due to proprietary
APIs, or data locked down either through licensing, technology, or
privacy concerns. Linked open data may be the key to liberating our own
data for use by other application developers. We have seen how opening
up transit data encourages people to write applications more quickly and
with higher quality than applications written by (or for) the transit
service itself. With linked data, we can expose our data secure in the
knowledge that it is immediately linkable with other data sets, built on
a simple, solid data model, so that others can reuse and repurpose the
data as desired. 

It is always tempting to see social formations reflected in technology,
to imagine that the flat structure of linked data and the AAA principle
reflects a democratization of our data model and vocabularies. Perhaps
that will turn out to be the case, but it is much more likely that our
understanding and application of linked data principles will be less
than adequate or incomplete, or that the system of domination in which
we live will continue to distort our best intentions, as it always does.
The problem of breaking out of our own histories, our own institutional
and organizational cultures, in order to make linked data really work,
not for us, but for the people and communities we serve, is a difficult
one. All we can do right now is, on the one hand, attempt to broaden and
deepen our knowledge and skills, continue to fight for the open (source,
access, data) against closed (systems, code, minds), and keep speaking
up about the ways in which our current data practices reflect oppression
and inequality in our societies at large. 

**Much of this blog post came out of discussions at #lodlamto, held at
Ryerson and York, May 12-13, 2016, and in conversation with John Fink,
Ruth Collings, Myron Groover, Alan Harnum, Kim Pham, Allana Mayer, Robin
Desmeules, MJ Suhonos, Tom Johnson, Gillian Byrne and Christina Harlow, for which I am grateful**
