title:	Scala Port Status
author:	David Pollak
date:	2012-12-27
tags:	[x-dpp]

## Quick Update on the Visi Scala Port ##

The basic Visi parser is ported from Haskell to Scala.

I used the [Parboiled](https://github.com/sirthias/parboiled/wiki) parser
because it has much better performance and location capturing capabilities than
does Scala's built in parser combinators.

The basic type checker is working and most of the test cases from Haskell are
passing. I haven't ported all the tests, but the ones I have ported are working.

In addition to having a running typer, Visi also calculates the dependency graph
for each node in the typed lambda calculus. This will come in handy.

I took a brief detour through Clojure and, while I'd love the opportunity to write in
Clojure, my brain works best in Scala because I know [most of the
potholes and craters](http://blog.goodstuff.im/oy_scalac) in Scala.

## What's next? ##

Rather than implementing the Visi runtime in Scala (like I did in Haskell),
I'm going to compile Visi code to JavaScript so that it can be executed on
any platform that can run JavaScript (the browser, the JVM, iOS, Node, etc.)

So, over the next few days, I'll be writing a compiler that will compile the typed
lambda calculus to JavaScript and emit the sources and sinks as JSON objects.
But the cool thing is that you'll also get a JavaScript function to call when each of
the sources gets triggers such that the function will return a list of updated values for
all of the recomputed sinks.


