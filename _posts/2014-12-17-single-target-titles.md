---
layout: post
title: "Single Target Titles"
description: ""
category: 
tags: []
---
{% include JB/setup %}

Extracting Single Target Titles from SFX Data
=============================================

Over the course of 2014, I've been involved in some initiatives [supporting librarians learning to code](http://software-carpentry.org/). I've taken as many opportunities as I can to explain why I think computer programming is an important skill for all librarians, both in library systems departments and elsewhere. As the first post on this new blog, I thought I would walk through a recent programming task that is fairly representative of the kind of thing I'm called upon to do, and the kind of task that coding can help solve. 

For those unfamiliar with the inner workings of library e-journal subscriptions, [SFX](http://www.exlibrisgroup.com/category/SFXOverview) is the name of a widely-used link resolver from [Ex Libris](http://www.exlibrisgroup.com/). Basically, it consists of a knowledge-base of e-journal metadata aggregated into e-journal vendor packages called targets. When a library purchases or licenses an e-journal, the target and the journal are activated in a local copy of your SFX knowledge-base. A certain amount of reporting is available within the SFX admin interface, but as usual with third-party software, sometimes you want a little more than the software can give you. One report our serials team occasionally asks me to run is "which e-journals are only available only from one given target" (because libraries often have multiple e-journals from different sources covering different date ranges - don't ask). The last time I was asked for this report, I wrote a Ruby program to produce the report. As this was before moving to GitHub, I have no idea what happened to that code. The code itself was probably suspect anyway, as it was before fully adopting [Test-Driven Development](http://en.wikipedia.org/wiki/Test-driven_development), so I felt I was better off rewriting the program from scratch using TDD. 

E-journal subscription information can be extracted from SFX as [MARC](http://www.loc.gov/marc/) records, encoded in [MARCXML](http://www.loc.gov/standards/marcxml/). The subscription information is contained in the MARC 866 tag within each e-journal record, and a sample record looks something like this:
