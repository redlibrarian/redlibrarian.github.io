---
layout: post
title: "Beyond IP Authentication in Libraries"
date: 2017-11-23
categories: article
tags: featured
image: /assets/images/mandolin.jpg
---

I haven't paid much attention to developments going on in the vendor
world around alternatives to IP authentication until recently. Yes, the
current duct-tape-and-glue solutions libraries have are
[broken](https://redlibrarian.github.io/article/2017/02/01/library-systems-disaster.html),
but that's nothing particularly new. And yes, Shibboleth has been around
at least since I started in libraries, but vendors have never really
gotten behind it before now. It seemed that the EZ-Proxy/IP-based
authentication status quo was here to stay.

But recently all that seems to have started to change. In response to a
problem with one of our vendors, we managed to get a few databases to
configure Shibboleth as an alternative to use when IP/proxy
authentication fails. This introduced uncertainty not only into the
systems, but into public service, where users now had a choice to make,
and instructions were no longer as straightforward as they were under a
pure IP/proxy regime.

Next, our collections unit received a few emails referring to Google's
Context-Aware Scalable Authentication (CASA). An example is this announcement from
[HighWire](https://www.highwirepress.com/thought-leadership/news/highwire-press-present-casa-campus-access-protocol-google-charleston),
the gist of which is:

>CASA enables Google Scholar users to see the same subscribed resources
>off-campus as on-campus, so that no off-campus login is necessary.
>HighWire and Google combined expertise to develop and test the CASA
>protocol with the goal of simplifying verified user access to
>subscribed content. A faster, easier user experience for legitimate
>users to access content on publishersâ€™ platforms will help libraries
>serve their patrons and may influence researchers who have developed a
>preference for Sci-Hub.

As I understand it, what CASA does is assembles a profile of what a user
(in this case, a Google user)
has licensed access to, based on various "passive" characteristics, one
of which *may* be "is currently at an institution with licensed access".
This profile then follows the user around even when they are outside
that institution, i.e. off campus. The authentication is associated with
the Google profile, so that Google user can have access whether or not
they are on an allowed IP. This access can be time-limited, so that a
user would have to return to a licensed campus to reenable their CASA
access, but I don't think this is part of the spec.

(This raises some questions around how this will work in practice. Since
members of the public are generally able to access library resources on
campus, this would give someone unaffiliated with the university -
someone who would not normally have EZ-Proxy access, a member of the
public - the ability to
access licensed resources simply by visiting the campus occasionally. This isn't something I'm particularly worried about, but vendors will have to figure out a way to close that hole).

More technical details on CASA can be found
[here](https://www.m-iti.org/uploads/Ian_CASA_SOUPS13.pdf).

Third, we have [ra21](https://ra21.org/), which stands for "Resource
Access for the 21st Century:

>
RA21â€™s mission is to align and simplify pathways to subscribed content
across participating scientific platforms. RA21 will address the common
problems users face when interacting with multiple and varied
information protocols.

ra21 is spearheaded by the International Association of Scientific,
Technical, and Medical Publishers (STM) and the National Information
Standards Organization (NISO), and has *lots* of library vendor support
(the [steering committee](https://ra21.org/index.php/about/) contains many vendors and organizations familiar
to libraries). It's clear that a sea-change is coming in the move away
from IP-based authentication.

When I mentioned this in a public service committee yesterday, I was
asked why vendors would want to to do this and what they would gain by
it. It's clear, I think, that the main impetus is the simplicity and
usability of SciHub. As I've written before, access to licensed library resources is barely
usable, extremely fragile, and frustrating to users (even when they
*are* able to get access to a desired resource. SciHub, on the other
hand, is basically the simplest access tool around: type in a title or
identifier, hit enter, read PDF. We know the vendors and publishers are terrified of
the ramifications of SciHub, and it looks as though rather than working
with libraries to come up with a solution, they are simply taking it out
of our hands.

But there are other reasons vendors and publishers would be behind these
systems. More granular monitoring of usage will make it easier to quash
abuse (rather than, as now, reporting possibly abusive IPs to libraries
to have them deal with). Linking access to profiles rather than IPs or
IP ranges will make it easier to track and target individual users (both
for marketing and for "filter bubble" purposes). Vendors probably also
hope that linking usage to a vendor (as opposed to a library) profile
will help uncover accounts which have been compromised (i.e. to SciHub),
as well as being able to monitor and block access *from* SciHub using a
compromised profile. I'm sure there are other benefits, but these alone
are likely sufficient to make moving in this direction worthwhile for
vendors and publishers.

From the library perspective, however, things aren't quite so simple.
Our access systems might be broken but they are a) well-understood and
b) fairly standardized. Most libraries use EZ-Proxy, for example. The
new non-IP ecosystem currently has three major players: Shibboleth,
Google's CASA, and ra21. More alternatives may develop, fracturing the
authentication landscape and causing a massive headache for systems
libraries, electronic resources, collections, and public services. In
addition, the implications for user privacy are frightening. Recent
debates in the library world around user monitoring pitted "pragmatic"
views on tracking/monitoring against a (happily very vocal) majority who
are unwilling to compromise user privacy for the sake of some assessment
metrics. Putting authentication firmly in the hands of our vendors will
throw all that out the window. Google's CASA, for example, will link a
user's scholarly research and reading with everything else in their
Google profile, including location, and all of this will be a complete
black box to libraries and their users.

To my mind, this constitutes a major, major change in the way we provide
access to electronic resources. I think the end result is likely to be
positive, as almost anything must be better than what we have now, but
in the short term, the ramifications for all areas of the library,
especially public services, are enormous, and the implications for
privacy unnerving.

Update 24/11/2017:

In a conversation last night, [Ruth
Collings](https://twitter.com/collingstruth) pointed out that another
way vendors can/will benefit from the fracturing of authentication
systems is by continuing the trend of building walled-gardens. As we've
seen over the last few years, the library vendor ecosystem has been
consolidating into fewer and fewer hands. One strategy in this
consolidation seems to be to acquire as many user tools as possible
(discovery system, citation management, knowledge base, etc) in order to
keep libraries, faculty, and students locked in to a single vendor's
system. In this sense, the vendors are simply following the model of,
say, Apple or Google, in which proprietary hardware and software, and
closed protocols and applications, serve to lock users in to a single
corporate system. By fracturing the authentication/access landscape, it
is only too plausible that vendors will use their own, proprietary,
authentication system to lock a particular library into their own suite
of closed systems and services.

Update 27/11/2017:

<blockquote class="twitter-tweet" data-partner="tweetdeck"><p lang="en"
dir="ltr">Hey Sam. As I recall, RA21 is effectively an application
profile of Shibboleth, so really there are two: straight-up Shibboleth
and an RA21-profiled Shibboleth. Thanks for the mention of Google&#39;s
CASA; that was a new one for me.</p>&mdash; Peter Murray (@DataG) <a
href="https://twitter.com/DataG/status/935239933685583873?ref_src=twsrc%5Etfw">November
27, 2017</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js"
charset="utf-8"></script>

