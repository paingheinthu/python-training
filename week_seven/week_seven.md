# Using AI to Debug & Code Generate — Claude & ChatGPT

## Table of Contents
1. What is AI in Coding?
2. When to Use AI for Coding
3. How to Write Good Prompts
4. Using ChatGPT for Code Generation
5. Using Claude for Code Generation
6. Using AI to Debug Code
7. Verifying AI-Generated Code
8. Limitations of AI
9. Best Practices
10. Hands-on Examples

---

## 1. What is AI in Coding?

AI tools like **ChatGPT** and **Claude** can:
- Generate code based on descriptions
- Explain code logic
- Debug and fix errors
- Suggest optimizations
- Answer programming questions

**Important:** AI is a helper, not a replacement for learning. Always understand the code before using it.

---

## 2. When to Use AI for Coding

### ✅ Good uses:
- Boilerplate code (repetitive patterns)
- Algorithm explanations
- Debugging help
- Code review feedback
- Documentation
- Refactoring suggestions
- Learning concepts

### ❌ Bad uses:
- Generating code without understanding it
- Trusting AI output without verification
- Using AI as primary learning method
- Not testing AI-generated code

---

## 3. How to Write Good Prompts

### Key Elements of a Good Prompt:

1. **Be Specific**
```
Bad: "Make a Python program"
Good: "Create a Python function that calculates the factorial of a number using recursion"
```

2. **Provide Context**
```
Bad: "Fix my code"
Good: "I'm trying to read a CSV file and group by column name. Here's my code: [code]. It gives error: [error message]"
```

3. **Mention Requirements**
```
Bad: "Make a login system"
Good: "Create a Python login system that validates email format and requires password length >= 8 characters"
```

4. **Specify Output Format**
```
Bad: "Explain functions"
Good: "Explain what a Python function is in 3-5 sentences with one example"
```

---

### Prompt Structure

```
[TASK] + [CONTEXT] + [REQUIREMENTS] + [FORMAT]

Example:
"Write a Python function that [TASK: removes duplicates from a list].
The function should [CONTEXT: work with both numbers and strings].
Requirements: [must preserve order, use built-in functions only].
Output: [just the code with comments]"
```

---

## 4. Using ChatGPT for Code Generation

### Example 1: Simple Function

**Prompt:**
```
Write a Python function that takes a list of numbers
and returns only the even numbers
```

**Typical Response:**
```python
def get_even_numbers(numbers):
    return [num for num in numbers if num % 2 == 0]
```

---

### Example 2: Class Generation

**Prompt:**
```
Create a Python class called BankAccount that:
- Has methods deposit() and withdraw()
- Prevents negative balance
- Returns current balance
```

**Typical Response:**
```python
class BankAccount:
    def __init__(self, balance=0):
        self.balance = balance

    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            return f"Deposited ${amount}"
        return "Invalid amount"

    def withdraw(self, amount):
        if amount > 0 and amount <= self.balance:
            self.balance -= amount
            return f"Withdrew ${amount}"
        return "Invalid withdrawal"

    def get_balance(self):
        return self.balance
```

---

## 5. Using Claude for Code Generation

### Example 1: Detailed Explanation

**Prompt:**
```
I'm learning list comprehensions in Python.
Can you show me how to create a list of squares from 1 to 10
and explain each part?
```

**Claude typically provides:**
- Clear explanation
- Multiple approaches
- Step-by-step breakdown
- Why certain methods are better

---

### Example 2: Error Fixing

**Prompt:**
```
I'm getting a TypeError in this code:

```python
def add_numbers(a, b):
    return a + b

result = add_numbers("5", 3)
print(result)
```

Error: unsupported operand type(s) for +: 'str' and 'int'

How do I fix this?
```

**Claude Response:**
Explains the error and provides solutions with explanations.

---

## 6. Using AI to Debug Code

### Step 1: Provide the Error
```
Prompt:
"I have this code:
[your code]

And I get this error:
[error message]

What's wrong?"
```

---

### Step 2: Ask for Explanation
```
Prompt:
"Can you explain why this error occurs and
provide a fixed version with comments?"
```

---

### Step 3: Test the Fix
Always test the provided solution before using it.

---

## 7. Verifying AI-Generated Code

### Checklist:
- [ ] Does it do what you asked?
- [ ] Does it run without errors?
- [ ] Does it handle edge cases?
- [ ] Does it follow best practices?
- [ ] Do you understand how it works?
- [ ] Is it efficient (not over-complicated)?

---

### Testing Strategy

```python
# Test with different inputs
def test_function(func, test_cases):
    for input_data, expected in test_cases:
        result = func(input_data)
        if result == expected:
            print(f"✓ Test passed: {input_data} → {result}")
        else:
            print(f"✗ Test failed: {input_data} → {result} (expected {expected})")

# Example
test_cases = [
    ([1, 2, 3, 4], [2, 4]),
    ([1, 3, 5], []),
    ([], [])
]
test_function(get_even_numbers, test_cases)
```

---

## 8. Limitations of AI

### Common Issues:

1. **AI can make mistakes**
```python
# Bad code generated by AI
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n)  # Missing n-1!
```

2. **AI may not understand your exact requirement**
```
You ask for "efficient code"
AI gives: Most readable code (not fastest)
Or: Most concise code (hard to understand)
```

3. **AI can't see your full context**
```
You ask for a function for your specific project
AI gives: Generic solution that doesn't integrate well
```

4. **AI may generate outdated code**
```
You ask for "read file in Python"
AI might suggest: open() instead of with statement
```

---

## 9. Best Practices

### ✅ DO:
1. **Understand before using**
```
Don't: Copy-paste code without reading
Do: Read and understand each line
```

2. **Test thoroughly**
```
Don't: Assume it works
Do: Test with multiple inputs
```

3. **Read multiple suggestions**
```
Don't: Use the first answer
Do: Ask for alternatives and compare
```

4. **Verify AI responses**
```
Don't: Trust AI as source of truth
Do: Cross-check with documentation
```

5. **Use for learning**
```
Don't: Just get code and move on
Do: Learn why it works and how to improve
```

---

### ❌ DON'T:
1. **Don't plagiarize**
```
Bad: Copy AI code as your own
Good: Use it as reference, understand and adapt
```

2. **Don't use without testing**
```
Bad: Put AI-generated code in production immediately
Good: Test thoroughly first
```

3. **Don't stop learning**
```
Bad: Rely entirely on AI for coding
Good: Use AI to help, but learn fundamentals
```

---

## 10. Hands-on Examples

### Example 1: Generate and Verify

**You want:** A function to check if a string is a palindrome

**Prompt to Claude/ChatGPT:**
```
Write a Python function that checks if a string is a palindrome.
It should ignore spaces and be case-insensitive.
Include test cases.
```

**What you should do:**
1. Read the code
2. Understand the logic
3. Run the provided test cases
4. Test with your own examples
5. Ask questions about any parts you don't understand

---

### Example 2: Debug with AI

**You have a bug in your code:**
```python
def get_unique_items(items):
    unique = []
    for item in items:
        if item not in unique:
            unique.append(item)
    return set(unique)  # Converts to set (loses order!)
```

**Prompt:**
```
This function returns a set instead of a list.
How can I fix it to return a list while keeping it ordered?
```

**Follow up:** Understand why the original code had this issue.

---

### Example 3: Learn with AI

**Prompt:**
```
Explain what a decorator does in Python.
Show a simple example of a decorator that prints
function name before and after it runs.
```

**What to do:**
1. Understand the example
2. Modify it slightly to learn
3. Ask follow-up questions

---

## Real-world Prompt Examples

### Example 1: Read CSV and Filter
```
Write a Python function that:
- Reads a CSV file
- Filters rows where age > 20
- Returns a list of dictionaries
Include error handling for file not found.
```

---

### Example 2: Database Query
```
I'm using MySQL. Write Python code that:
- Connects to database
- Queries employees table
- Groups by department
- Calculates average salary per department
- Handles connection errors
```

---

### Example 3: Debugging
```
I'm trying to read JSON from an API but getting JSONDecodeError.
Here's my code: [code]
Here's the error: [error]

What's wrong and how do I fix it?
```

---

## Tips for Better Results

1. **Be conversational** — Follow up with "Why?" questions
2. **Request alternatives** — "Can you show another way?"
3. **Ask for optimizations** — "How can I make this faster?"
4. **Request explanations** — "Explain this line: [line]"
5. **Test suggestions** — Always run code before trusting it
6. **Learn patterns** — Notice how AI structures code
7. **Provide feedback** — "This is too complex, simplify"

---

## Summary

| Task | Best Approach |
|------|--------|
| Generate boilerplate | Use AI → Customize |
| Learn concept | Ask AI → Understand → Practice |
| Debug error | Paste error → Understand fix → Apply |
| Refactor code | Ask AI for suggestions → Review → Test |
| Write tests | Generate with AI → Review and customize |
| Learn library | Ask AI examples → Read docs → Practice |

---
