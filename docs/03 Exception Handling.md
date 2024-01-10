# Exception Handling in Python

Our code generates a number of errors. In this section, we are going to look out for them and how to avoid them.

In **Prof. Madhavan's** words, we will learn how to _Recover gracefully_.

### Common Types of Errors while a program is syntactically valid:

| Name of Error |               Cause               |
| :-----------: | :-------------------------------: |
|   NameError   | Variable used before initialising |
|   ZeroError   |    A number is divided by zero    |
|  IndexError   |       List is out of range        |
|   KeyError    | Key does not exist in dictionary  |

### Using try-except block

Python provides a way to handle exceptions in the code using try-except block.

```py linenums="1"
try:
  # Some code to run here
except errorName: # if you want to execute something on specific error
  # Handle the specific error here.
except: # Handles all the general errors
  # General error handling
else:
  # Code if your try block runs without any error
```

### Using exceptions "positively"

Exceptions are of a great use and you can use them to make your program greatly readable and efficient.

**Example**: Adding a new key in dictionary

Let `D` be a dictionary whose values of lists and we want to add key `t` to it.

```py linenums="1"
try:
  D[t].append("abc")
except KeyError:
  D[t] = ["abc"]
```
