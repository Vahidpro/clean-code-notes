# Clean Code Notes
## Introduction

This repository contains my personal notes and key takeaways from Robert C. Martin's book Clean Code. It's a collection of insights and best practices to help me write clean, maintainable, and readable code.

# Foreword

> Honesty in small things is not a small thing.

 Attentiveness to detail is an even more critical foundation of professionalism than is any grand vision.
 
 A piece of code should be where you expect to find it—and, if not, you should re-factor to get it there.

**Making your code readable is as important as making it executable.**

> Don’t put off until tomorrow what you can do today.
>
> An ounce of prevention is worth a pound of cure.


 You should name a variable using the same care with which you name a firstborn child.

 **Design as a process, not a static endpoint.**

 # Introduction
  Of course you have been impeded by bad code. So then why did you write it?
 
  We’ve all said we’d go back and clean it up later. Of course, in those days we didn’t know LeBlanc’s law: Later equals never.

  **No duplication, one thing, expressiveness, tiny abstractions. Everything is there.**
  
  It is not the language that makes programs appear simple. It is the programmer that make the language appear simple!

  We are authors. And one thing about authors is that they have readers. Indeed, authors are responsible for communicating well with their readers. The next time you write a line of code, remember you are an author writing for readers who will judge your effort.

  **Leave the campground cleaner than you found it.**

The cleanup doesn’t have to be something big. Change one variable name for the better, break up one function that’s a little too large, eliminate one small bit of duplication, clean up one composite if statement

## Chatper 2: Meaningful Names

Names are everywhere in software. We name our variables, our functions, our arguments, classes, and packages. We name our source files and the directories that contain them. We name our jar files and war files and ear files. We name and name and name. Because we do so much of it, we’d better do it well.

## Use Intention-Revealing Names
**Choosing good names takes time but saves more than it takes. So take care with your names and change them when you find better ones.**

The name of a variable, function, or class, should answer all the big questions. 
It should tell you 
+ why it exists,
+ what it does,
+ and how it is used.

If a name requires a comment, then the name does not reveal its intent.

## Avoid Disinformation

Noise words are another meaningless distinction. Imagine that you have a `Product` class. If you have another called `ProductInfo` or `ProductData`, you have made the names different without making them mean anything different. Info and Data are indistinct noise words like `a`, `an`, and `the`.

## Use Pronounceable Names
## Use Searchable Name
My personal preference is that single-letter names can ONLY be used as local variables inside short methods. _The length of a name should correspond to the size of its scope_

## Class Names
Classes and objects should have noun or noun phrase names like `Customer`, `WikiPage`, `Account`, and `AddressParser`. Avoid words like `Manager`, `Processor`, `Data`, or Info in the name of a class. A class name should not be a verb.

**Say what you mean. Mean what you say.**
The function names have to stand alone, and they have to be consistent in order for you to pick the correct method without any additional exploration. Likewise, it’s confusing to have a `controller` and a `manager` and a `driver` in the same code base.

## Don't Pun
Avoid using the same word for two purposes. Using the same term for two different ideas is essentially a pun.

## Add Meaningful Context
Imagine that you have variables named `firstName`, `lastName`, `street`, `houseNumber`, `city`, `state`, and `zipcode`. Taken together it’s pretty clear that they form an address. But what if you just saw the `state` variable being used alone in a method? Would you automatically infer that it was part of an address? You can add context by using prefixes: `addrFirstName`, `addrLastName`, `addrState`, and so on. At least readers will understand that these variables are part of a larger structure.

# Chapter 3: Functions
## Small!
The first rule of functions is that they should be small.
The second rule of functions is _that they should be smaller than that_.
Functions should not be 100 lines long.Functions should hardly ever be 20 lines long.

### Blocks and Indenting
This implies that the blocks within `if` statements, `else` statements, `while` statements, and so on should be one line long. Probably that line should be a function call. Not only does this keep the enclosing function small, but it also adds documentary value because the function called within the block can have a nicely descriptive name.

This also implies that functions should not be large enough to hold nested structures. Therefore, the indent level of a function should not be greater than one or two. This, of course, makes the functions easier to read and understand.

## Do One Thing

**FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL. THEY SHOULD DO IT ONLY.**
The problem with this statement is that it is hard to know what “**one thing**” is.

another way to know that a function is doing more than “one thing” is if you can extract another function from it with a name that is not merely a restatement of its implementation.

## One Level of Abstraction per Function
In order to make sure our functions are doing “one thing,” we need to make sure that the statements within our function are all at the same level of abstraction.

## Reading Code from Top to Bottom: _The Stepdown Rule_
We want the code to read like a top-down narrative.5 We want every function to be followed by those at the next level of abstraction so that we can read the program, descending one level of abstraction at a time as we read down the list of functions.

## Use Descriptive Names
> “You know you are working on clean code when each routine turns out to be pretty much what you expected.”

The smaller and more focused a function is, the easier it is to choose a descriptive name
Don’t be afraid to make a name long. A long descriptive name is better than a short enigmatic name. A long descriptive name is better than a long descriptive comment.

## Function Arguments
The ideal number of arguments for a function is zero (niladic). Next comes one (monadic), followed closely by two (dyadic). Three arguments (triadic) should be avoided where possible. More than three (polyadic) requires very special justification—and then shouldn’t be used anyway.

## Flag Arguments
Flag arguments are ugly. Passing a boolean into a function is a truly terrible practice. It immediately complicates the signature of the method, loudly proclaiming that this function does more than one thing. It does one thing if the flag is true and another if the flag is false!

## Dyadic Function
**The parts we ignore are where the bugs will hide.**

There are times, of course, where two arguments are appropriate. For example,
`Point p = new Point(0,0);` is perfectly reasonable. Cartesian points naturally take two arguments. Indeed, we’d be very surprised to see `new Point(0)`. However, the two arguments in this case are ordered components of a single value! Whereas `output-Stream` and `name` have neither a natural cohesion, nor a natural ordering.

Dyads aren’t evil, and you will certainly have to write them. However, you should be aware that they come at a cost and should take advantage of what mechanims may be available to you to convert them into monads.

## Argument Objects
When a function seems to need more than two or three arguments, it is likely that some of those arguments ought to be wrapped into a class of their own. Consider, for example, the
difference between the two following declarations:

`Circle makeCircle(double x, double y, double radius);`
`Circle makeCircle(Point center, double radius);`

Reducing the number of arguments by creating objects out of them may seem like cheating, but it’s not. When groups of variables are passed together, the way `x` and `y` are in the example above, they are likely part of a concept that deserves a name of its own.

## Argument Lists
Functions that take variable arguments can be monads, dyads, or even triads. But it would be a mistake to give them more arguments than that.

`void monad(Integer... args);`

`void dyad(String name, Integer... args);`

`void triad(String name, int count, Integer... args);`

### Have No Side Effects
Side effects are lies. Your function promises to do one thing, but it also does other hidden things. Sometimes it will make unexpected changes to the variables of its own class. Sometimes it will make them to the parameters passed into the function or to system globals. In either case they are devious and damaging mistruths that often result in strange temporal couplings and order dependencies.

## Output Arguments
Arguments are most naturally interpreted as inputs to a function. If you have been programming for more than a few years, I’m sure you’ve done a double-take on an argument
that was actually an output rather than an input. For example: `appendFooter(s);`

Does this function append `s` as the footer to something? Or does it append some footer to `s`? Is `s` an input or an output?

## Command Query Separation
Functions should either do something or answer something, but not both.
Either your
function should change the state of an object, or it should return some information about that object. Doing both often leads to confusion.
This leads to odd statements like this:

`if (set("username", "unclebob"))...`

Imagine this from the point of view of the reader. What does it mean? Is it asking whether the `“username”` attribute was previously set to `“unclebob”?` Or is it asking whether the
`“username”` attribute was successfully set to `“unclebob”`? It’s hard to infer the meaning from the call because it’s not clear whether the word `“set”` is a verb or an adjective.

could try to resolve this by renaming the set function to `setAndCheckIfExists`, but that doesn’t much help the readability of the if statement. The real solution is to separate the
command from the query so that the ambiguity cannot occur.  
`if (attributeExists("username")) {`   
`setAttribute("username", "unclebob"); `  
`...  `  
`}`  

## Prefer Exceptions to Returning Error Codes

## Error Handling Is One Thing

Functions should do one thing. Error handing is one thing. Thus, a function that handles errors should do nothing else. This implies that if the keyword try exists in a function, it should be the very first word in the function and that there should be nothing after the catch/finally blocks.  

## Don't Repeat Yourself
**Duplication may be the root of all evil in software.**

## Conclusion
Every system is built from a domain-specific language designed by the programmers to describe that system.  
Functions are the verbs of that language, and classes are the nouns.  
Master programmers think of systems as stories to be told rather than programs to be written. They use the facilities of their chosen programming language to construct a much richer and more expressive language that can be used to tell that story.  
Never forget that your real goal is to tell the story of the system, and that the functions you write need to fit cleanly together into a clear and precise language to help you with
that telling.

# Chapter 4: Comments
> _“Don’t comment bad code—rewrite it.”_  
> —Brian W. Kernighan and P. J. Plaugher1

Comments are not like Schindler’s List. They are not “pure good.” Indeed, comments are, at best, a necessary evil.  
The proper use of comments is to compensate for our failure to express ourself in code. Note that I used the word failure. I meant it. Comments are always failures.  
Every time you write a comment, you should grimace and feel the failure of your ability of expression.  
Truth can only be found in one place: the code. Only the code can truly tell you what it does. It is the only source of truly accurate information. Therefore, though comments are sometimes necessary, we will expend significant energy to minimize them.  

## Comments Do Not Make Up for Bad Code
Rather than spend your time writing the comments that explain the mess you’ve made, spend it cleaning that mess.

## Explain Yourself in Code
Which would you rather see? This:  

```JavaScript
// Check to see if the employee is eligible for full benefits  
if ((employee.flags & HOURLY_FLAG) &&
(employee.age > 65))
```

Or this?  

```Java
if (employee.isEligibleForFullBenefits())
```  

It takes only a few seconds of thought to explain most of your intent in code. In many cases it’s simply a matter of creating a function that says the same thing as the comment
you want to write.

## Good Comments
### Legal Comments
Sometimes our corporate coding standards force us to write certain comments for legal reasons. For example, copyright and authorship statements are necessary and reasonable things to put into a comment at the start of each source file.
```js
// Copyright (C) 2003,2004,2005 by Object Mentor, Inc. All rights reserved.
// Released under the terms of the GNU General Public License version 2 or later.
```

### Informative Comments
It is sometimes useful to provide basic information with a comment. For example, consider this comment that explains the return value of an abstract method:  
```java
// Returns an instance of the Responder being tested.
protected abstract Responder responderInstance();
```

### Explanation of Intent
Sometimes a comment goes beyond just useful information about the implementation and provides the intent behind a decision.  

## Clarification  
Sometimes it is just helpful to translate the meaning of some obscure argument or return value into something that’s readable.
```java
assertTrue(a.compareTo(a) == 0); // a == a
assertTrue(a.compareTo(b) != 0); // a != b
assertTrue(ab.compareTo(ab) == 0); // ab == ab
```

## TODO Comments

It is sometimes reasonable to leave “To do” notes in the form of comments. In the //TODO following case, the `TODO` comment explains why the function has a degenerate implementation
and what that function’s future should be.
```java
**//TODO-MdM these are not needed
// We expect this to go away when we do the checkout model**
protected VersionInfo makeVersion() throws Exception
{
return null;
}
```

## Amplification

A comment may be used to amplify the importance of something that may otherwise seem inconsequential.

```javascript
String listItemContent = match.group(3).trim();
// the trim is real important.
It removes the starting
// spaces that could cause the item to be recognized
// as another list.
new ListItemWidget(this, listItemContent, this.level + 1);
return buildList(text.substring(match.end()));
```

## Bad Comments

### Mumbling

Plopping in a comment just because you feel you should or because the process requires it, is a hack. If you decide to write a comment, then spend the time necessary to make sure it is the best comment you can write.  
Any comment that forces you to look in another module for the meaning of that comment has failed to communicate to you and is not worth the bits it consumes.

### Redundant Comments
The comment probably takes longer to read than the code itself.
