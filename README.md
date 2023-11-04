# Clean Code Notes
### My notes and highlights of the Clean Code book.

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
