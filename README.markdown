## Table of Contents

- [The Official arway.ai C# Style Guide](https://www.arway.ai/)
  - [Inspiration](#inspiration)
  - [Nomenclature](#nomenclature)
    - [Namespaces](#namespaces)
    - [Classes & Interfaces](#classes--interfaces)
    - [Methods](#methods)
    - [Fields](#fields)
    - [Properties](#properties)
    - [Parameters](#parameters)
    - [Actions](#actions)
    - [Misc](#misc)
  - [Declarations](#declarations)
    - [Access Level Modifiers](#access-level-modifiers)
    - [Fields & Variables](#fields--variables)
    - [Classes](#classes)
    - [Interfaces](#interfaces)
  - [Spacing](#spacing)
    - [Indentation](#indentation)
      - [Blocks](#blocks)
      - [Line Wraps](#line-wraps)
    - [Line Length](#line-length)
    - [Vertical Spacing](#vertical-spacing)
  - [Brace Style](#brace-style)
  - [Switch Statements](#switch-statements)
  - [Language](#language)
  - [Copyright Statement](#copyright-statement)

# The Official ARway C# Style Guide

This style guide is different from others you may find, because the focus is
centered on readability for app and SDKs. We created this style guide to
keep the code in our app/SDK consistent.  

Our overarching goals are **conciseness**, **readability** and **simplicity**. Also, this guide is written to keep **Unity** in mind. 

## Inspiration

[This style guide is based Microsoft Guide](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/identifier-names#naming-rules) 




## Nomenclature

On the whole, naming should follow C# standards.

### Namespaces

Namespaces are all **PascalCase**, multiple words concatenated together, without hyphens ( - ) or underscores ( \_ ). The exception to this rule are acronyms like GUI or HUD, which can be uppercase:

**AVOID**:

```csharp
com.ARwayKit.CreatorView.XXXX
```

**PREFER**:

```csharp
ARwayKit.CreatorView.XXXX
```

### Classes & Interfaces

Classes and interfaces are written in **PascalCase**. For example `RadialSlider`. 

### Methods

Methods are written in **PascalCase**. For example `DoSomething()`. 

### Fields

All non-static fields are written **camelCase**. Per Unity convention, this includes **public fields** as well.

For example:

```csharp
public class MyClass 
{
    public int publicField;
    int packagePrivate;
    private int m_myPrivate;
    protected int myProtected;
}
```

**AVOID:**

```csharp
private int myPrivateVariable
```

**PREFER:**

```csharp
private int _myPrivateVariable
```

Static fields are the exception and should be written in **PascalCase**:

```csharp
public static int TheAnswer = 42;
```
### Properties

All properties are written in **PascalCase**. For example:

```csharp
public int PageNumber 
{
    get { return pageNumber; }
    set { pageNumber = value; }
}
```

### Parameters

Parameters are written in **camelCase**.

**AVOID:**

```csharp
void DoSomething(Vector3 Location)
```

**PREFER:**

```csharp
void DoSomething(Vector3 location)
```

Single character values are to be avoided except for temporary looping variables.

### Actions

Actions are written in **PascalCase**. For example:

```csharp
public event Action<int> ValueChanged;
```

### Misc

In code, acronyms should be treated as words. For example:

**AVOID:**

```csharp
XMLHTTPRequest
String URL
findPostByID
```  

**PREFER:**

```csharp
XmlHttpRequest
String url
findPostById
```

## Declarations

### Access Level Modifiers

Access level modifiers should be explicitly defined for classes, methods and member variables.

### Fields & Variables

Prefer single declaration per line.

**AVOID:**

```csharp
string username, twitterHandle;
```

**PREFER:**

```csharp
string username;
string twitterHandle;
```

### Classes

Exactly one class per source file, although inner classes are encouraged where scoping appropriate.

### Interfaces

All interfaces should be prefaced with the letter **I**. 

**AVOID:**

```csharp
RadialSlider
```

**PREFER:**

```csharp
IRadialSlider
```

## Spacing

Spacing is especially important in arway.ai code, as code needs to be easily readable as part of the tutorial. 

### Indentation

Indentation should be done using **spaces** — never tabs.  

#### Blocks

Indentation for blocks uses **4 spaces** for optimal readability:

**AVOID:**

```csharp
for (int i = 0; i < 10; i++) 
{
  Debug.Log("index=" + i);
}
```

**PREFER:**

```csharp
for (int i = 0; i < 10; i++) 
{
    Debug.Log("index=" + i);
}
```

#### Line Wraps

Indentation for line wraps should use **4 spaces** (not the default 8):

**AVOID:**

```csharp
CoolUiWidget widget =
        someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line);
```

**PREFER:**

```csharp
CoolUiWidget widget =
    someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line);
```

### Line Length

Lines should be no longer than **100** characters long.

### Vertical Spacing

There should be exactly one blank line between methods to aid in visual clarity 
and organization. Whitespace within methods should separate functionality, but 
having too many sections in a method often means you should refactor into
several methods.


## Brace Style

All braces get their own line as it is a C# convention:

**AVOID:**

```csharp
class MyClass {
    void DoSomething() {
        if (someTest) {
          // ...
        } else {
          // ...
        }
    }
}
```

**PREFER:**

```csharp
class MyClass
{
    void DoSomething()
    {
        if (someTest)
        {
          // ...
        }
        else
        {
          // ...
        }
    }
}
```

Conditional statements are always required to be enclosed with braces,
irrespective of the number of lines required.

**AVOID:**

```csharp
if (someTest)
    doSomething();  

if (someTest) doSomethingElse();
```

**PREFER:**

```csharp
if (someTest) 
{
    DoSomething();
}  

if (someTest)
{
    DoSomethingElse();
}
```
## Switch Statements

Switch-statements come with `default` case by default (heh). If the `default` case is never reached, be sure to remove it.

**AVOID:**  
  
```csharp
switch (variable) 
{
    case 1:
        break;
    case 2:
        break;
    default:
        break;
}
```

**PREFER:**  
  
```csharp
switch (variable) 
{
    case 1:
        break;
    case 2:
        break;
}
```

## Language

Use US English spelling.

**AVOID:**

```csharp
string colour = "red";
```

**PREFER:**

```csharp
string color = "red";
```

The exception here is `MonoBehaviour` as that's what the class is actually called.

## Copyright Statement

The following copyright statement should be included at the top of every source file:

    /*
     * Copyright (C) 2020 ARWAY Ltd. All Rights Reserved.
     * 
     * This file is part of ARwayKit AR SDK
     * The ARwayKit SDK cannot be copied, distributed, or made available to
     * third-parties for commercial purposes without written permission 
     * of ARWAY Ltd.
     */

In this repository, copy the **ScripTemplates** folder into your own Unity **Assets** folder. This way the header above will be included in new scripts.


