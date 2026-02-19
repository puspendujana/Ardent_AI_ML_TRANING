🧮 Python Calculator
A simple, menu-driven command-line calculator built with Python. It supports basic arithmetic operations as well as statistical calculations — all through user input with built-in type casting and error handling.

📋 Features
CategoryOperationsBasic ArithmeticAddition +, Subtraction -, Multiplication *, Division /, Modulo %StatisticsMean, Median, Mode, Average

🚀 How to Run
Requirements: Python 3.8+, no external libraries needed.
bashpython3 calculator.py

🗂️ How It Works
When you run the script, you'll see a simple menu:
========================================
     🧮  Python Calculator
========================================

  MENU
  ─────────────────────────────────
  1 → Basic Arithmetic  (+, -, *, /, %)
  2 → Statistics  (mean, median, mode)
  0 → Exit
  ─────────────────────────────────
Option 1 — Basic Arithmetic
Enter two numbers and choose an operator. The result is displayed instantly.

Division and modulo by zero are safely handled with an error message.
All inputs are cast from str → float automatically.

Option 2 — Statistics
Enter a comma-separated list of numbers (e.g. 3, 5, 7, 5, 9) and choose:

Mean — sum divided by count
Median — middle value when sorted
Mode — most frequently occurring value(s)
Average — same as mean
All of the above — runs all four at once

Multiple modes are supported (e.g. if two values tie, both are shown).

🏗️ Code Structure
calculator.py
│
├── get_number()        → Prompts user, casts input to float, loops on bad input
├── get_number_list()   → Accepts comma-separated numbers, returns list of floats
├── basic_calculator()  → Handles +, -, *, /, % using a lambda dispatch table
├── stats_calculator()  → Handles mean, median, mode using Python's statistics module
└── main()              → Menu loop, routes user to the right function

🧠 Python Concepts Used

input() for user input
float() type casting (str → float)
try / except ValueError for input validation
lambda functions for arithmetic operations
Python built-in statistics module (mean, median, mode, multimode)
List comprehensions
f-strings for formatted output


📌 Example Session
  Your choice: 1

  Enter first number : 10
  Operations: +  -  *  /  %
  Choose operation  : %
  Enter second number: 3

  ✅ 10.0 % 3.0 = 1

---

  Your choice: 2

  Choose option (1-5): 5
  Enter numbers separated by commas: 4, 8, 6, 8, 2

  📊 Mean / Average  : 5.6000
  📊 Median          : 6.0000
  📊 Mode(s)         : 8

📄 License
This project is open source and free to use.
