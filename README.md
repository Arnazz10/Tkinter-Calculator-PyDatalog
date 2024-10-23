# Tkinter-Calculator-PyDatalog
This project is a simple calculator built with Python's Tkinter library for the user interface. It performs basic arithmetic operations such as addition, subtraction, multiplication, and division. The calculator evaluates the expressions using Python's eval() function, making it user-friendly and interactive.

# CODE :

import tkinter as tk

# Function to update the display when buttons are clicked
def button_click(value):
    current_text = entry.get()
    entry.delete(0, tk.END)  # Clear the display
    entry.insert(0, current_text + str(value))  # Add the clicked button's value

# Function to evaluate the expression
def calculate():
    expression = entry.get()
    try:
        result = eval(expression)  # Evaluate the mathematical expression
        entry.delete(0, tk.END)
        entry.insert(0, str(result))  # Display the result
    except Exception as e:
        entry.delete(0, tk.END)
        entry.insert(0, "Error")

# Function to clear the display
def clear_display():
    entry.delete(0, tk.END)

# Initialize the main window
window = tk.Tk()
window.title("Calculator")

# Entry widget to display the input and results
entry = tk.Entry(window, width=20, font=("Arial", 18), borderwidth=2, relief="solid", justify="right")
entry.grid(row=0, column=0, columnspan=4, padx=10, pady=10)

# Define the buttons and their positions on the grid
buttons = [
    ('7', 1, 0), ('8', 1, 1), ('9', 1, 2), ('/', 1, 3),
    ('4', 2, 0), ('5', 2, 1), ('6', 2, 2), ('*', 2, 3),
    ('1', 3, 0), ('2', 3, 1), ('3', 3, 2), ('-', 3, 3),
    ('0', 4, 0), ('.', 4, 1), ('+', 4, 2), ('=', 4, 3)
]

# Loop to create buttons
for (text, row, col) in buttons:
    button = tk.Button(window, text=text, width=5, height=2, font=("Arial", 14),
                       command=lambda t=text: button_click(t))
    button.grid(row=row, column=col, padx=5, pady=5)

# Additional buttons: clear and equals
clear_button = tk.Button(window, text="C", width=5, height=2, font=("Arial", 14), command=clear_display)
clear_button.grid(row=5, column=0, columnspan=2, padx=5, pady=5)

equal_button = tk.Button(window, text="=", width=5, height=2, font=("Arial", 14), command=calculate)
equal_button.grid(row=5, column=2, columnspan=2, padx=5, pady=5)

# Start the main loop
window.mainloop()



