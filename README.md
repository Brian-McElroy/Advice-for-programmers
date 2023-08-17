# Advice-for-programmers.
A few principles I've found to be important and useful in my career making games and apps and using Unity.  

## Communication skill is more important than coding skill.
I would much rather have a terrible coder / great communicator on my team rather than the inverse.  
Sitting down to write some code without talking to someone first is a bad sign and should be avoided.  
Overcommunication is always better than undercommunication. Overcommunication could be annoying or seen as patronising but the alternative is far worse. eg. a top dev spending a week writing excellent code for the *wrong feature*!  
Ask questions. Keep asking questions until it is 100% clear in your own mind...  
Exactly what you are doing.  
Why you are doing it.  
How you plan to do it.  

## Take your time.
It's much better to underpromise and overdeliver than the inverse.  
Schedule plenty of time for your work. eg. make a resonable estimate, then double it.  
Everything almost always takes longer than you think it will.  
Being hasty and writing unmaintainable code will lose you time overall, and more importantly it will make the project unpleasant to work on for the future.  

## More code = more problems.
As an engineer you might think your job is to write code. But a very important task you have is to always fight against writing more software and more code.  
Every feature you add and every change you make almost certainly introduces bugs and regressions.  
The more features a program has the slower and more difficult it is to work on (to fix bugs and make necessary changes later)  
Also more features can muddy the design and the apps purpose for users.  
You should question whoever is suggesting making more software and more code and have them prove their point with data, prove that it's worthwhile.  
Ideally you would be removing features, deleting software and code. Question the existing features and always be asking should we delete this?  

## Actual Coding advice.

### If you've been convinced to write some code, when sitting down to actually do so...
You should ideally be starting a new file, (or a new class)  
If you must work in an existing file then you should at least be starting a new function.  
Very rarely should you be adding more code to an existing function. Perhaps just one line calling your new function would be ok, anything else is dubious.  

### The fundamentals.
If you can religiously follow these fundamentals then u are half way to having good code already.  

Keep classes tiny, (eg. 100 lines max) each class *really* should only do *one thing*.  
Keep functions tiny (eg. 10 lines).  
Many small things are almost always better then one big thing (classes, scenes, prefabs, whatever.)  
Keep the lifetime of everything to a minimum (objects, scenes, prefabs, whatever.) It's always better to spawn and destroy stuff than keep it around.  

### But how can small classes do complicated tasks?
Think of your program like a corporation and the classes as people with different jobs. Like in a corporation there are workers and managers.  
Worker classes do hard work (like complicated math or procedural generation), but they dont make any decisions.  
Manager classes dont do any hard work at all, but instead just make decisions and give orders to other classes.    

You should end up with a hierarchy of many classes like a tree structure, with workers on the bottom, followed by a layer of manager classes managing those workers, followed by more layers of manager classes managing the managers beneath them.  

You can also think of your classes like Lego bricks, each one is small and simple but can be combined to make something complicated.  
If your classes are loosely coupled they really will be reusable like Lego bricks and you could rearrange them to make a different app.  

At the beginning of a project you can just start writing worker classes you know you will need without thinking too much or worrying about design patterns. You can build your program from the bottom-up rather than top-down.  

### Minimise coupling.  
Different parts of your code will need to talk to each other at some point and that's ok.  
Classes should have well defined public endpoint functions and everything else should be private.  
If you can delete everything inside a class and replace it with something entirely different, without any of your other code breaking, then thats fine and you have avoided coupling.   
 
Some things that are probably signs of coupling...  
If class A is calling class B and class B is also calling class A.  
If class A is micromanaging class B, like setting a bool on it.  
If class A is calling many different functions on class B.  

### Fancy features.
Avoid fancy features of the langauge if you can.  
If you can do everything with the basics (the things you learned in week 1 of college) thats great! Having to use fancier features of a language (eg. ternary operators, linq, whatever) is not a good sign.  
Other programmers (including future you) mightn't know those fancy features very well. Also if you are resorting to using fancy features it shows your head is in the wrong place, you should be striving to make your code as simple as possible, not fancy.

### Static functions ftw
The absolute best class is static with no fields and just static simple functions that take some input and return some output. As much of your code as possible should be like that.

### Testability
Code that is easy to write unit tests for is probably good. It is a red flag if code is difficult to write unit tests for.

### Naming
Names of files / classes / functions are important. It's worth spending a little extra time coming up with a good name. Long and descriptive is definitely better than short and ambiguous. Eg. I have a class called ChatGPTresponseNiceFormatter with these functions..    
public static string MakeNiceForTextToSpeech(string rawGPTresponse)  
public static string MakeNiceForPrinting(string rawGPTresponse)  
Also, if you are adding code that is not within the scope of the original class or functions name, you should probably start a new class or function and put the code there instead.

### Elegance
So coders usually say code is "elegant" meaning it is very terse and/or clever and accomplishes a lot in few lines of code. This is not very good imo. I would much rather have 4 lines of very simple basic code that a child could understand, rather than a clever elegant one-liner. Just like with fancy features, future programmers (including you) may not understand that clever code and so it is less maintainable then the simple basic code.

### Design patterns.
The best design pattern is none.  
It's good to know and have experience with various design patterns, but you should avoid using one in your own programs until the last possible moment, only when it's an emergency.  The thing about design patterns is that once you've committed to a certain pattern. you cant go back, all future work now needs to fit into the pattern, and you dont know what features or changes you might want in the future. Maybe they will be an awkward fit for the pattern? So by using a design pattern in a way you have made your code less maintainable.
a design pattern can help you implement a very difficult feature, overcome a big challenge but ideally you wont ever need to use one.

### Why spaghetti is bad.
The reason we call a certain type of bad code "spaghetti code" is not because it is disorganised and has no pattern like spaghetti, it's because it's all tangled and stuck together like spaghetti. You cant pull on a single strand of spaghetti without a huge clump of it following.  
Obviousuly it's nice to have code organized and neat, but disorganized code is not the end of the world, what *should* certainly be avoided is "spaghetti code" which is code that is highly highly coupled with many instances of bad coupling, where you cant change one class without having to change another, and so on.  

## Optimise for *you*.
The first code you write for any feature should be the utter simplest thing you can think of. The absolute easiest thing you personally as the dev could do that might give the client what they want. Ideally short and also *simple* and basic.  
If this code works and it's fit for purpose then, happy days! you are done. Move on to next task. Only if your program is now failing some predetermined benchmark of performance / quality / security / whatever, should you consider optimizing your code.  
That process might look like this...
1. Write simplest code.
2. Run benchmarks.
3. If benchmark passes, you're done! If benchmark fails and program is not fit for purpose, goto 4
4. Run profiler, find the lowest hanging fruit to optimize
5. optimise lowest hanging fruit, then goto 2

## *Do* worry about maintainability.
Pretty much the only thing I worry about in a project is maintainability. Performance / security / whatever problems very rarely arise in my experience, and if they do they can be troubleshooted and fixed.  
Lack of maintainability however, is a looming existential problem in *every project*.  
By maintainability I mean: How easy is it to make changes without breaking stuff and creating bugs.  
To me, it feels like every sofware project has a half-life and it's only a matter of time until it decays into unmaintainable goop, where 1 hour of bugfixing work creates 2 more hours worth of bugs, and progress is almost impossible. A project in that state is really horrible to work on and really saps your motivation.  
A lot of the tips above are geared towards helping you keep your project more maintainable for as long as possible. Ideally your project can avoid becoming goop for its entire lifetime and be a pleasure to work on every day.  
Another benefit of a maintainable project is that progress is linear and more predictable, whereas in an unmaintainable one, progress is really fast at the beginning and then slows down geometrically over time. It's worth moving slowly at the beginning of a project to ensure you are setting things up in a maintainable way. 


