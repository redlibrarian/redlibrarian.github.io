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
 
As you can see, in the 866 field, each subcode contains information about the subscription package. One thing to bear in mind is that the display name of the target ("SAGE Deep Backfile Package: Full Text") is not the same name used in the SFX knowledge-base. Subfields *s* and *t* contain identifiers which *are* used internally. The serials team generally gives me the knowledge-base name of the target they're interested in, so I either have to ask them for the ID number, or find it out myself. 

The code for the program itself is not difficult, though there are a few tricky places. I find it's easier to approach and work out the tricky parts using test-driven development. In this case, I'm using basic [minitest](https://rubygems.org/gems/minitest), a common Ruby testing framework. The first test is simply to read the SFX data extract and load it into a Ruby object in order to work with it. The full [test file](https://github.com/ualbertalib/sfx_scripts/blob/master/single_target_report/single_target_test.rb) begins with a simple set up, and then tests to see that our object ends up populated with e-journal records (my test data file contained 14 records; the full data set contains around 100,000):

{% highlight ruby %}
 def setup
    @single_target_titles = SingleTargetTitles.new("test_sfxdata.xml")
  end

  def test_object_contains_records
    refute_empty @single_target_titles.all
    assert_equal 14, @single_target_titles.all.size
  end

{% endhighlight %}

After writing the test, of course, it's time to write the code to make the test pass. 

{% highlight ruby %}
require "marc"

class SingleTargetTitles

  attr_reader :all, :matches

  def initialize(datafile)
    begin
      data = MARC::XMLReader.new(File.open(datafile))
    rescue => e
      puts "Unable to open file. Exiting (#{e})"
      exit
    end
    @all = data.entries
  end
{% endhighlight %}

After the red (tests fail) and the green (writing code to make the tests pass), it's time to refactor. There really isn't much here to refactor. I don't love the "exit" statement, so I could look into whether there's a way to clean that up, but it's not too bad. On to the next test:

{% highlight ruby %}
 def test_query_results
   query_target = "1000000000001505" #="EBSCOHOST_ACADEMIC_SEARCH_COMPLETE"
   refute_empty @single_target_titles.matches(query_target)
   assert_equal 2, @single_target_titles.matches(query_target).size
 end
{% endhighlight %}

Now we're getting somewhere a bit more interesting. This test passes a target ID (in this case, the ID for Academic Search Complete) to the class of e-journal records and returns the records that match the query. The test itself is simple: pass a target ID to the #matches method and it should return which e-journals belong to that target. Because I'm using a small test dataset, I know exactly how many e-journals should be returned. The code to make this test pass is:

{% highlight ruby %}
def matches(query)
   @matches ||= search(query)
end

def search(query)
  @all.each_with_object([]) do |record, matches|
  matches << record if ((record['866']['t'] == query) || (record['866']['s'] == query))
  end
end
{% endhighlight %}

Notice how I'm explictly only testing one method (#matches), but I've written two. I don't need to explicitly test the #search method, because if it doesn't work, neither will #matches. In [Practical Object-Oriented Design in Ruby](http://www.poodr.com/), Sandi Metz talks about testing to an object's interface: 

> Tests should concentrate on the incoming or outgoing messages that cross an object's boundaries. The incoming
> messages make up the public interface of the receiving objct. The outgoing messages, by definition, are incoming
> into other objects and so are part of some other object's interface. (POODR, p.196)

