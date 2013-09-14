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

## Exceptions

* **DO NOT** simply swallow exceptions
* **DO NOT** catch `Exception` (or whatever the generic exception type is in the language in which you are writing code)

