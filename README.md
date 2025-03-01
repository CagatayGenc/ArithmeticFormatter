```python
def arithmetic_arranger(problems, show_answers=False):

  #Check length of problems
  if len(problems) > 5:
    return 'Error: Too many problems.'

  #Arranging lines
  line1 = ""
  line2 = ""
  line3 = ""
  line4 = ""

  #For final view
  arranged_problems = ""

  #Assigning numbers and operators of problems
  for problem in problems:
      number1, op, number2 = problem.split()
      if not number1.isdigit() or not number2.isdigit():
        return 'Error: Numbers must only contain digits.'

      #Check operator (+ or -)
      if op not in ["+","-"]:
        return "Error: Operator must be '+' or '-'."

      #Check length of numbers
      if len(number1) > 4 or len(number2) > 4:
        return 'Error: Numbers cannot be more than four digits.'

      #Assign width (2 = 1 blank + 1 operator)
      width = max(len(number1) ,len(number2)) + 2

      #Print lines
      line1 += number1.rjust(width) + "    "
      line2 += op + number2.rjust(width - 1) + "    "
      line3 += "-" * width + "    "

      #If answers are to be displayed, prints
      if show_answers:
        if op == "+":
          result = str(int(number1) + int(number2))
        else:
          result = str(int(number1) - int(number2))

        #Print results
        line4 += result.rjust(width) + "    "

  #Final view
  arranged_problems = line1.rstrip() + "\n" + line2.rstrip() + "\n" + line3.rstrip()

  #If answers are to be displayed, operations
  if show_answers:
    arranged_problems += "\n" + line4.rstrip()

  return arranged_problems
```
