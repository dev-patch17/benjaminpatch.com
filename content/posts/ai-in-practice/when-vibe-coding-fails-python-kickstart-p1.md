Title: When Vibe Coding Fails: Python Kickstart (part 1)
Date: 2025-05-13 00:17
Category: AI in Practice
Tags: python, python kickstart, virtual environments, best practices, vibe coding, open-source, generative ai
Slug: when-vibe-coding-fails-python-kickstart-p1
Description: Python Kickstart: Part One. Why should you learn Python in the age of vibe coding? Then get your feet wet by learning how to start writing Python code.
Summary: Welcome to part one of my Python Kickstart series! Let's discuss why you should still learn Python in the age of vibe coding. Then we'll get our feet wet by learning about running Python code. An introduction to variables, the print function, basic errors, and code comments. Let's get started!

## Why Learn Python?

From web development to data science to machine learning applications, Python has become one of today's most in-demand programming languages. Being skilled with it opens countless possibilities for your career. Its clean syntax and logical structure make it easy to learn and even fun to use!

Python's massive number of powerful modules, packages, and frameworks extend the language into virtually any domain of interest. Not to mention this is all fully open-source, making it free to use, modify, and redistribute - including for commercial purposes.

## Why Isn't Vibe Coding the Answer?

Now, you may have heard some AI startup CEOs proclaim it is essentially a “waste of time to learn how to code in 2025.”<sup>[1](#works-cited)</sup> I strongly disagree with these comments for several reasons. To start, I have first-hand experience asking LLMs (Large Language Models) to write and/or edit various types of code on my behalf. And while their speed and general capabilities can be astonishing, like people, they still make mistakes. And these mistakes can lead to broken and/or highly unmaintainable codebases.

To catch and correct mistakes from LLM-generated code (AKA vibe coding), you need to understand the fundamentals of the programming languages, modules, packages, and frameworks your application requires. Otherwise, it’s like asking an LLM a general question in English and receiving a response in Japanese. If you have no understanding of Japanese, you will be hard-pressed to refine any output it produces.

Plus, let's not forget those AI startup CEOs have a vested interest in you being totally reliant on their products. Knowledge is power. Please don't outsource your critical thinking skills to AI. It's a tool, not a replacement for your brain.

## Is There a Place for AI in Coding?

Even with that being said, there absolutely is a place for AI-assisted coding. Once you understand the basics, AI tools can supercharge your productivity - even acting as a paired-programming partner. The key is understanding what these LLMs excel at, and when you need to take the lead.

The first step in getting to that point is understanding the fundamentals of Python - or any programming language for that matter. As I recently read, "Vibe coding is fun, but **vibe refactoring** pays the bills."<sup>[2](#works-cited)</sup>

With that in mind, let’s kickstart our knowledge of Python programming!

## Install Python 3

If you don’t already have a Python development environment set up, there are several ways you can do this. The method I recommend is creating a virtual environment using `pyenv`. If you’re not familiar with installing Python via `pyenv`, please reference [Simple Python Virtual Environments: Linux and Mac](https://www.benjaminpatch.com/posts/2025/Jan/30/simple-python-virtual-environments-linux-mac/) where I explain the benefits of this approach and walk you through the necessary steps to get rolling.

As noted in the linked article above, Windows users should use [pyenv-win](https://github.com/pyenv-win/pyenv-win) instead.

Because this **Python Kickstart** series of articles is an introduction to the basic principles and syntax of the language, any currently supported version of Python 3 is sufficient to install. Support for all versions of Python 2 were sunset in January 2020<sup>[3](#works-cited)</sup>, and it is quite different. So please use Python 3.

I generally recommend choosing the most current stable release (`3.13` as of this writing) unless your project specifically requires something older.

With Python 3 installed and running on your system, let’s get started with this incredible programming language!

## Run Python Code in Your Terminal

There are many ways to execute (or run) Python code, but for the purposes of learning the basics, I recommend using a combination of your system's terminal and a code editor. Let's start with your terminal, then we'll bring a code editor into the mix.

To run Python code in your terminal, simply type:

```bash
# Linux and Mac:
python3 # or just 'python' if pyenv was used to install Python

# or on Windows:
py
```

Press `enter` and the Python interpreter will open. It will look something like this (colors will vary based on your shell configuration):

```python
Python [version number] (plus info about your system)
Type "help", "copyright", "credits" or "license" for more information.
>>> # Python code goes here
```

From here, you can run any Python code. To exit the interpreter, type `ctrl-d` on Linux/Mac or `ctrl-z` on Windows, followed by `enter`. If that doesn’t work, you can also exit by typing: `quit()` or `exit`, followed by `enter`.

## Variables

```python
greeting = "Hello, Python!"
```

In the example above, `greeting` is the variable, and it is set to the `string` (a sequence of characters inside quotes) `Hello, Python!` The equals sign (`=`) is called an **assignment operator**. A few rules to keep in mind:

- Variables cannot start with a number. So `x1` is a valid variable, but `1x` is not valid and will throw a syntax error.
- Variables also cannot contain spaces or special characters other than an underscore (`_`).
- Traditionally, variables start with lowercase letters so they are not confused with a `class`. More on classes later in this series.

In Python, variables can be assigned to just about anything the language supports - as we will see moving forward.

## Python's `print()` Function

If we open the Python interpreter in our terminal (`python3` on Linux/Mac or `py` on Windows), and enter the following two lines of code:

```python
greeting = "Hello, Python!"
print(greeting)
```

The output will be:

```
Hello, Python!
```

The `print()` function is built into Python and displays the specified message on screen. Anything inside the `()` becomes the output. We’ll be using the `print()` function extensively so you gain a better understanding of what the code is doing.

## Jump into a Code Editor

Writing and running code in the Python interpreter is fine for simple checks, but anything longer than a few lines should be written to a `.py` (Python) file with your preferred code editor.

If you don’t yet have a preferred code editor, I recommend starting with [Visual Studio Code](https://code.visualstudio.com/). It’s free, has excellent Python support (with a few free extensions), and runs well on Linux, Mac, and Windows.

If you would like to follow along with the following code examples, feel free to create a `.py` file in your code editor. As long as it ends with `.py`, it can be called almost anything you would like, I’ll go with `python_kickstart.py`. Like variables, spaces and special characters (other than underscores) are not allowed. Your filename also cannot start with a number.

Now in our `.py` file, write the following code:

```python
x = 4 + 3
print(x)
```

Save your `python_kickstart.py` file.

Next, go back to your terminal and, if it is still running, exit the Python interpreter (`ctrl-d` on Linux/Mac or `ctrl-z` on Windows).

Then `cd` (change directory) into the location where `python_kickstart.py` lives. And run:

```bash
# Linux and Mac:
python3 python_kickstart.py

# or on Windows:
py python_kickstart.py
```

And your terminal will return:

```
7
```

Great job! You just asked Python to run the code in `python_kickstart.py` and return the results. In this case, Python didn't simply print `4 + 3` but it did the arithmetic and only printed the result.

Going forward, I encourage you to manually write out (refrain from copy and paste) and execute the code examples for the topics we'll be covering. Then create a few more samples following the same patterns but with different content. I find this to be the most effective way to retain, understand, and eventually apply these foundational Python programming concepts.

## Python Errors

We all make mistakes. And when mistakes happen within your code, Python might throw an error message. This is nothing to be afraid of because Python error messages routinely provide helpful information - guiding you to narrow down the problem. For example, Python will point to the location where an error occurred with one or more `^` characters like this:

```python
python_error = "Let's see if this works."
print(python_error
```

output:

```python
  File ".../python_kickstart.py", line 2
    print(python_error
         ^
SyntaxError: '(' was never closed
```

This is called a `SyntaxError`, which means there is something wrong with the way our program is written — punctuation that does not belong, a command where it is not expected, or a missing parenthesis (as seen above) can all trigger a `SyntaxError`.

Between the specific line number being noted, the `^` pointing, and the `SyntaxError` message, this all makes it very clear what we did wrong. Thanks, Python!

Another common error type is called a `NameError`:

```python
print(best_movie)
```

With no further context, this Python code will output:

```python
Traceback (most recent call last):
  File ".../python_kickstart.py", line 1, in <module>
    print(best_movie)
          ^^^^^^^^^^
NameError: name 'best_movie' is not defined
```

A `NameError` occurs when the Python interpreter sees a word it does not recognize. Code that contains something that looks like a variable but was never defined (as seen above) will throw such an error.

Again, this detailed feedback makes simple debugging much easier than the code simply failing and maybe outputting some cryptic message. Good programmers read and try to decipher error messages. Python tries to help where it can - going well beyond many other programming languages in this regard.

## Python Comments

You may have already noticed the use of `#`. In Python, `#` indicates anything that follows on the same line, is a comment. Python ignores all comments when running code, so they do not affect the output.

Comments can be thought of as notes for people. In fact, many programmers use comments as a form of documentation. Stating the intended purpose of a function, for example, can help other developers (or your future self) follow the logic of the program.

```python
# This is a single-line comment

"""
This is a multi-line comment

Anything inside the triple quotes is also ignored by the Python interpreter 
"""
```

A set of three single quotes also works:

```python
'''
Multi-line comments can also be surrounded by a set of three single quotes

The end result is the same as using a set of three double quotes
'''
```

Comments are a great way of explaining existing code or to outline future plans. Code comments are incredibly helpful and I encourage you to use them.

In fact, if you ever need to ask an AI model to generate code for you (in the future, only after you learn the basics), direct it to document the output with code comments. This way, even when the code is broken, you'll have a better idea what the AI was trying to do. Then you can use your Python skills to refactor and fix it!

## Basic Python Data Types

In Python, there are three basic data types:

- Strings
- Numbers
- Booleans

The next article in this series dives into these data types and then continues with data structures, which are both crucial in writing effective Python programs. Thanks for your interest in learning Python, and I'll catch you next time!

Up next: [Python Kickstart (part 2): Data Types and Data Structures](https://www.benjaminpatch.com/posts/2025/Jul/09/python-kickstart-p2-data-types-structures/)

<a id="works-cited"></a>
## Works Cited

1. [Replit CEO Explains Why Learning To Code Is Pointless In AI Era](https://www.ndtv.com/feature/replit-ceo-explains-why-learning-to-code-is-pointless-in-ai-era-instead-learn-how-to-8039962) - NDTV, accessed May 12, 2025.
2. [Vibe Coding Is Fun - But Vibe Refactoring Pays the Bills](https://dawidmakowski.com/en/2025/04/vibe-coding-is-fun-but-vibe-refactoring-pays-the-bills/) - Dawid Makowski, accessed May 12, 2025.
3. [Sunsetting Python 2](https://www.python.org/doc/sunset-python-2/) - python.org, accessed May 12, 2025.
