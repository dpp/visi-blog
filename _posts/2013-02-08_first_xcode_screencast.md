title:	First Xcode Screencast
author: David Pollak
tags: [x-dpp]

## First Xcode Screencast ##

I've put together a screencast of integrating a Visi model into an iPad app using
Xcode: [http://tunaforcats.com/Visi_ipad_demo.mov](http://tunaforcats.com/Visi_ipad_demo.mov).

The workflow is as follows:

* Create an iPad app
* Copy the `visi.jar` compiler into the project
* Create your Visi model
* Compile the Visi model
* Subclass your controller from the generated Objective-C code
* Wire up your app
* Update your model
* Re-wire your app

In Visi, all inputs are done via "Sources" and all outputs are "Sinks".

Each time a source changes (signals) all the dependent sinks are recomputed and signaled.

In Xcode, sources are `IBAction`s and sinks are `IBOutlet`s. So, it's pretty easy to wire
the sources and sinks to the UI elements in Xcode.

## Accumulation ##

One of the interesting features of Visi is that if you have a recursive function that
is dependent on a source, the recursive function is recomputed each time the source
triggers. This allows you to accumulate data over multiple signals. The syntax is easy:

```

?n1 // a number source

sum = sum + n1

```

So, each time `n1` signals, the `sum` is updated.

## It's JavaScript on the backend ##

Visi models now compile to JavaScript and use JSON for communication.

So, the same model will execute the same way with the same signals on the iPad or on anything else that
runs standard JavaScript.

Signal by sending JSON in: `{"n1": 5, "n2": 10}` and get JSON out: `{"Sum": 15, "Prod": 50}`.

That way, you can run the same code and get the same results on mobile devices, in the browser, or in
the cloud.

## Enjoy ##

And Happy Weekend



