title:	New Visi Development Direction
author:	David Pollak
date:	2012-12-04
tags:	[x-dpp]

## New Visi Development Direction ##

A lot of things "came together" on Sunday. I judged at AngelHack, I met with the founder
and the technology guy from a promising startup (not an AngelHack participant), and
I had breakfast with [Alexis Richardson](https://twitter.com/monadic) in which we started
chatting about Visi.

Alexis is an excellent combination of technical and business and he kept asking me hard
questions about Visi, where Visi models could execute, development environments, etc.

After the meeting, I had an hour-long, [very rainy](http://abclocal.go.com/kgo/story?section=weather&id=8905194)
drive from San Francisco to San Jose.

During the drive, I thought. I thought about the Visi vision, which is spelled out quite well in the
video presentation from [Emerging Languages Camp](http://blog.visi.la/posts/emerging_langs_preso).
I thought about my development failures (the type checker is broken) and my development challenges
(the type system that deals with types related to unit [inches, dollars, etc] and more broadly
a type algebra). I thought about execution and how Visi models would necessarily need to be compiled
to JavaScript so they could execute on the server, in the browser, and be dynamically reloaded into
iOS devices.

One of the greatest challenges and greatest joys in Visi development was doing Visi in Haskell.

Haskell is a huge win because it compiles to native iOS (ARM) code as well as native x86 code.
I was planning to use the excellent Haskell runtime to deal with threading issues because Haskell's
threading model is a lot closer to Erlang's threading model: you can create millions of threads in Haskell-land
because the threads are not tied to the underlying OS (a major problem on the JVM and one that
the likes of Scala doesn't solve.) Also, because Haskell is a lazy language and has built-in compile
time support for tail-calls, you wind up with a lot less stack depth than you do in a language like Scala.

Unfortunately, Haskell also presents a lot of challenges. Cabal is not nearly as powerful/flexible as
Maven or sbt. Doing cross-compilations is Haskell isn't really easy, despite the excellent
work by Stephen Blackheath in the [GHC iPhone](http://projects.haskell.org/ghc-iphone/) project.

The bridge between Haskell and C/Objective-C is painful.

Debugging Haskell is darned hard. I have yet to wrap my brain around the lazy evaluation model and
I spend a **lot** of time spinning my wheels because I am dealing with more moving parts than
my brain can deal with.

## Back to Scala ##

I am moving Visi development to Scala.  What this means:

* I'm porting the existing Visi code from Haskell to Scala (I miss Haskell's beautifully economical syntax already)
* I will create a Visi model compiler in Scala that will emit JavaScript and communicate via JSON
* I will be able to move more quickly on Visi language features because I will be in an environment I'm
  more familiar with

## Unanswered Questions ##

Here are some questions in my mind that do not yet have answers:

* Will Visi get rolled into Lift?
* Will Visi's server-side execution engine be Node.js?
* Will Visi development speed up?

Stick around to see how things progress over the next few months.

## BTW ##

By the way, I've changed the Visi domain to visi.la reflecting the "Visi Language" nature
of the project and avoiding folks calling the project "Visio".

I've merged the Visi.Pro piece of things into the visi.la domain for now, although if the project
does get back on track, there will be a commercial hosting component to it.

I've taken down the Visi.Pro and Visi web sites and they are replaced by this blog so
that they are less stale (and also so they are hosted on [Telegram](https:/telegr.am)).

