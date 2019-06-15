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
    This is a problem with single-letter variable names. Certainly a loop counter may be named i or j or k (though never l !) if its scope is very small and no other names can conflict with it. This is because those single-letter names for loop counters are traditional.

    However, in most other contexts a single-letter name is a poor choice; it’s just a place holder that the reader must mentally map to the actual concept.


### Class Names
Classes and objects should have noun or noun phrase liek: Customer, WikiPage, Account, AddressParser. Avoid words like: Manager, Processor, Data, Info in the name of a class.

### Method Names
Methods should have verb or verb phrase names like: postPayment, deletePage, save. Accessors, mutators and predicates should be named for their value and prefixed with get, set and is according to the standard.

```java
string name = employee.getName();
customer.setName("mike");
if (paycheck.isPosted())...
```

### Pick One Word per Concept
Pick one word for one abstract concept and stick with it. For instance, it’s confusing to have fetch, retrieve, and get as equivalent methods of different classes. Likewise, it’s confusing to have a controller and a manager and a driver in the same code base.

A consistent lexicon is a great boon to the programmers who must use your code.

### Don't Pun
Avoid using the same word for two purposes. Using the same term for two different ideas is essentially a pun.

Eg: If you follow the “one word per concept” rule, you could end up with many classes
that have, for example, an add method. As long as the parameter lists and return values of the various add methods are semantically equivalent, all is well. However one might decide to use the word add for “consistency” when he or she is not in fact adding in the same sense. Let’s say we have many classes where add will create a new value by adding or concatenating two existing values. Now let’s say we are writing a new class that has a method that puts its single parameter into a collection. Should we call this method add ? It might seem consistent because we have so many other add methods, but in this case, the semantics are different, so we should use a name like insert or append instead. To call the new method add would be a pun.

### Use Solution Domain Names
Remember that the people who read your code will be programmers. So go ahead and use computer science (CS) terms, algorithm names, pattern names, math terms, and so forth. It is not wise to draw every name from the problem domain because we don’t want our coworkers to have to run back and forth to the customer asking what every name means when they already know the concept by a different name.

### Use Problem Domain Names
When there is no “programmer-eese” for what you’re doing, use the name from the problem domain.

### Add Meaningful Context
Imagine that you have variables named firstName , lastName , street , houseNumber , city, state, and zipcode. Taken together it’s pretty clear that they form an address. But what if you just saw the state variable being used alone in a method? Would you automatically infer that it was part of an address? You can add context by using prefixes: addrFirstName , addrLastName , addrState , and so on. At least readers will understand that these variables are part of a larger structure. Of course, a better solution is to create a class named Address .

### Don't Add Gratuitous Context
In an imaginary application called “Gas Station Deluxe,” it is a bad idea to prefix every class with GSD. Shorter names are generally better than longer ones, so long as they are clear. Add no more context to a name than is necessary.

If I need to differentiate between MAC addresses, port addresses, and Web addresses, I might consider PostalAddress , MAC , and URI . The resulting names are more precise which is the point of all naming.

## Chapter 3 - Functions
How can we make a function communicate its intent? What attributes can we give our functions that will allow a casual reader to intuit the kind of program they live inside?

### Small
- The first rule of functions is that they should be small.
- The second rule of functions is that they should be smaller than that.

**Functions should hardly ever be 20 lines long.**

#### Blocks and Indenting
This implies that the blocks within if statements, else statements, while statements,and so on **should be one line long**. Probably that line should be a **function call**. Not only does this keep the enclosing function small, but it also adds documentary value because the function called within the block can have a nicely **descriptive name**.

This also implies that **functions should not be large enough to hold nested structures**. Therefore, the indent level of a function should not be greater than one or two. This, of course, makes the functions easier to read and understand.

### Do One Thing
> FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL. THEY SHOULD DO IT ONLY.

If a function does only those steps that are one level below the stated name of the function, then the function is doing one thing. After all, the reason we write functions is to decompose a larger concept (in other words, the name of the function) into a set of steps at the next level of abstraction.

Another way to know that a function is doing more than “one thing” is if you can extract another function from it with a name that is not merely a restatement of its implementation.

#### Sections within Functions
If a function is divided into sections such as declarations, initializations, and sieve. This is an obvious symptom of doing more than one thing. Functions that do one thing cannot be reasonably divided into sections.

### One  Level of Abstraction per Function
In order to make sure our functions are doing “one thing,” we need to make sure that the statements within our function are all **at the same level of abstraction**. Mixing levels of abstraction within a function is always confusing. Readers may not be able to tell whether a particular expression is an **essential concept** or a **detail**. Worse, like broken windows, once details are mixed with essential concepts, more and more details tend to accrete within the function.

#### Reading Code from Top to Bottom: _The Stepdown Rule_
The code should be read like a top-down narrative. Every function should be followed by those at the next level of abstraction so that we can read the program descending one level of abstraction at a time as we read down the list of functions.

To say this differently, we want to be able to read the program as though it were a set of _TO paragraphs_, each of which is describing the current level of abstraction and referencing subsequent _TO paragraphs_ at the next level down.

Eg:
- To include the setups and teardowns, we include setups, then we include the test page content, and then we include the teardowns.
    - To include the setups, we include the suite setup if this is a suite, then we include the regular setup.
        - To include the suite setup, we search the parent hierarchy for the “SuiteSetUp” page and add an include statement with the path of that page.
            -To search the parent...

### Switch Statements
Even a switch statement with only two cases is larger than I’d like a single block or function to be. It’s also hard to make a switch statement that does one thing. By their nature, switch statements always do N things. Unfortunately we can’t always avoid switch statements, but we can make sure that each switch statement is buried in a low-level class and is never repeated. We do this, of course, with polymorphism.

Consider:

```java
public Money calculatePay(Employee e) throws InvalidEmployeeType {
    switch (e.type) {
        case COMMISSIONED:
            return calculateCommissionedPay(e);
        case HOURLY:
            return calculateHourlyPay(e);
        case SALARIED:
            return calculateSalariedPay(e);
        default:
            throw new InvalidEmployeeType(e.type);
    }
}
```
There are several problems with this function:
- It's large, and when new employee types are added, it will grow;
- Does more than one thing;
- Violates the Single Responsability Principle (SRP) because there is more than one reason for it to change;
- Violates the Open Closed Principle 8 (OCP) because it must change whenever new types are added;
- Possibly the worst problem with this function is that there are an unlimited number of other functions that will have the same structure, like:

```java
isPayday(Employee e, Date date),
// or
deliverPay(Employee e, Money pay)
```

The solution to this problem is to bury the switch statement in the basement of an ABSTRACT FACTORY, and never let anyone see it. The factory will use the
switch statement to create appropriate instances of the derivatives of Employee , and the various functions, such as calculatePay , isPayday , and deliverPay , will be dispatched polymorphically through the Employee interface.

```java
public abstract class Employee {
    public abstract boolean isPayday();
    public abstract Money calculatePay();
    public abstract void deliverPay(Money pay);
}
-----------------
public interface EmployeeFactory {
    public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType;
}
-----------------
public class EmployeeFactoryImpl implements EmployeeFactory {
    public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType {
        switch (r.type) {
            case COMMISSIONED:
                return new CommissionedEmployee(r) ;
            case HOURLY:
                return new HourlyEmployee(r);
            case SALARIED:
                return new SalariedEmploye(r);
            default:
                throw new InvalidEmployeeType(r.type);
        }
    }
}
```

My general rule for switch statements is that they can be tolerated if they appear only once, are used to create polymorphic objects, and are hidden behind an inheritance relationship so that the rest of the system can’t see them.

### Use Descriptive Names
Remember Ward’s principle:
> You know you are working on clean code when each routine turns out to be pretty much what you expected.

The smaller and more focused a function is, the easier it is to choose a descriptive name. **Don’t be afraid to make a name long**. A long descriptive name is better than a short enigmatic name. A long descriptive name is better than a long descriptive comment.

### Function Arguments
The ideal number of arguments for a function is zero (niladic). Next comes one (monadic), followed closely by two (dyadic).

Three arguments (triadic) should be avoided where possible. More than three (polyadic) requires very special justification — and then shouldn’t be used anyway.

- Common Monadic Forms
There are two very common reasons to pass a single argument into a function. You may be **asking a question about that argument**, as in _boolean fileExists(“MyFile”)_. Or you may be **operating on that argument, transforming it into something else and returning it**. For example, _InputStream fileOpen(“MyFile”)_ transforms a file name String into an InputStream return value.

The overall program is meant to **interpret the function call as an event** and use the argument to **alter the state of the system**, for example, _void passwordAttemptFailedNtimes(int attempts)_. Use this form with care. It should be very clear to the reader that this is an event.

Try to avoid any monadic functions that don’t follow these forms. If a function is going to transform its input argument, the transformation should appear as the return value. Indeed, _StringBuffer transform(StringBuffer in)_ is better than _void transform-(StringBuffer out)_, even if the implementation in the first case simply returns the input argument. At least it still follows the form of a transformation.

- Flag Arguments
Flag arguments are ugly. Passing a boolean into a function is a truly terrible practice. Loudly proclaiming that this function
does more than one thing. It does one thing if the flag is true and another if the flag is false.

- Dyadic Functions
Dyads aren’t evil, and you will certainly have to write them. However, you should be aware that they come at a cost and should take advantage of what mechanims may be available to you to convert them into monads.

There are times, of course, where two arguments are appropriate. For example, Point p = new Point(0,0) is perfectly reasonable, the two arguments in this case are ordered components of a single value!

- Triads
Functions that take three arguments are significantly harder to understand than dyads.

- Argument Objects
When a function seems to need more than two or three arguments, it is likely that some of those arguments ought to be wrapped into a class of their own. Consider, for example, the difference between the two following declarations:
```
Circle makeCircle(double x, double y, double radius);
Circle makeCircle(Point center, double radius);
```

Reducing the number of arguments by creating objects out of them may seem like cheating, but it’s not. When groups of variables are passed together, the way x and y are in the example above, they are likely part of a concept that deserves a name of its own.

- Argument Lists

Sometimes we want to pass a variable number of arguments into a function. Consider, for example, the `String.format` method:
```java
String.format("%s worked %.2f hours.", name, hours);
```

If the variable arguments are all treated identically, as they are in the example above, then they are equivalent to a single argument of type `List`. By that reasoning, `String.format` isactually dyadic. Indeed, the declaration of `String.format` as shown below is clearly dyadic.

```java
public String format(String format, Object... args)
```

- Verbs and Keywords
Choosing good names for a function can go a long way toward **explaining the intent of the function** and the **order and intent of the arguments**.

### Have No Side Effects
Side effects are lies. Your function promises to do one thing, but it also does other hidden things.

Consider:

```java
public class UserValidator {
    private Cryptographer cryptographer;
    public boolean checkPassword(String userName, String password) {
        User user = UserGateway.findByName(userName);
        if (user != User.NULL) {
            String codedPhrase = user.getPhraseEncodedByPassword();
            String phrase = cryptographer.decrypt(codedPhrase, password);
            if ("Valid Password".equals(phrase)) {
                Session.initialize();
                return true;
            }
        }
        return false;
    }
}
```
This function uses a standard algorithm to match a userName to a password . It returns true if they match and false if anything goes wrong. But it also has a side effect: `Session.initialize();`

The name does not imply that it initializes the session. So a caller who believes what the name of the function says runs the risk of erasing the existing session data when he or she decides to check the validity of the user.

If you must have a temporal coupling, you should make it clear in the name of the function.

### Output Arguments
If you have been programming for more than a few years, I’m sure you’ve done a double-take on an argument that was actually an output rather than an input. For example:

`appendFooter(s);`

Does this function append s as the footer to something? Or does it append some footer to s ? Is s an input or an output? It doesn’t take long to look at the function signature and see:

```java
public void appendFooter(StringBuffer report)
```

This clarifies the issue, but only at the expense of checking the declaration of the function. Anything that forces you to check the function signature is equivalent to a double-take. It’s a cognitive break and should be avoided.


### Command Query Separation

