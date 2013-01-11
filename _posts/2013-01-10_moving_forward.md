title:	Moving Forward
author:	David Pollak
date:	2013-01-10
tags:	[x-dpp]

## Moving Forward ##

The Scala port of Visi now has more features than the Haskell version.

The Scala version of Visi compiles to JavaScript and within JavaScript,
it supports lazy evaluations via Thunks.

The dependency graph works correctly such that Visi can determine
all the sinks (outputs) what change based on a source changing.

The JavaScript runtime correctly does minimal recomputation such
that only the sinks impacted by a set of sources changing will be recalculated.

Also, if there are any parameterless functions that depend on a source,
they will be reset before the sinks are recomputed.

Most importantly, recursive parameterless functions work correctly. For example:

```

?in // an input

sum = sum + in

always1 x = 1

cnt = cnt + always1 in

"Average" = sum / cnt

```

The above code will accumulate triggers of "in" and for each trigger, recompute the average.

## It compiles to JavaScript ##

Also, Visi compiles to JavaScript so all of the above stuff is
all running in JavaScript. It's not fancy pants Scala code or Actors or
anything, it's just JavaScript that can be executed in Rhino, your browser,
or shoveled into the iOS or Android JavaScript engine.

