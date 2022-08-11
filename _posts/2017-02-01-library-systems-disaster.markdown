---
layout: post
title: "The Library Systems Disaster"
date: 2017-02-01
categories: article
tags: featured
image: /assets/images/mandolin.jpg
---

As someone who has worked in library systems/discovery for nearly ten
years, I knew our systems had problems, but I generally thought they
made the best of a bad situation. I've used academic libraries for three
degrees, and in general, they were fine - they served their purpose. But
I've been thinking more and more lately about user experience, and also
about the totality of how our systems work together to solve whatever
problem they're supposed to solve (note: I'm being purposefully vague
right now as to what that problem is).

I think one of the reasons systems librarians think things are working
*OK* is because a) we know the constraints within each system and b) we
tend to work on particular problems connecting two pieces of the puzzle.
It's hard for us to think in terms of the entire process that a user has
to go through when trying to find or get access to material. Think about
the applications/systems that are involved in a basic discovery system search
leading (one hopes) to full text:

* The library website
* The discovery system (and article databases)
* The metadata
* The link resolver
* The proxy

This doesn't address what users need to do *within* each of these
systems, which - when they work - can range from the simple ("enter your
ID and password") to extremely confusing (a user enters an endless
discovery-system/link-resolver loop, for example).

Last night I was trying to track down the full text of some book reviews
I had written in the early days of my career, which I didn't think to
keep. Knowing - as our students and faculty do - that our library
systems are at best OK and at worst actively bad, I started out in
Google. But the journals I published these book reviews in aren't open
access, and I find nothing, so I turn to a journal-title level search in our discovery
system (because I can't remember the titles of the reviews themselves).
I track down the journal, and inside the proprietary database I do a
search within the journal for my last name. Nothing comes up. So a
broad-based search in Google has failed and a narrower search in a
particular journal has failed. At this point, if I was a student, I
would give up and hit the pub. But I'm a professional. So I turn to one
of the discovery services that my library licenses (Ebsco). A search for the
journal title and my last name finally pulls up some results. I'm
off-campus, so before I can click into any of the results I have to be
redirected to our proxy and log in.

Once inside the record, I notice (because I know what I'm looking for) that the actual PDF is not available in the discovery system, so I have to click on our
link resolver. This gives me two options, one of which is the publisher
database I've already tried. That should be the canonical record, right?
But that link takes me to the journal home page, where I already know I
can't find the article. The second link in the link resolver menu is to
an Ebsco database. I've just been searching Ebsco, so I figure that
won't work because I already know the record doesn't have the PDF. But
when I click on the link I *am* taken to an Ebsco record with the PDF. I
get my full text.

Now, this account leaves out many of the issues within, for example,
the discovery system (e.g. relevancy, search optins, configuration,
database activation, etc), which are also esoteric and hard to get right
for users (but as David Fiander points out "discovery systems are sold
to librarians, not to users"). Having said that, just the fact that all
these different systems have to be hooked together in slapdash ways
forced on us by vendors, by lack of staff time, by outdated application
architectures, means that, in my view, we can't keep tinkering with all
the bits and pieces that make this work and hope to - in the end - have
a successful method for students, faculties, and researchers to do what
they want.

And we can't presume to know exactly what they want. As library workers,
we can't (and we shouldn't) try to guess in advance every use case. User
stories and personas, in my view, have been an attempt to try to guess
use cases, rather than focusing on user-centred design and development
which is abstract and flexible enough to allow for any use case.
Known-item search and contextual browse shouldn't be a zero-sum game.

The vendor solution to all of this is, of course, "buy our new thing!" -
that new thing being cloud LSPs with integrated link resolver and proxy.
But we all know that under the hood, a vendor's cloud LSP is just
hooking those pieces together (with duct tape and glue) the way we're
doing it right now. Also, one of the major issues is quality and
interoperability of metadata - publisher metadata, when it isn't of
abysmally bad quality, doesn't necessarily follow any of the myriad
standards the library world has come up with. Two different vendor
records for the same item can appear radically different. And since we
trigger system behaviour off metadata (for example, constructing a link
resolver URL), the presence or absence of a single field can bring the
whole house of cards down.

It's disheartening to think that the systems you work on are not only
pretty crappy, but that there's no feasible way of fixing them. We can't
redesign our existing systems - they are already in production, and we
have so much else on our plates. However, we may -
as a profession - need to decide that we're going to tear everything
down and start from scratch. But I'm afraid that the library world's
solution will end up like the library's world's solution to
institutional repositories: enormous monolithic systems which are hard
to implement and are unclear as to the problem they're trying to solve
(institutional memory? long-term preservation? humanities computing
corpuses? big data?)

I think we need to start again, but from two "open" principles: one is
an open knowledge base. This has been raised before, but the more I
think about it, the more I think this is the number one thing we could
do to improve our systems. We have to stop relying on vendor or
publisher records, especially when those are locked in proprietary
systems. If every cataloguing department in North America divvied up the
journals that are currently being published, we could produce
high-quality records and put them in an open knowledge base for everyone
to use. (I know there are open KB project out there; I don't know how
mature they are, and I haven't heard any library talk about adopting
them). Proprietary KBs are what keep us from moving to 100% open-source
systems (writing a proxy, a discovery system, or a link resolver is not
hard, but you need the data).

Secondly, we need to create data models that are not conceptual models.
As someone mentioned this morning on the BIBFRAME listserv, in his
opinion BIBFRAME is doomed to fail in part because of the super-heavy
conceptual nature of the model. Our systems need simple, lightweight
models that we can build simple, lightweight APIs on top of.

There's a lot more that we would need to do to build library systems
that actually work for people, but these are two things I think we would
have to commit to at a bare minimum.
