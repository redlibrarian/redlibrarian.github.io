---
layout: post
title: "The ILS and Systemic Generality"
date: 2017-02-12
categories: article
tags: featured
image: /assets/images/mandolin.jpg
---

"simplicity buys you power" -- [Daniel
Higginbotham](http://www.flyingmachinestudios.com/programming/hey-rubyists-try-clojure/)

1. Complexity and the ILS

At a recent presentation about FOLIO, I was reminded of conversations
that took place a couple of years ago with Gillian Byrne and others
around the idea of "disintegrating" the ILS. The "integrated library
system" which developed out of early library automation initiatives and
is now morphing into the "library services platform" (essentially, a
modular ILS in the cloud). One of the aspects of our conversation was
that, perhaps, the integration of the ILS was a cost, not a benefit, to
library work. From my perspective, this idea grew out of an increased
decoupling of the OPAC from the rest of the ILS, which has culminated in
my own work with an implementation of Blacklight at University of
Alberta Libraries.

Working with a decoupled OPAC has lifted many of the constraints
inherent with working with a legacy, proprietary ILS: we are not limited
in data or document format, for example, nor on clunky, outdated,
essentially pre-web UI technologies. We are also free, down the road, to
switch out the ILS layer and keep our Blacklight implementation. Since
Blacklight only requires MARC records from the ILS (and some user-facing
functions accessed via API), it is agnostic as to the underlying system.

One of the things that came out of the FOLIO discussion was some more
information about the underlying system layer of the project. Below the
OKAPI microservices platform, FOLIO plans to have a databases (SQL or
NOSQL), an indexer (probably Solr), an object repository (Fedora), and a
few other storage applications. It's argued that this will allow FOLIO
to accept and manage many more different formats and object-types than
ILS' currently can. Libraries can substitute other applications for any
of these pieces (say, ElasticSearch for Solr), but for most libraries,
this layer is encapsulated by FOLIO - they access the system layer
through OKAPI, and in any event the system stack lives in the cloud.

Another thing that came up was the fact that, as the FOLIO rep put it,
SirsiDynix' BlueCloud is a suite of services built on top of Symphony
(one of SirsiDynix's ILSs), which raised a red flag for me, because
marketing and selling a modern LSP which is fundamentally built on top
of an out-of-date, basically obsolete application, seems at best a bad
idea, at worst a scam [1]. If the LSP is meant to take advantage of modern
archiectures and technologies, building it on top of a legacy ILS would
be like putting a Tesla body on top of an Edsel. It turns out things
aren't quite so dire - according to the BlueCloud documentation,
SirsiDynix had the chance to redesign and re-implement the database
layer of their existing ILSs and chose not to, ostensibly in order to
focus on more important things (given that, according to them, their
database architecture and design decisions were solid and well-founded).

Even if this is the case, and they haven't based BlueCloud on Symphony,
this is still problematic. The Symphony database can still only handle
records in a small number of formats (i.e. MARC), its indexes are still
built on outmoded conceptions of search, discovery, and access, and it
likely still tightly couples the database design to a database implementation
(can you use MongoDB with BlueCloud, or do you have to use Oracle?).

What is common in both these characterizations of the database or system
layer is an insistence on the part of vendors for an encapsulated
solution that on the one hand hides complexity from people who work with
the system, and on the other hand makes libraries even more dependent on
vendor-supplied solutions for maintenance and support (Ebsco's avowed
business-model with the FOLIO project). However, there is something
disingenuous and self-serving about this particular instance of hiding
complexity. It gives vendors an incentive to *increase* complexity
contrary to best-practices and industry standards, or at least not to
actively reduce complexity (anyone who has had to log in to an SFX
server and work directly with the software knows what I'm talking about). But even worse than that, it doesn't *in fact* reduce
the complexity presented to the library worker, it simply shifts it.
Managing, for example, the printing of library slips or user-rules
within an ILS are mind-numbingly complex. The
next-generation library systems like Primo and Summon hide the
underlying complexity of the database systems and ETL pipelines, but
anyone who has worked with Primo's normalization rules and pipelines
will know that this doesn't save on cognitive load, skill, training, or
experience required to configure the system. The people who understand
these things tend to become single-points-of-failure in a library
system. And since there are so many of these pieces within the ILS, the
library systems ends up with many people who understand a single piece
of the ILS *really well*, but that knowledge isn't shared (indeed, it's
barely shareable). Again, the end result is that we rely even more on
vendor support, but it also means that the cost of moving away from a
given system, which is already high, becomes even higher: imagine all
those single-points-of-failure who now have to learn an entirely new,
entirely different, equally overcomplicated system.

One of the thought-experiments systems librarians sometimes like to
undertake is to imagine the smallest, lightest stack of open-source
tools on which you could build a library system. The great thing about
many open-source applications, take Solr for instance, is that they are
multi-purpose. You can index anything in Solr, not just bibliographic
data. On the other hand, ILS modules (circulation, cataloguing, OPAC)
are built for a single purpose. Just as many people won't tolerate
single-purpose gadgets in their kitchen, why do we tolerate
single-purpose gadgets in our library systems? If, indeed, these modules
made things simpler and easier for staff, that would be a good argument
in their favour, but they don't - the complexity is simply shifted to a
different part of the workflow.


2. Clojure and Systematic Complexity

The ILS (and the LSP) then, are not *complex* per se; they are
*complected*, a word coined by Rich Hickey, the inventor of Clojure, to
describe systems which are composed of simple things, but are made
complex through entanglement of their simple pieces (see [Simple Made
Easy](https://www.infoq.com/presentations/Simple-Made-Easy) and
[Simplicity Matters](https://www.youtube.com/watch?v=rI8tNMsozo0) ). In essence, the
"integratedness" of the integrated library system is the problem. Not
only are many disparate technologies employed "under the hood" (a
telling phrase) in the ILS, but this entangling is hidden from the
users, making their work not so much complicated as complected. Working
with library data in a system should be simple, but it has been made
complex.

Now, one of the principles of Clojure is simplicity, and one of the ways
in which it is simple is through what has been called "systemic
generality". In the [*Programming
Clojure*](https://pragprog.com/book/shcloj2/programming-clojure) book, this is introduced
alongside one of the [programming
epigrams](http://www.cs.yale.edu/homes/perlis-alan/quotes.html) by Alan J. Perlis: it is
better to have 100 functions operated on one data structure than 10
functions on 10 data structures. In Clojure, rather than the myriad
classes, arrays, and hashes that get created in a given object-oriented programming [2], Clojure
programming relies upon the use of a few very simple collection types.
Rather than creating a new datatype (class) for a specific kind of data
(i.e. describing or modeling your data with a class), you simply use
Clojure collections (mainly vectors and maps) in order to hold any kind
of data you're working with.

This systematic generality, this lack of specific classes in favour of a
few generalized data types that are used *everywhere* really does reduce
the complexity of an application. Vectors and maps are not
single-purpose data types, like a applicationVectorModeBitstreamPipeline
class might be in Java; they are general purpose. It's much easier to
remember how to use two generic types like vector and map than to
remember dozens or hundreds of specific classes, depending on the size
of the application.

In this case, then, what if we moved the skill and experience required
by a library worker away from the one ILS module they know inside-out,
to a reusable component that is likely to be understood by more people
in a system, simply through its generality and reuse. A circulation
module is a database of transactions; a user module is a database of
users; a cataloguing module is a database of bibliographic records.
Currently, the people who understand the circulation module share little
or no knowledge with those who understand the user module or the
cataloguing module, simply because these modules have been made
overspecific and overcomplex. If, instead, we used a database (or
tables) for circulation, a database (or tables) for users, and a
databsse (or tables) for cataloguing, then all of a sudden we have three
people who share knowledge and expertise because they're all working on
the same kind of thing (a database). Similarly, an OPAC is just a
website, but working with an OPAC in an ILS is painfully different from
working on a webpage (and I have no expectation that this will be
different with an LSP), so if we instead made the OPAC a website then,
through systemic generality, anyone who works with the web can work with
the OPAC and vice versa. This helps build in-house capacity and reduce
single-points-of-failure (though it still leaves the problem of small
libraries, addressed below).

Given that none of the proprietary LSPs (Alma, BlueCloud and, one
assumed, FOLIO) can be expected to reduce complexity, as that would
reduce the means by which they can be paid for maintenance and support,
maybe the time has come to disintegrate the ILS not only in the sense of
breaking apart its modules, but of getting rid of the idea of an ILS
module altogether. Let our ILS administrators be database
administrators, our OPAC programmers web programmers, our cataloguers
simply people who work with a particular database interface so that
their expertise can be about cataloguing and metadata and not taken up
with (what should be) irrelevant things like how to use the cataloguing
client.

Obviously, this still leaves the problem of smaller libraries who can't
afford to have a database administrator or programmer. However,
currently these smaller libraries are limited to vendor support for
their ILS problems. Applying the kind of systemic generality I've been
talking about would allow them to get support from *any* database
administrator or web developer. It would bring library technology more
in line with standards and best-practices and help us to overcome the
library exceptionalism that plagues our culture (and not just in
technology). For all libraries, big and small, it would reduce if not
eliminate the stranglehold our technology vendors have on us and,
through competition, ought to reduce costs as well.

NOTE: I haven't talked about open-source ILSs in this post (Evergreen or
Koha). My sense is, while conforming more to standards, best-practices,
and generality, they still suffer from the probems of complectedness.
They also have an ecosystem of support-vendors which has grown up
alongside them. I'd be happy to hear from anyone who has recent
experience with the open-source ILSs to know how that sector stands
right now.

[1] This has actually been confirmed for me by a few other people since
I first put up this post. The BlueCloud documentation, then, is being at
best disingenuous when it talks about the database layer.

[2] OO languages "use the same constructs for modeling
values as they do for identities, objects, and default to mutability,
causing all but the most disciplined programmers to create many more
identities than they should." [Values and Change: Clojure’s approach to
Identity and State](https://clojure.org/about/state)
