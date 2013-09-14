# Code Guidelines

## Format of Rules

Because there are very few complete absolutes when talking about coding standards, it is useful to document not only the rule itself, but how stringently we expect adherence to the rule to be. To this end, each rule will be stated as one of the following:

* **DO** - Do guidelines should always be followed (or have a really, really good reason why it needs to be broken in this specific case)
* **CONSIDER** - Consider guidelines should generally be followed, but if you fully understand the reasoning behind a guideline and have a good reason to not follow it anyway, you should not feel bad about breaking the rules
* **AVOID** - Avoid guidelines indicate that something is generally not a good idea, but there are known cases where breaking the rule makes sense
* **DO NOT** - Do not guidelines are something you should almost never do

*Stolen from [Framework Design Guidelines](http://www.amazon.com/Framework-Design-Guidelines-Conventions-Libraries/dp/0321545613/)*

## Readability

> Always code as if the person who ends up maintaining your code is a violent psychopath who knows where you live.<br/>
> -- [Coding Horror blog](http://www.codinghorror.com/blog/2008/06/coding-for-violent-psychopaths.html)

Readability should be the #1 concern when writing code. Code is read far more often than it is written, so one should optimize for that fact.

* **DO** follow formatting and naming standards for the language

> Thou shalt make thy program's purpose and structure clear to thy fellow man by using the One True Brace Style, even if thou likest it not, for thy creativity is better used in solving problems than in creating beautiful new impediments to understanding.<br/>
> -- [8<sup>th</sup> C Commandment](http://www.lysator.liu.se/c/ten-commandments.html)

If there aren't clear standards for the language, pick a standard and stick with it. Any standard is better than no standard.

* **DO** keep lines to 100 characters or less
* **DO** keep functions short

Short functions are more readable functions. The more lines of code a function has, the harder it is to understand everything it is doing. Often, one will see code like this:

```java
public void foo() {
    // Frob the frobnicator
    FrobnicatorFactory frobnicatorFactory = new FrobnicatorFactory();
    Frobnicator frobnicator = frobnicatorFactory.createInstance();
    frobnicator.frob();

    // Reticulate splines
    SplinesFactory splinesFactory = new SplinesFactory();
    Splines splines = splinesFactory.createInstance();
    splines.reticulate();

    // ... snip ... many more chunks of code
}
```

If the code is complicated enough that we need comments to understand what each block of code is doing, extract those blocks of code into functions to make the whole thing much more readable:

```java
public void foo() {
    frobFrobnicator();
    reticulateSplines();
}
```

The maximum recommended length of functions will vary by language, but in almost any language fifty lines is too long and twenty lines or less is pretty good.

## Exceptions

* **DO** catch exceptions which you can handle or recover from
* **CONSIDER** catching exceptions to log them or repackage them as more specific exceptions, but always re-throw
* **AVOID** simply swallowing exceptions

It is rarely the right thing to do, but there are circumstances where it can be. For example, in some languages parsing data can throw an exception when the data isn't recognized. In this limited case, catching the exception and moving on can be acceptable.

* **DO NOT** catch `Exception` (or whatever the generic exception type is in the language in which you are writing code)

Because you should only catch exceptions that you can handle or recover from (unless you're rethrowing them), you should never catch the base exception class. Additionally, by letting exceptions crash the application while you're developing it, you can find out what is causing problems and *fix the problems*. (See Martin Fowler's article [Fail Fast](http://martinfowler.com/ieeeSoftware/failFast.pdf).)
