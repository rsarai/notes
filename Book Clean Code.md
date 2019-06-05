# Clean Code

## Introduction
There are two parts to learning craftsmanship: knowledge and work. You must gain the knowledge of principles, patterns, practices, and heuristics that a craftsman knows, and you must also grind that knowledge into your fingers, eyes, and gut by working hard and practicing.

## Chapter 1 - Clean Code

### There Will Be Code
One might argue that a book about code is somehow behind the times—that code is no longer the issue; that we should be concerned about models and requirements instead. Indeed some have suggested that we are close to the end of code. That soon all code will be generated instead of written. That programmers simply won’t be needed because business people will generate programs from specifications.

**Nonsense!** We will never be rid of code, because code represents the details of the requirements. At some level those details cannot be ignored or abstracted; they have to be specified. And specifying requirements in such detail that a machine can execute them is programming. Such a specification is code.

### Bad code
Good code matters. That premise is one of the most
robust, supported, and overloaded of all the pre-
mises in our craft and we know good code matters because we’ve had to deal for so long with its lack. Have you ever been significantly impeded by bad code? If you are a programmer of any experience then you’ve felt this impediment many times.

### What Is Clean Code?

Bjarne Stroustrup, inventor of C++ and author of The C++ Programming Language:

> I like my code to be elegant and efficient. The logic should be straightforward to make it hard for bugs to hide, the dependencies minimal to ease maintenance, error handling complete according to an articulated strategy, and performance close to optimal so as not to tempt people to make the code messy with unprincipled optimizations. Clean code does one thing well.


> "Not to tempt people to make the code messy"
Bad code tempts the mess to grow! When others change bad code, they tend to make it worse. Pragmatic Dave Thomas and Andy Hunt said this a different way. They used the metaphor of broken windows:

> A building with broken windows looks like nobody cares about it. So other people stop caring. They allow more windows to become broken. Eventually they actively break them. They despoil the facade with graffiti and allow garbage to collect. One broken window starts the process toward decay.

Grady Booch, author of Object Oriented Analysis and Design with Applications:

> Clean code is simple and direct. Clean code reads like well-written prose. Clean code never obscures the designer’s intent but rather is full of crisp abstractions and straightforward lines of control.

“Big” Dave Thomas, founder of OTI, godfather of the Eclipse strategy:

> Clean code can be read, and enhanced by a developer other than its original author. It has unit and acceptance tests. It has meaningful names. It provides one way rather than many ways for doing one thing. It has minimal dependencies, which are explicitly defined, and provides a clear and minimal API. Code should be literate since depending on the language, not all necessary information can be expressed clearly in code alone.

Michael Feathers, author of Working Effectively with Legacy Code:

> I could list all of the qualities that I notice in clean code, but there is one overarching quality that leads to all of them. Clean code always looks like it was written by someone who cares. There is nothing obvious that you can do to make it better. All of those things were thought about by the code’s author, and if you try to imagine improvements, you’re led back to where you are, sitting in appreciation of thecode someone left for you—code left by someone who cares deeply about the craft.

Ron Jeffries, author of Extreme Programming Installed and Extreme Programming Adventures in C#

> In recent years I begin, and nearly end, with Beck’s rules of simple code. In priority order, simple code:
>    - Runs all the tests;
>    - Contains no duplication;
>    - Expresses all the design ideas that are in the system;
>    - Minimizes the number of entities such as classes, methods, functions, and the like.

> Of these, I focus mostly on duplication. When the same thing is done over and over, it’s a sign that there is an idea in our mind that is not well represented in the code. I try to figure out what it is. Then I try to express that idea more clearly.

> Expressiveness to me includes meaningful names, and I am likely to change the names of things several times before I settle in. With modern coding tools such as Eclipse, renaming is quite inexpensive, so it doesn’t trouble me to change. Expressiveness goes beyond names, however. I also look at whether an object or method is doing more than one thing. If it’s an object, it probably needs to be broken into two or more objects. If it’s a method, I will always use the Extract Method refactoring on it, resulting in one method that says more clearly what it does, and some submethods saying how it is done.

> Duplication and expressiveness take me a very long way into what I consider clean code, and improving dirty code with just these two things in mind can make a huge difference. There is, however, one other thing that I’m aware of doing, which is a bit harder to explain.

> After years of doing this work, it seems to me that all programs are made up of very similar elements. One example is “find things in a collection.” Whether we have a database of employee records, or a hash map of keys and values, or an array of items of some kind, we often find ourselves wanting a particular item from that collection. When I find that happening, I will often wrap the particular implementation in a more abstract method or class. That gives me a couple of interesting advantages. I can implement the functionality now with something simple, say a hash map, but since now all the references to that search are covered by my little abstraction, I can change the implementation any time I want. I can go forward quickly while preserving my ability to change later.

> In addition, the collection abstraction often calls my attention to what’s “really” going on, and keeps me from running down the path of implementing arbitrary collection behavior when all I really need is a few fairly simple ways of finding what I want.

> Reduced duplication, high expressiveness, and early building of simple abstractions. That’s what makes clean code for me.

Ward Cunningham, inventor of Wiki, inventor of Fit, coinventor of eXtreme Programming. Motive force behind
Design Patterns. Smalltalk and OO thought leader. The godfather of all those who care about code.

> You know you are working on clean code when each routine you read turns out to be pretty much what you expected. You can call it beautiful code when the code also makes it look like the language was made for the problem.


### The Boy Scout Rule
It’s not enough to write the code well. The code has to be kept clean over time.
> Leave the campground cleaner than you found it


## Chapter 2 - Meaningful Names

### Use Intention-Revealing Names
The name of a variable, function, or class, should answer all the big questions. It should tell you:

- **Why it exists**
- **What it does**
- **How it is used**

If a name requires a comment, then the name does not reveal its intent.

```python
# BAD
d = 1  # elapsed time in days

# GOOD
elapsed_time_in_days = 1
```

Choosing names that reveal intent can make it much easier to understand and change code. What is the purpose of this code?
```java
public List<int[]> getThem() {
    List<int[]> list1 = new ArrayList<int[]>();
    for (int[] x : theList)
        if (x[0] == 4)
            list1.add(x);
    return list1;
}
```
The problem isn’t the simplicity of the code but the implicity of the code (to coin a phrase): the degree to which the context is not explicit in the code itself. The code implicitly requires that we know the answers to questions such as:

1. What kinds of things are in theList ?
2. What is the significance of the zeroth subscript of an item in theList ?
3. What is the significance of the value 4 ?
4. How would I use the list being returned?

The answers to these questions are not present in the code sample, _but they could have been_.

Say that we’re working in a mine sweeper game. We find that the board is a list of cells called `theList`. Each cell on the board is represented by a simple array. We further find that the zeroth subscript is the location of a status value and that a status value of 4 means “flagged.”

- theList     -> gameBoard
- number 4    -> flagged

```java
public List<int[]> getFlaggedCells() {
    List<int[]> flaggedCells = new ArrayList<int[]>();
    for (int[] cell : gameBoard)
        if (cell[STATUS_VALUE] == FLAGGED)
            flaggedCells.add(cell);
    return flaggedCells;
}
```

The simplicity of the code has not changed. It still has exactly the same number of operators and constants, with exactly the same number of nesting levels. But the code has become much more explicit.

- list of cells (int[])     -> class Cell
- number 4                  -> isFlagged()

```java
public List<Cell> getFlaggedCells() {
    List<Cell> flaggedCells = new ArrayList<Cell>();
    for (Cell cell : gameBoard)
        if (cell.isFlagged())
            flaggedCells.add(cell);
    return flaggedCells;
}
```

### Avoid Disinformation
Programmers must avoid leaving false clues that obscure the meaning of code. Do not refer to a grouping of accounts as an accountList unless it’s actually a `List`. The word list means something specific to programmers.

Beware of using names which vary in small ways. How long does it take to spot the subtle difference between a `XYZControllerForEfficientHandlingOfStrings` in one module and, somewhere a little more distant, `XYZControllerForEfficientStorageOfStrings`? The words have frightfully similar shapes. **Spelling similar concepts similarly is information. Using inconsistent spellings is disinformation.**

### Make Meaningful Distinctions
Number-series naming (a1, a2, .. aN) is the opposite of intentional naming. Such names are not disinformative—they are noninformative; they provide no clue to the author’s intention. Consider:

```java
public static void copyChars(char a1[], char a2[]) {
    for (int i = 0; i < a1.length; i++) {
        a2[i] = a1[i];
    }
}
```
This function reads much better when source and destination are used for the argument names.

Noise words are another meaningless distinction. Imagine that you have a `Product` class. If you have another called `ProductInfo` or `ProductData` , you have made the names different without making them mean anything different. Info and Data are indistinct noise words like a, an, and the.

**Noise words are redundant**. The word variable should **never** appear in a variable name. The word table should never appear in a table name. How is NameString better than Name? Would a Name ever be a floating point number? If so, it breaks an earlier rule about disinformation. Imagine finding one class named Customer and another named CustomerObject. What should you understand as the distinction? Which one will represent the best path to a customer’s payment history?

```java
getActiveAccount();
getActiveAccounts();
getActiveAccountInfo();
```

How the programmers are supposed to know which of these function to call?

### Use Pronounceable Names
If you can’t pronounce it, you can’t discuss it without sounding like an idiot.This matters because programming is a social activity.

```java
class DtaRcrd102 {
    private Date genymdhms;
    private Date modymdhms;
    private final String pszqint = "102";
    /* ... */
};

class Customer {
    private Date generationTimestamp;
    private Date modificationTimestamp;;
    private final String recordId = "102";
    /* ... */
};
```

### Use Searchable Names
Single-letter names and numeric constants have a particular problem in that they are not easy to locate across a body of text. One might easily grep for `MAX_CLASSES_PER_STUDENT`, but the number 7 could be more troublesome.  If a variable or constant might be seen or used in multiple places in a body of code, it is imperative to give it a search-friendly name. Once again compare:

```java
for (int j=0; j<34; j++) {
    s += (t[j]*4)/5;
}

// to

int realDaysPerIdealDay = 4;
const int WORK_DAYS_PER_WEEK = 5;
int sum = 0;
for (int j=0; j < NUMBER_OF_TASKS; j++) {
    int realTaskDays = taskEstimate[j] * realDaysPerIdealDay;
    int realTaskWeeks = (realdays / WORK_DAYS_PER_WEEK);
    sum += realTaskWeeks;
}

```

### Avoid Encodings
We have enough encodings to deal with without adding more to our burden. Encoding type or scope information into names simply adds an extra burden of deciphering. It hardly seems reasonable to require each new employee to learn yet another encoding “language” in addition to learning the (usually considerable) body of code that they’ll be working in. It is an unnecessary mental burden when trying to solve a problem. Encoded names are seldom pronounceable and are easy to mis-type.

1. Avoid Hungarian Notation
2. Avoid Member Prefixes
3. Avoid Naming Interfaces and Implementations with the prefixes/sufixes: `I`, `Imp`, etc.
4. Avoid Mental Mapping

