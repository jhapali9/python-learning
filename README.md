# python-learning

---


## 2. Using the Python Interpreter
### 2.1. Invoking the Interpreter
```
    Run a file: python script.py (simple run)

    Run a command: python -c "print('Hello!')" (execute statements in command)

    Run a module: python -m module_name (Find the module by name and run it as a script)

    Stay in interactive mode after script: python -i script.py
```
#### 2.1.1. Argument Passing
 - Inside the sys module → sys.argv (you have to import sys first)
```
    # on the terminal
    python myscript.py hello world

    # inside your code
    import sys
    print(sys.argv)
    print(sys.argv[0])

    # output 
    ['myscript.py', 'hello', 'world']
    hello.py
```

#### 2.1.2. Interactive Mode
- When you run Python with no script: python3.13
- You enter interactive mode, and you’ll see:
```
    Python 3.13 (default, April 4 2023, 09:25:04)
    [GCC 10.2.0] on linux
    Type "help", "copyright", "credits" or "license" for more information.
    >>>

```
- Prompt Types:
  - Primary prompt: >>> — where you type new commands.
  - Secondary prompt: ... — used for continued lines.

```
    >>> for i in range(3):
    ...     print(i)
    ...
    0
    1
    2
```

- Tip: Use interactive mode to test code snippets quickly. Tools like IPython or Jupyter Notebooks offer enhanced interactive features! 

## 2.2. The Interpreter and Its Environment

### 2.2.1. Source Code Encoding
- By default, Python source files are encoded in **UTF-8**.
- UTF-8 supports characters from almost all languages, which means:
  - You can use non-English characters in string literals, comments, and even variable names (though it’s not recommended for portable code).
- Python’s standard library follows the **ASCII-only** convention for identifiers.
- Your text editor should:
  - Detect UTF-8 encoding.
  - Use a font that supports the characters in your file.

##### 📝 Custom Encoding:

To use a different encoding, you must declare it at the top of your Python file using this special comment:

```python
# -*- coding: encoding -*-

- Replace encoding with any valid codec name supported by Python.

```
Example: Use Windows-1252 Encoding
    # -*- coding: cp1252 -*-

    ⚠️ Exception: Shebang Line
    If your file starts with a Unix-style shebang (used to specify the Python interpreter path), then the encoding declaration should go on the second line.

    #!/usr/bin/env python3
    # -*- coding: cp1252 -*-

## 3. An Informal Introduction to Python

#### 🧪 Working with Examples in the Docs

#### 👀 Input vs Output

- In Python documentation:
  - Lines starting with `>>>` or `...` are input prompts.
  - [>>>] → This is a primary prompt: Python is waiting for you to type a new command
  - ... → This is a secondary prompt: Python is expecting you to finish a multi-line statement (like a loop or function).
    - Press Enter to send a blank line (often used to end a block like a function or loop).

#### Example:

```python
>>> for i in range(3):
...     print(i)
...
0
1
2
```

### 3.1. Using Python as a Calculator

#### 📐 3.1.1 Numbers in Python

#### 🧮 Python as a Calculator
---

The Python interpreter can be used just like a calculator!

You can type math expressions directly, and it will give you the result.

```python
>>> 2 + 2
4
>>> 50 - 5*6
20
>>> (50 - 5*6) / 4
5.0
>>> 8 / 5  # Division always returns a float
1.6
```

#### 🔢 Types of Numbers
---
- Whole numbers like 2, 4, 20 → int
- Numbers with decimals like 5.0, 1.6 → float

#### 🔧 More Operations
---
🔽 Floor Division (//) & Remainder (%)
```
>>> 17 / 3  # Regular division
5.666666666666667

>>> 17 // 3  # Floor division: drops the decimal
5

>>> 17 % 3  # Remainder (modulo)
2

>>> 5 * 3 + 2  # 5 full groups of 3, plus 2 leftover = 17
17
```

💥 Power Operator (**)
---
```
>>> 2 ** 7  # 2 to the power of 7
128
```

🗃️ Variables
---
You can store values in variables using =
```
>>> width = 20
>>> height = 5 * 9
>>> width * height
900
```

🚨 If you try to use a variable before assigning it, you'll get an error:
```
>>> n
NameError: name 'n' is not defined
```

🔁 Mixed Type Operations
---

If you mix an int and float, Python automatically converts to float:

```
>>> 4 * 3.75 - 1
14.0
```

🔙 Special Variable: _ (underscore)
---
- In interactive mode, the last result is saved in _.
- Great for quick math chains!

```
>>> tax = 12.5 / 100
>>> price = 100.50
>>> price * tax
12.5625

>>> price + _
113.0625

>>> round(_, 2)
113.06
```
🛑 Don't assign a value to _ — it's managed automatically by Python.



➕ More Number Types

---
Python also supports:
- Decimal for high-precision decimals.
- Fraction for rational numbers.
- complex numbers (with j for the imaginary part):

```
>>> complex_num = 3 + 5j
>>> complex_num
(3+5j)
```

#### 📝 3.1.2. Text (Strings) in Python

💬 What Are Strings?
---

Python can manipulate text using the `str` type, also known as "strings".

Examples:

```
'spam eggs'                            # single quotes
"Paris rabbit got your back :)! Yay!"  # double quotes
'1975'                                 # digits in quotes are strings
```
You can use either '...' or "..." for strings — they behave the same.

🧙 Escaping Quotes
---
Use \ to escape quotes inside strings:
```
'doesn\'t'       # Escapes the single quote
"doesn't"        # Or just use double quotes

'"Yes," they said.'
"\"Yes,\" they said."
'"Isn\'t," they said.'
```

📤 print() vs Just Typing
---
```
s = 'First line.\nSecond line.'
s           # Shows the raw string with \n
print(s)    # Interprets \n as newline
```
🔒 Raw Strings
---
- Add r before the string to prevent escape characters from being processed:
```
print('C:\some\name')    # \n is a newline
print(r'C:\some\name')   # raw string, prints as-is
```
- Note: Raw strings can’t end in an odd number of backslashes!


🧵 Multiline Strings
---
- Use triple quotes ('''...''' or """...""") for strings over multiple lines:
```
print("""\
Usage: thingy [OPTIONS]
     -h                        Display this usage message
     -H hostname               Hostname to connect to
""")
```
➕ Concatenation and Repetition
---
```
3 * 'un' + 'ium'    # Repeat and add
# Output: 'unununium'

'Py' 'thon'         # Adjacent string literals auto-concatenate
# Output: 'Python'
```
- Useful for breaking up long strings:
```
text = ('Put several strings within parentheses '
        'to have them joined together.')
```
- But doesn’t work with variables or expressions:
```
prefix = 'Py'
prefix 'thon'       # ❌ SyntaxError
```
- Use + instead:
```
prefix + 'thon'     # ✅ Output: 'Python'
```
🎯 Indexing Strings
---
- Strings are indexed with 0-based positions.
- No char type in Python — just strings of length 1.
```
word = 'Python'
word[0]     # 'P'
word[5]     # 'n'
word[-1]    # 'n' (last character)
word[-2]    # 'o' (second to last)
```
✂️ Slicing Strings
---
```
word[0:2]   # 'Py'
word[2:5]   # 'tho'
word[:2]    # 'Py' (same as word[0:2])
word[4:]    # 'on'
word[-2:]   # 'on'
```
```
 +---+---+---+---+---+---+
 | P | y | t | h | o | n |
 +---+---+---+---+---+---+
 0   1   2   3   4   5   6
-6  -5  -4  -3  -2  -1
```
- Slice from i to j → includes i, excludes j.
- word[:i] + word[i:] == word

🚫 Index Out of Range
---
```
word[42]    # ❌ IndexError
word[4:42]  # ✅ 'on'
word[42:]   # ✅ ''
```
🔐 Strings Are Immutable
---
- You can’t change parts of a string directly:
```
word[0] = 'J'    # ❌ TypeError
word[2:] = 'py'  # ❌ TypeError
```
- Instead, make a new string:
```
'J' + word[1:]       # 'Jython'
word[:2] + 'py'      # 'Pypy'
```
📏 Length of a String
---
```
s = 'supercalifragilisticexpialidocious'
len(s)      # 34
```

Text Sequence Type — str
---
📌 What is `str`?

- In Python, textual data is represented using `str` objects (strings).
- Strings are **immutable sequences** of **Unicode code points**.
- Indexing a string returns another string of length 1 — Python has no separate `char` type.

🧱 Ways to Define Strings

```python
'Single quotes'                       # can contain "double quotes"
"Double quotes"                       # can contain 'single quotes'
'''Triple single quotes'''            # for multi-line strings
"""Triple double quotes"""            # also for multi-line strings
```
Implicit String Concatenation
---
- Adjacent string literals with only whitespace between them are automatically joined:
```
("spam " "eggs") == "spam eggs"   # ✅ True
```
Creating Strings with str()
---

```
str(123)               # '123'
str(['a', 'b'])        # "['a', 'b']"

# creating a bytes object instead of a string
# converting the bytes object into a string representation of that object.
#  instead of converting it into "hello", it gives you the literal form, "b'hello'"
# Useful for working with binary data, network protocols, file I/O, and cryptographic operations.

str(b'hello')          # "b'hello'" 

# convert b'hello' back to a normal string using either of two :

b'hello'.decode()                # Output: 'hello'
str(b'hello', encoding='utf-8')  # Output: 'hello'

```

```
# If the object has a __str__() method, that’s what gets called.
class Dog:
    def __str__(self):
        return "I'm a dog!"
        
d = Dog()
print(str(d))  # This will call d.__str__()
```















