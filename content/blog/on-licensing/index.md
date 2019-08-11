---
title: "On Licensing"
date: 2015-08-22T13:54:00-06:00
tags: [ "law", "copyright", "creative" ]
---
# What about it?

Copyright is broken. The whole concept of controlling copying of a resource is just not viable, and furthermore erronous. To me it is reminiscent of censorship, and we all know how well that works.

Lately I have been releasing any works to the public domain. Before discussing why, let's examine this "copyright" thing.
# What got me thinking about this

I don't recall what exactly was being looked for when I saw a project on github with an `UNLICENSE` file. Initially I payed no mind to this and I went on my way. Little did I know of the reagent I had encountered.

A few days later—presumably because I was about to release a chunk of code—I began to wonder why we could just copy certain works, yet most code had to be attributed—in the best case—or bought. I suddenly remembered the [link](http://unlicense.org) at the bottom of that `UNLICENSE`. I read a bit and although I don't agree with it completely, I began to question why copyright exists.
# Why copyright

I'm not going to rehash all of the history of copyright, just look at reasons people commonly cite for copyright.
## Credit/Attribution

This is—quite possibly—the most common excuse for copyright I've seen. Manifests in common Creative Commons licences for art and in BSD type licenses for code. I fail to see how this would not work, but it is incredibly heavy handed and inpractical.

Many circles already have a name for this called `plagiarism`. [Merriam-Webster](http://merriam-webster.com/dictionary/plagiarism) defines this as "the act of using another person's words or ideas without giving credit to that person". In academia this is a very a serious offense. Just ask any of the many students expelled for it. In other circles it is also considered common curtesy. In light of this, is applying law to the problem of plagiarism a proper aid?

And what happens when your works are plagiarized? If you did not place copyright on it, nothing (assuming plagiarism is fine). If you did, either you sue or you let the law be broken. Assuming you're not a sadist, I doubt you'll do the former. If a law is meant to be broken, then what's the point of said law?
## Control

This is not quite as common, but still a reason. I am guilty of this one too. The aim is to maintain control on a project, and this is pretty close to an actual reason.

Usually achieved partially via closed source in software and strict licensing in art. Not being an artist I can't say how it is managed; so I will seek code. Two related project I am slightly familiar with and have vastly different approaches to this would be [clojure](http://clojure.org) and [datomic](http://datomic.com).

Clojure is under the EPL 1.0 which actually allows forks. Many forks actually do exist, [#clojure](http://kiwiirc.com/client/irc.freenode.net/#clojure) on freenode, the [mailing lists](http://groups.google.com/group/clojure) and other sources do a decent job of reminding people of the downsides of using forks. So while you're welcome to run your own forks, the community at large tries hard to use the canonical implementation. The way this is implemented on the [JVM](http://openjdk.java.net/) makes it rather easy to swap the implementation of clojure at launch. This is very useful for testing new features before inclusion in the upstream code.

Datomic on the other hand is not open source and has a custom EULA. This establishes control firmly for Cognitect at the expense of customization for users. As datomic is enterprise software—and relatively small—this could be a fair trade-off. And considering datomic was made after clojure it is plausible that the EPL-shaded picture I painted previously isn't as well-made as I think.
## Monetary Endowement

I would have to claim pure greed for this, but that's my opinion and don't care much.
## Why *I* avoid it

I feel as I received for free what little skill I have and it is very fitting for me to give it freely. Not just me, but I feel everyone should do the same as they all received in the same manner. I do not pretend to have any such ability to force anyone, and furthermore I do not think it'd be right to. Therefore I hope that by doing this I can set yet another example for any other content creator out there.

I may not be very creative, or even well-endowed in programming, but darn it if I'm not going to share what I do create!

