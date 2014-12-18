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

{% highlight xml %}
 <record>
  <leader>-----nas-a2200000z--4500</leader>
  <controlfield tag="008">141216uuuuuuuuuxx-uu-|------u|----|eng-d</controlfield>
  <datafield tag="010" ind1="" ind2="">
   <subfield code="a">sc 78001886 </subfield>
  </datafield>
  <datafield tag="245" ind1="" ind2="0">
   <subfield code="a">ABCA bulletin</subfield>
  </datafield>
  <datafield tag="210" ind1="" ind2="">
   <subfield code="a">A B C A BULLETIN</subfield>
  </datafield>
  <datafield tag="260" ind1="" ind2="">
   <subfield code="a">Urbana, Ill.,</subfield>
   <subfield code="b">[American Business Communication Association]</subfield>
  </datafield>
  <datafield tag="022" ind1="" ind2="">
   <subfield code="a">0001-0383</subfield>
  </datafield>
  <datafield tag="090" ind1="" ind2="">
   <subfield code="a">954921332002</subfield>
  </datafield>
  <datafield tag="866" ind1="" ind2="">
   <subfield code="a">Available from 1969 until 1984. </subfield>
   <subfield code="b">$obj-&gt;parsedDate('&gt;=','1969',undef,undef) &amp;&amp; $obj-&gt;parsedDate('&lt;=','1984',undef,undef)</subfield>
   <subfield code="c">G</subfield>
   <subfield code="s">3230000000000051</subfield>
   <subfield code="t">3230000000000047</subfield>
   <subfield code="x">SAGE Deep Backfile Package:Full Text</subfield>
   <subfield code="z">10920000000045475</subfield>
  </datafield>
  <datafield tag="650" ind1="" ind2="4">
   <subfield code="a">Business, Economy and Management</subfield>
   <subfield code="x">Trade and Commerce</subfield>
  </datafield>
 </record>
 {% endhighlight %}
