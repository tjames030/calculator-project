# calculator-project
from fractions import Fraction

def get_number(prompt):
  """Gets a number from the user as input. Ensures it's a valid number (float or string representing a fraction)."""
  while True:
    try:
      number = Fraction(input(prompt))  # Attempt to convert input to Fraction
      return number
    except ValueError:
      try:
        number = float(input(prompt))  # If not a fraction, try as float
        return number
      except ValueError:
        print("Invalid input. Please enter a number or a fraction (e.g., 1/2).")

def main():
  """Main function for the calculator program. Runs in a loop until user exits."""
  print("Welcome to the Simple Calculator!")

  while True:
    # Get operation choice
    print("\nSelect operation:")
    print("1. Add")
    print("2. Subtract")
    print("3. Multiply")
    print("4. Divide")
    print("5. Exit")
    operation_choice = input("Enter choice (1/2/3/4/5): ")

    if operation_choice in ('1', '2', '3', '4'):
      # Get two numbers
      first_number = get_number("Enter first number: ")
      second_number = get_number("Enter second number: ")

      # Perform calculation based on choice
      if operation_choice == '1':
        result = first_number + second_number
      elif operation_choice == '2':
        result = first_number - second_number
      elif operation_choice == '3':
        result = first_number * second_number
      else:
        if second_number.denominator == 0:  # Check for division by zero
          print("Error: Division by zero is not allowed.")
        else:
          result = first_number / second_number

      # Display result in decimal form (even if it's a fraction)
      result = float(result)  # Convert the result to a float
      print(f"The result is: {result}")

    elif operation_choice == '5':
      print("Exiting calculator. Thank you for using!")
      break  # Exit the loop to terminate the program
    else:
      print("Invalid choice. Please enter 1, 2, 3, 4, or 5.")

if __name__ == "__main__":
  main()
