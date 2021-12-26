# Starting Out
## Ready, Set, go!

Alright, let's get started! If you're the sort of horrible person who doesn't read introductions to things and you skipped it, you might want to read the last section in the introduction anyway because it explains what you need to follow this tutorial and how we're going to load functions. The first thing we're going to do is run ghc's interactive mode and call some function to get a very basic feel for haskell. Open your terminal and type in ghci. You will be greeted with something like this.

```
GHCi, version 6.8.2: http://www.haskell.org/ghc/  :? for help  
Loading package base ... linking ... done.  
Prelude>
```

Congratulations, you're in GHCI! The prompt here is `Prelude>` but because it can get longer when you load stuff into the session, we're going to use ghci>. If you want to have the same prompt, just type in `:set prompt "ghci> "`.

Here's some simple arithmetic.



```
ghci> 2 + 15  
17  
ghci> 49 * 100  
4900  
ghci> 1892 - 1472  
420  
ghci> 5 / 2  
2.5  
ghci>  

```

This is pretty self-explanatory. We can also use several operators on one line and all the usual precedence rules are obeyed. We can use parentheses to make the precedence explicit or to change it.

```
ghci> (50 * 100) - 4999  
1  
ghci> 50 * 100 - 4999  
1  
ghci> 50 * (100 - 4999)  
-244950  

```

Pretty cool, huh? Yeah, I know it's not but bear with me. A little pitfall to watch out for here is negating numbers. If we want to have a negative number, it's always best to surround it with parentheses. Doing 5 * -3 will make GHCI yell at you but doing 5 * (-3) will work just fine.

Boolean algebra is also pretty straightforward. As you probably know, && means a boolean and, || means a boolean or. not negates a True or a False.

```
ghci> True && False  
False  
ghci> True && True  
True  
ghci> False || True  
True   
ghci> not False  
True  
ghci> not (True && True)  
False  
```

Testing for equality is done like so.

```
ghci> 5 == 5  
True  
ghci> 1 == 0  
False  
ghci> 5 /= 5  
False  
ghci> 5 /= 4  
True  
ghci> "hello" == "hello"  
True   
```

What about doing 5 + "llama" or 5 == True? Well, if we try the first snippet, we get a big scary error message!

```
No instance for (Num [Char])  
arising from a use of `+' at <interactive>:1:0-9  
Possible fix: add an instance declaration for (Num [Char])  
In the expression: 5 + "llama"  
In the definition of `it': it = 5 + "llama"   
```

Yikes! What GHCI is telling us here is that "llama" is not a number and so it doesn't know how to add it to 5. Even if it wasn't "llama" but "four" or "4", Haskell still wouldn't consider it to be a number. + expects its left and right side to be numbers. If we tried to do True == 5, GHCI would tell us that the types don't match. Whereas + works only on things that are considered numbers, == works on any two things that can be compared. But the catch is that they both have to be the same type of thing. You can't compare apples and oranges. We'll take a closer look at types a bit later. Note: you can do 5 + 4.0 because 5 is sneaky and can act like an integer or a floating-point number. 4.0 can't act like an integer, so 5 is the one that has to adapt.

You may not have known it but we've been using functions now all along. For instance, * is a function that takes two numbers and multiplies them. As you've seen, we call it by sandwiching it between them. This is what we call an infix function. Most functions that aren't used with numbers are prefix functions. Let's take a look at them.

Functions are usually prefix so from now on we won't explicitly state that a function is of the prefix form, we'll just assume it. In most imperative languages functions are called by writing the function name and then writing its parameters in parentheses, usually separated by commas. In Haskell, functions are called by writing the function name, a space and then the parameters, separated by spaces. For a start, we'll try calling one of the most boring functions in Haskell.

```
ghci> succ 8  
9   
```