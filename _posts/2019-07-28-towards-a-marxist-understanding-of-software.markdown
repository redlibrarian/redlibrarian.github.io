---
layout: post
title: Towards a Marxist Understanding of Software
date: 2019-07-28
categories: article
tags: featured
image: /assets/images/mandolin.jpg
---

>The machine... is a mechanism that, after being set in motion, performs
>with its tools the same operations as the worker formerly did with
>similar tools. (Capital, Chapter 15, p. 495).

For Marx, a machine consisted of three parts. In modern terms, the power
supply, the transmission mechanism, and the powered-tool itself. A few
differences in detail - we mostly convert a power source (wind, sun, fossil
fuels) to electricity in order to use it - should not prevent us from
seeing the essential continuity between the machinery of Marx's day and
contemporary computerized machines. Indeed, robots fit this schema
exactly, because we consider robots to be powered-tools rather than...
well, whatever we think a computer is (I will return to this question in
a moment).

In their recent book, *Inhuman Power: Artificial Intelligence and the
Future of Capitalism*, Nick Dyer-Witheford, Atle Mikkola Kjøsen, and
James Steinhoff draw a rigid distinction between robots and AI. Basing
their understanding of robotics on Alan Winfield's definition,
Dyer-Witheford, Kjøsen, and Steinhoff argue that while "all robots have
bodies", "AI is software and, therefore, need not be embodied, though it
requires computing hardware to run on" (10). It seems to me that this
distinction is spurious: what is the difference between a robot "body"
and the hardware that runs software? The rest of Winfield's definition
states that robots (but not computers) can sense and act on their
environment, and that they can "autonomously carry out useful work".
However, consider a light-monitoring application in a so-called "smart
home". It can sense the light levels within the house, and it can turn
on or off various lights to fit the parameters of the "useful work" it
has been programmed to perform. Is this a robot or a computer?

I think the distinction between robots and computers stems from two
things. In the first place, robots are seen as a *continuation* of
earlier automation technologies while computers are seen as something
radically new and different (Lovelace and Babbage's engines
notwithstanding). In the second place, robots were originally
"hard-coded", that is, their function was determined through the
physical operation of parts, rather than by a separate, programmed
control mechanism (software). (Early computers operated like this too,
of course, but Turing's theoretical papers consigned this fact to a
historical curiosity, easily ignored). The fact that robots are now
software-driven is ignored in maintaining a hard distinction between a
computer and a robot. In fact, there is pretty much no difference: a
robot can be understood as a computer with a particular set of
peripherals. The distinction between robot and computer is historically
determined, but does not hold up in contemporary terms.

But what about software. Despite their caveat that software "requires
computing hardware to run", Dyer-Witheford, Kjøsen, and Steinhoff claim
that "software... need not be embodied". If robots are embodied, and
there is no real distinction between robots and computers, then the idea
that software need not be embodied collapses. As the adage goes, "the
cloud is just someone else's computer".

I think that the mistake made here stems, again, from the early days of
the computer. For Turing, in his 1938 paper on the Entscheidungsproblem
in which he defines the Turing machine, the computer is a virtual
machine whose purpose is computation. For Norbert Wiener, on the other
hand, the computer is a control mechanism for the performance of work.
In *The Human Use of Human Beings: Cybernetics and Society*, Wiener writes that:

>The development of these computing machines has been very rapid since
>the war. For a large range of computational work, they have shown
>themselves much faster and more accurate than the human computer. Their
>speed has long since reached such a level that any intermediate human
>intervention in their work is out of the question. Thus they offer the
>same need to replace human capacities by machine capacities as those
>which we found in the anti-aircraft computer. (151)

Wiener does not draw a distinction between the "virtual" machine
performing computations and the material effects of computer labour in
the real world. Computer scientists, it would appear, side with Turing,
math, software, virtuality, and disembodied computation; engineers, like Wiener,
side with work, hardware, materiality, and robots. The robot-computer
distinction is a cultural one as well as a historical one. These
distinctions, then, do not arise empirically, but are a priori ones
*brought to* the study of or work with technology by the people
involved.

In terms of software in general and AI in particular, the dominant
discourse is that of disembodied computation leading to "thought",
"reasoning", and "understanding". We take the arguments of AI
researchers at face value that these anthropomorphized terms are
accurate descriptions of what AI software does. There are the usual
caveats that a computer does not "think", "reason", or "understand" in
the same way as human beings, but nonetheless what they are doing can
and must be considered in these anthropomorphic terms. The hard-and-fast
distinction between robots/hardware and AI/software above is explicitly
stated by Margaret Boden in her classic AI text *Artificial Intelligence
and Natural Man*:

>One thing, however, is certain: artificial intelligence is not the
>study of computers. Computers are metallic macchines of intrinsic
>interest to electronic engineers but not, as such, to many others.
>[...] It would be more accurate to say that artificial intellifence is
>the study of computer programs. (3)

It must pain AI researchers to have to care about such things as FLOPs
and Moore's Law, which must appear as a "revenge of the flesh" to those
who wish they could concern themselves purely with mathematics,
statistics, and computation.

This brings us around, then, to the question of software. We could
approach the question purely from a Turing-AI perspective and say that
software is the "mind" of the machine, no matter how simplified (indeed,
one of Boden's recent works is titled "mind as machine"). Or we could
understand software as the extension of Marx's three-part conception of
the machine to encompass a fourth part: the control of the machine
itself. This would fit with Wiener's more cybernetic perspective - and
indeed, the word "cybernetics" comes from the Greek word for
"steersman". So software is never disembodied, but always "steers",
governs, or controls hardware - hardware which is the condition for
the software's operation. (There is probably an argument to be made that
the software/hardware dualism simply reproduces Cartesian dualism in
mechanical form; we are arguing here for a monist perspective).
Software, then, is *the automation of the labour of the worker who
controls a machine*.

As we know from the history of technology, before a task can be
automated, it must be broken down into its simplest parts. The simplest
parts of a decision-making governor is predicate logic, the logic on
which all computation and software are built. The IF-THEN-ELSE branches
and FOR loops of computer programming are the crudest representation of
human decision making, and the simplest version of it necessary for
controlling computers/robots. The list of steps into which a problem or
task is decomposed is the *algorithm*; there is nothing mysterious or
nefarious about algorithms (though they do, of course, encode human
values, biases, and prejudices).

As the work we require of our machines becomes more sophisticated, so
too do the control mechanisms. We find that the logical and object
structures encoded in traditional programs are no longer fast enough,
parallelizable enough, or efficient enough to do the "useful work" we
ask of them, and so we develop new techniques (AI) which are really no
different from the old techniques, except that they are faster, more
parallelizable, and more efficient. In no sense do AI technologies
"think", "reason", or "understand" - not even by metaphor or analogy. At
best, they automate a small piece of work (perception, classifying, etc.)
that had, until now, been the work of a human being. This places this
process squarely within what Marx calls the
[subsumption](https://journal.radicallibrarianship.org/index.php/journal/article/view/25) of labour under
capital.

So why call them AI? Why create a
panic around something that is basically simply the next phase of the
automation of human labour by capital? To understand that, we can return
to Marx's chapter on technology:

>Machinery does not just act as a superior competitor to the worker,
>always on the point of making him superfluous. It is a power inimical
>to him, and capital proclaims this fact loudly and deliberately, as
>well as making use of it. It is the more powerful weapon for
>suppressing strikes, those periodic revolts of the working class
>against the autocracy of capital. (562)

Capital does not just replace human labour with the dead labour of
machines, it "proclaims this fact loudly and deliberately". There is a
*discursive* requirement to make sure workers think their jobs are at
risk due to technological advance (whether that be robotics or AI), in
order to keep them scared, docile, and subservient. The same discursive
requirement applies to race, as well, with anti-immigrant feeling
spurred up in part by fears of "immigrants coming to take your jobs".
However, in the case of technology - as opposed to immigration - just
because capital whips up such fear for its own purposes does not make it
false. It is true that technological advance will necessitate job loss,
more precarity, proletarianization and immiseration. In the case of
immigrants, it suits the capitalist's purposes to lie; in the case of
technology, it suits their purpose to tell the truth - but the purpose
remains the same.

*Reference*

Boden, Margaret. *Artificial Intelligence and Natural Man* (New York:
Basic Books, 1977).

Dyer-Witheford, Nick, Atle Mikkola Kjøsen and James Steinhoff. *Inhuman
Power: Artificial Intelligence and the Future of Capitalism* (London:
Pluto Press, 2019).

Marx, Karl. *Capital, Volume 1* (London: Penguin Books, 1976).

Wiener, Norbert. *The Human Use of Human Beings: Cybernetics and
Society* (Boston: Da Capo, [1950] 1954).
