# mersus-coding-guidelines

> Author : Suriya Palaniswami <br>
> Email : suriya@mersus.ie <br>
> In case of any issues with these guidelines please contact the author.

This document describes the rule and recommendations for developing software application and class libraries in .NET using C# as a language. The main purpose is to define the general guidelines to enforce consistent coding styles and formatting that can be useful for developers to avoid common mistakes they do while development of software applications using C#. This document covers naming conventions, coding styles and some architecture level suggestions.

**This document will serve as the _Mersus Coding Guidelines_, every developer should adhere to these standards and follow the set of rules laid down in these document.**

As our primary language is C# we follow the list of existing guidelines setup by the C# community.

# Table of Contents

- <a href ="#purpose"> Purpose </a>
- <a href = "#namingConventions"> Naming Conventions </a>
- <a href = "#pascalCase"> Pascal Case </a>
- <a href = "#camelCase"> Camel Case </a>
- <a href = "#coroutine"> Coroutine Naming Convention </a>
- <a href = "#commenting">Commenting Conventions</a>

# Purpose:

<div id="purpose">Coding standards are a set of guidelines used for programming language that recommends programming style and best practices to achieve it. </div>
 
The coding standards generally covers indentation, comments, naming conventions, programming practices, file structure within project, architectural best practices etc. Software developers are highly recommended to follow these guidelines. The coding guidelines have following advantages.
- Increases the readability of source code written.
- Will contain fewer bugs and work more efficiently.
- Requires less maintenance.
- Easier for old and new developers to maintain and modify the code.
- Leads to increase in productivity of developers.
- Reduces the overall cost for software development.
- Make the difference between a successful project and a project that is, at worst, dead on delivery. 


# Naming Conventions

<div id = "namingConventions">There are three type of naming conventions generally used while doing C# programming, <br> </div>

**Pascal Convention – First character of all word is in upper case and other characters are in lower case.** <br>
> Example: HelloWorld <br>

**Camel Case Convention – The first character of all words, except the first word, is upper case and other characters are lower case.** <br>
> Example: helloWorld <br>

**Hungarian Case Convention – The data type as prefix is used to define the variable by developers long ago. This convention is not used anywhere now a day’s except local variable declaration.**
> Example:string m_sName; string strName; int iAge;

We at Mersus use both _Pascal and Camel Case_, each convention is supposed to be used in different scenarios.

In the following examples, any of the guidance pertaining to elements marked public is also applicable when working with protected and protected internal elements, all of which are intended to be visible to external callers. 

# Pascal Case

<div id = "pascalCase">Use pascal casing ("PascalCasing") when naming a class, record, or struct. </div>

```
public class DataService
{
}
```

```
public record PhysicalAddress(
    string Street,
    string City,
    string StateOrProvince,
    string ZipCode);
}
```

```
public struct ValueCoordinate
{
}
```
When naming an **interface**, use pascal casing in addition to prefixing the name with an I. This clearly indicates to consumers that it's an **interface**.

```
public interface IWorkerQueue
{
}
```

When naming **public** members of types, such as **fields**, **properties**, **events**, **methods**, and **local functions**, use pascal casing.

```
public class ExampleEvents
{
    // A public field, these should be used sparingly
    public bool IsValid;

    // An init-only property
    public IWorkerQueue WorkerQueue { get; init; }

    // An event
    public event Action EventProcessing;

    // Method
    public void StartEventProcessing()
    {
        // Local function
        static int CountQueueItems() => WorkerQueue.Count;
        // ...
    }
}
```


# Camel Case

<div id="camelCase">Use camel casing ("camelCasing") when naming **private** or **internal** fields, and prefix them with _. </div>

It is paramount that we mark every private variable with an 'underscore' because this practice helps you in searching through all the private variables in your scripts as well makes an explicit differentiation between **private** and **public** variables. 

```
public class DataService
{
    private IWorkerQueue _workerQueue;
}
```
When working with static fields that are private or internal, use the s_ prefix and for thread static use t_.
Usually we don't use static threads in unity but in case of using it, it is good to follow the underlying notations.

```
public class DataService
{
    private static IWorkerQueue s_workerQueue;

    [ThreadStatic]
    private static TimeSpan t_timeSpan;
}
```

When writing method parameters, use camel casing.

```
public T SomeMethod<T>(int someNumber, bool isValid)
{
}
```

# Coroutine Naming Conventions

<div id="coroutine"> Coroutine is something we constantly use, all coroutines need to be written with a suffix 'Co'. </div>

```
IEnumerator CoStopPour()
{
        yield return null;   
}
```
# Commenting Conventions

<div id="#commenting">
 
- Place the comment on a separate line, not at the end of a line of code.
- Begin comment text with an uppercase letter.
- End comment text with a period.
- Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.
- Don't create formatted blocks of asterisks around comments.
- Ensure all public members have the necessary XML comments providing appropriate descriptions about their behavior.
</div>

```
// The following declaration creates a query. It does not run
// the query.

```

