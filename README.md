# mersus-coding-guidelines

> Author : Suriya Palaniswami <br>
> Email : suriya@mersus.ie <br>
> In case of any issues with these guidelines please contact the author.



This document describes the rule and recommendations for developing software application and class libraries in .NET using C# as a language. The main purpose is to define the general guidelines to enforce consistent coding styles and formatting that can be useful for developers to avoid common mistakes they do while development of software applications using C#. This document covers naming conventions, coding styles and some architecture level suggestions.

**This document will serve as the _Mersus Coding Guidelines_, every developer should adhere to these standards and follow the set of rules laid down in these document.**

As our primary language is C# we follow the list of existing guidelines setup by the C# community.

**Purpose:**

Coding standards are a set of guidelines used for programming language that recommends programming style and best practices to achieve it.
 
The coding standards generally covers indentation, comments, naming conventions, programming practices, file structure within project, architectural best practices etc. Software developers are highly recommended to follow these guidelines. The coding guidelines have following advantages.
- Increases the readability of source code written.
- Will contain fewer bugs and work more efficiently.
- Requires less maintenance.
- Easier for old and new developers to maintain and modify the code.
- Leads to increase in productivity of developers.
- Reduces the overall cost for software development.
- Make the difference between a successful project and a project that is, at worst, dead on delivery.


# Naming Conventions

There are three type of naming conventions generally used while doing C# programming, <br>

**Pascal Convention – First character of all word is in upper case and other characters are in lower case.** <br>
> Example: HelloWorld <br>

**Camel Case Convention – The first character of all words, except the first word, is upper case and other characters are lower case.** <br>
> Example: helloWorld <br>

**Hungarian Case Convention – The data type as prefix is used to define the variable by developers long ago. This convention is not used anywhere now a day’s except local variable declaration.**
> Example:string m_sName; string strName; int iAge;

We at Mersus use both _Pascal and Camel Case_, each convention is supposed to be used in different scenarios.

In the following examples, any of the guidance pertaining to elements marked public is also applicable when working with protected and protected internal elements, all of which are intended to be visible to external callers.

# Pascal Case

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

