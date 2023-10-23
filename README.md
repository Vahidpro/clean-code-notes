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
