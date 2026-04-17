# Reusing other people's code in your projects

Increase your coding efficiency and knowledge by integrating existing code into your projects.

One of the best things about open source software is the ability to reuse other people's code. Repurposing code helps you save time, discover new functionality, and learn other programming styles. There are two main ways to reuse code:

* **Copying and pasting a code snippet directly into your project.** If you're new to coding, this is the quickest way to start reusing code.
* **Importing a library into your project.** While this approach takes some time to learn, it's ultimately easier and more efficient. It's also a foundational skill for software development.

In this article, we'll learn both by working through an example: reusing Python code that calculates the factorial of a number.

## Using other people's code snippets in your project

When you're first learning to code, you might start with reuse by copying and pasting other people's code snippets into your project. It's a great way to save time, but there are a few key steps you should always take before copying another developer's code.

### 1. Finding and understanding a code snippet

First, you need to find and understand the code snippet you want to reuse. For this example, we'll choose the [`new2code/python-factorial`](https://github.com/new2code/python-factorial) repository.

First, **open** [`factorial_finder.py`](https://github.com/new2code/python-factorial/blob/main/factorial_finder.py), which implements the calculator using a loop:

```python
# Initialize the factorial result to 1
factorial = 1

# Initialize the input number to 6
number = 6

# Loop from 1 to number (inclusive) and multiply factorial by each number
for i in range(1, number + 1):
    factorial *= i

print(f"The factorial of {number} is {factorial}")
```

Then, in the menu bar at the top of the file, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="Ask Copilot about this file" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg> to start a conversation with Copilot.

![Screenshot of the Copilot button, outlined in dark orange, at the top of the file view.](/assets/images/help/copilot/factorial-finder-copilot-button.png)

In the chat window, ask Copilot:

```text copy
Explain this program.
```

### 2. Understanding project licensing

Before you can reuse the code you've found, you need to understand its licensing. Licenses determine how you can use the code in a project, including your ability to copy, modify, and distribute that code.

To identify the license for [new2code/python-factorial](https://github.com/new2code/python-factorial), locate the "About" section on the repository's main page. There, you'll see that the repository is licensed under the MIT license. To read the license, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-law" aria-label="law" role="img"><path d="M8.75.75V2h.985c.304 0 .603.08.867.231l1.29.736c.038.022.08.033.124.033h2.234a.75.75 0 0 1 0 1.5h-.427l2.111 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.006.005-.01.01-.045.04c-.21.176-.441.327-.686.45C14.556 10.78 13.88 11 13 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L12.178 4.5h-.162c-.305 0-.604-.079-.868-.231l-1.29-.736a.245.245 0 0 0-.124-.033H8.75V13h2.5a.75.75 0 0 1 0 1.5h-6.5a.75.75 0 0 1 0-1.5h2.5V3.5h-.984a.245.245 0 0 0-.124.033l-1.289.737c-.265.15-.564.23-.869.23h-.162l2.112 4.692a.75.75 0 0 1-.154.838l-.53-.53.529.531-.001.002-.002.002-.006.006-.016.015-.045.04c-.21.176-.441.327-.686.45C4.556 10.78 3.88 11 3 11a4.498 4.498 0 0 1-2.023-.454 3.544 3.544 0 0 1-.686-.45l-.045-.04-.016-.015-.006-.006-.004-.004v-.001a.75.75 0 0 1-.154-.838L2.178 4.5H1.75a.75.75 0 0 1 0-1.5h2.234a.249.249 0 0 0 .125-.033l1.288-.737c.265-.15.564-.23.869-.23h.984V.75a.75.75 0 0 1 1.5 0Zm2.945 8.477c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L13 6.327Zm-10 0c.285.135.718.273 1.305.273s1.02-.138 1.305-.273L3 6.327Z"></path></svg> **MIT license**.

![Screenshot of the main page of the new2code/python-factorial repository. In the right sidebar, "MIT license" is outlined in dark orange.](/assets/images/help/repository/license-info-python-factorial.png)

We want to copy the entire `factorial_finder.py` file, so the MIT license indicates that we should include a copy of the license in our own project. At the top of your Python file, paste the license as a comment.

> \[!TIP] You can learn what's allowed by other common licenses with the [Choose a license](https://choosealicense.com/licenses/) tool.

### 3. Using and modifying code snippets

Now, you're ready to paste the code snippet into your project. While you'll sometimes to be able to use code snippets as they are, you will often want to **modify** them for your specific use case. Let's practice that now!

Let's say we want to quickly calculate the factorials of 5, 7, 9, and 10. Instead of copying and pasting the entire program for each number, we can move our calculator into a **function** that takes a number as an argument.

Use [Copilot Chat](https://github.com/copilot) to suggest and explain an implementation. Paste our current code into the chat window, followed by this prompt:

```text copy
Wrap the Python code above in a function.
```

Copilot will generate code that looks something like this:

```python copy
def calculate_factorial(number):
    # Initialize the factorial result to 1
    factorial = 1

    # Loop from 1 to number (inclusive) and multiply factorial by each number
    for i in range(1, number + 1):
        factorial *= i

    return factorial
```

With our new function, we can easily find the factorials of our numbers by adding the following code to our project, then running the Python program:

```python copy
print(calculate_factorial(5))
print(calculate_factorial(7))
print(calculate_factorial(9))
print(calculate_factorial(10))
```

Congratulations! You've successfully found, understood, and modified an example code snippet.

## Using code from libraries in your project

Now, let's learn how to use libraries, which is **standard practice** for developers. Libraries are essentially collections of code written by other developers to perform specific tasks. You can import libraries into your project to use the pre-written code, saving you time and effort.

In this section, we'll continue working with the Python factorial calculator example from the previous section. For reference, here's our current code:

```python copy
def calculate_factorial(number):
    # Initialize the factorial result to 1
    factorial = 1

    # Loop from 1 to number (inclusive) and multiply factorial by each number
    for i in range(1, number + 1):
        factorial *= i

    return factorial

print(calculate_factorial(5))
print(calculate_factorial(7))
print(calculate_factorial(9))
print(calculate_factorial(10))
```

### 1. Finding a library

Once you know what functionality you want to add to your project, you can search for a library with relevant code. Copilot Chat is an easy way to search for libraries, since you can use natural language to describe exactly what you're looking for.

Finding a factorial is a pretty common function, and there's a good chance someone included that function in an existing library. Open [Copilot Chat](https://github.com/copilot), then ask:

```text copy
Is there a Python library with a function for calculating a factorial?
```

Copilot will tell us a factorial function is included in the [`math`](https://docs.python.org/3/library/math.html) module from the standard Python library.

### 2. Prioritizing security in your project

When you add a library or module to your project, you create what's called a **dependency**. Dependencies are pre-written code bundles that your project relies on to function correctly. If they aren't carefully written or maintained, they can introduce security vulnerabilities to your work.

Thankfully, there are some steps you can take to best protect your project. Let's practice them now.

#### Using popular libraries

Popular libraries are more likely to be secure, because they are actively maintained and used by many developers. One good marker of popularity is the number of **stars** a repository has. If you can't find the GitHub repository for a dependency, you can ask Copilot for help.

Open [Copilot Chat](https://github.com/copilot), then ask:

```text copy
Find the GitHub repository containing the code for the math module in Python.
```

Copilot will tell you that the `math` module is defined in [`python/cpython`](https://github.com/python/cpython), which has over 64,000 stars.

#### Enabling Dependabot alerts for your project

When enabled, Dependabot alerts are automatically generated when Dependabot detects a security issue in your dependencies, helping you quickly fix vulnerabilities. Dependabot is available for **free** on all open source GitHub repositories.

Turn Dependabot alerts on for your repository now. Click the **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-shield" aria-label="shield" role="img"><path d="M7.467.133a1.748 1.748 0 0 1 1.066 0l5.25 1.68A1.75 1.75 0 0 1 15 3.48V7c0 1.566-.32 3.182-1.303 4.682-.983 1.498-2.585 2.813-5.032 3.855a1.697 1.697 0 0 1-1.33 0c-2.447-1.042-4.049-2.357-5.032-3.855C1.32 10.182 1 8.566 1 7V3.48a1.75 1.75 0 0 1 1.217-1.667Zm.61 1.429a.25.25 0 0 0-.153 0l-5.25 1.68a.25.25 0 0 0-.174.238V7c0 1.358.275 2.666 1.057 3.86.784 1.194 2.121 2.34 4.366 3.297a.196.196 0 0 0 .154 0c2.245-.956 3.582-2.104 4.366-3.298C13.225 9.666 13.5 8.36 13.5 7V3.48a.251.251 0 0 0-.174-.237l-5.25-1.68ZM8.75 4.75v3a.75.75 0 0 1-1.5 0v-3a.75.75 0 0 1 1.5 0ZM9 10.5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Security and quality** tab for your project's GitHub repository. Next to Dependabot alerts, click **Enable Dependabot alerts**. You can access Dependabot alerts from the **Dependabot** tab of the sidebar.

### 3. Implementing code from a library

Now you're ready to import the library into your project, then use its contents in your code. You can read the documentation for the library to learn how to do it yourself, or you can ask Copilot to suggest and explain an implementation for you.

Open [Copilot Chat](https://github.com/copilot), then ask:

```text copy
How do I use the factorial function of the math module in my Python project?
```

Copilot will then suggest a version of the following code:

```python copy
import math

# Calculate the factorial of a number
number = 5
result = math.factorial(number)

print(f"The factorial of {number} is {result}")
```

After you replace the existing code in your project with the above implementation, you've successfully used code from a library in your example project!

## Sharing your work

With this tutorial, you've learned how to safely reuse other people's code in your own work. To celebrate, share how you repurposed code and built on the example project in our [community discussion](https://github.com/orgs/community/discussions/153140).

## Further reading

* [Finding and understanding example code](/en/get-started/learning-to-code/finding-and-understanding-example-code)