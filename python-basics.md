# Python Basics

**Resources:**
- [Python Official Tutorial](https://docs.python.org/3/tutorial/)
- [Real Python Python Basics](https://realpython.com/python-basics/)

## Variables and Data Types
```python
name = "John"
age = 25
height = 5.9
is_student = True

# Data types
string = "Hello"
integer = 42
float_num = 3.14
boolean = True
list_example = [1, 2, 3, 4]
tuple_example = (1, 2, 3)
dict_example = {"key": "value", "age": 25}
```

## Control Structures

### If Statements
```python
if age >= 18:
    print("Adult")
elif age >= 13:
    print("Teenager")
else:
    print("Child")
```

### For Loops
```python
for i in range(5):          # Range: 0, 1, 2, 3, 4
    print(i)

for item in [1, 2, 3]:      # List iteration
    print(item)

for char in "hello":        # String iteration
    print(char)

for key, value in {"a": 1, "b": 2}.items():  # Dictionary iteration
    print(key, value)

for i, item in enumerate([10, 20, 30]):      # Index and value
    print(i, item)
```

### While Loops
```python
count = 0
while count < 5:
    print(count)
    count += 1

# Infinite loop with break
while True:
    user_input = input("Enter 'quit' to exit: ")
    if user_input == 'quit':
        break
```

### Loop Control
```python
for i in range(10):
    if i == 3:
        continue            # Skip rest of iteration
    if i == 8:
        break              # Exit loop completely
    print(i)
```

### Loop Differences
- **For loops**: Use when you know iterations or have a sequence
- **While loops**: Use when condition-based termination is needed

## Error Handling

**Resources:**
- [Python docs: Errors and Exceptions](https://docs.python.org/3/tutorial/errors.html)
- [Real Python Exception Handling](https://realpython.com/python-exceptions/)

### Try-Catch
```python
# Basic try-except
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")

# Multiple exceptions
try:
    number = int(input("Enter a number: "))
    result = 10 / number
except ValueError:
    print("Invalid input! Please enter a number.")
except ZeroDivisionError:
    print("Cannot divide by zero!")

# Try-except-else-finally
try:
    file = open("data.txt", "r")
    data = file.read()
except FileNotFoundError:
    print("File not found!")
else:
    print("File read successfully")
finally:
    file.close()  # Always runs
```

### Common Exceptions to Raise
```python
# ValueError - wrong value format/content
raise ValueError("Invalid email format")

# TypeError - wrong data type
raise TypeError("Expected string, got integer")

# KeyError - dictionary key not found
raise KeyError("Missing required key 'password'")

# FileNotFoundError - file doesn't exist
raise FileNotFoundError("Config file not found")

# IndexError - list index out of range
raise IndexError("List index out of range")
```

### Input Validation
```python
def validate_email(email):
    if not email:
        return False, "Email cannot be empty"
    if "@" not in email:
        return False, "Email must contain @"
    return True, "Valid email"

def validate_password(password):
    errors = []
    if len(password) < 8:
        errors.append("Password must be at least 8 characters")
    if not any(c.isupper() for c in password):
        errors.append("Password must contain uppercase letter")

    if errors:
        return False, errors
    return True, "Password is valid"
```

### When to Use Try-Catch vs If Validation
- **Use if validation for**: User input, business logic, predictable conditions
- **Use try-catch for**: File operations, network requests, type conversions

## Functions
```python
def greet(name, age=None):
    if age:
        return f"Hello {name}, you are {age} years old"
    return f"Hello {name}"

# Lambda functions
square = lambda x: x**2
```

## Type Checking with isinstance()

**Resources:**
- [Real Python isinstance() tutorial](https://realpython.com/what-does-isinstance-do-in-python/)
- [Python docs: isinstance()](https://docs.python.org/3/library/functions.html#isinstance)
```python
def process_data(data):
    if isinstance(data, str):
        return data.upper()
    elif isinstance(data, int):
        return data * 2
    elif isinstance(data, list):
        return len(data)
    else:
        return "Unknown type"

# Multiple types
def handle_number(value):
    if isinstance(value, (int, float)):
        return value + 10
    return "Not a number"

def validate_input(data):
    if isinstance(data, str):
        return f"String: {data}"
    elif isinstance(data, int):
        return f"Integer: {data}"
    elif isinstance(data, list):
        return f"List with {len(data)} items"
    else:
        return "Unknown type"
```

## File Operations

**Resources:**
- [Python docs: Reading and Writing Files](https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files)
- [Real Python Working with Files](https://realpython.com/working-with-files-in-python/)
```python
# Reading files
with open("file.txt", "r") as f:
    content = f.read()
    lines = f.readlines()

# Writing files
with open("file.txt", "w") as f:
    f.write("Hello World")
```

