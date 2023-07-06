# Advice-for-programmers
A few random principles I've found to be important and useful in my career programming games and apps.

* More code = more problems.
As an engineer you might think your job is to write code. But a very important task you have is to always fight against writing more software and more code.
Every feature you add and every change you make almost certainly introduces bugs and regressions.
The more features a program has the slower and more difficult it is to work on (to fix bugs and make necessary changes later)
Also more features can muddy the design and the apps purpose for users.
You should question whoever is suggesting making more software and more code and have them prove their point with data, prove that it's worthwhile.
Ideally you would be removing features, deleting software and code. Question the existing features existence and always be asking should we delete this?

* If you've been convinced to write some code, when sitting down to actually do so...
You should ideally be starting a new file, (or a new class)
If you must work in an existing file then you should at least be starting a new function.
Very rarely should you be adding more code to an existing function. Perhaps just one line calling your new function would be ok, anything else is dubious.

* Coding fundamentals - If you can religiously follow these then u are 50% of the way to having good code already.
Keep classes tiny, each class should only do one thing.
Keep functions tiny.
Many small things almost always better then one big thing (classes, scenes, prefabs, whatever.)
keep lifetime of everything to minimum (classes, scenes, prefabs, whatever.)

Minimise coupling
Everyone always says this but I think they dont define coupling too well. Obviously different parts of your code will need to talk to each other at some point and that's ok.
Classes should have well defined public endpoint functions and everything else should be private.
If you can delete everything inside a class and replace it with something entirely different, without any of your other code breaking, then thats fine and you have avoided bad coupling.

Some things that are probably bad coupling.
If class A is calling class B and class B is also calling class A.
If class A is micromanaging class B, like setting a bool on it.
If class A is calling many functions on class B.

* Optimise for *you*
Always write code that is optimized to be easy for you the developer to write. The simplest most basic thing 
Dont worry about performance
	Theres only one case in which you do... Your benchmarks are not up to the required standard. In that case run profiler, find lowest hanging fruit
Dont worry about security (only if ure being pwned)
Do worry about maintainability
