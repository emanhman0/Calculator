import art

#Creates arithmetic operator functions
def add(n1, n2):
    return n1 + n2

def subtract(n1, n2):
    return n1 - n2

def multiply(n1, n2):
    return n1 * n2

def divide(n1, n2):
    return n1 / n2

#Creates a dictionary to store the key and values for the operators
operations = {"+": add,
             "-": subtract,
             "*": multiply,
             "/": divide,
}
#Creates a function to call itself again if user wants to use a calculator
def calculator():
    print(art.logo)
    new_calculation = True
    users_first_number = float(input("What's the first number?: "))

    #Creates a while loop to continue calculation
    while new_calculation:
        #Loops through dictionary to display operators
        for symbol in operations:
            print(symbol)
        #Takes users operator to call any of the arithmetic functions.
        users_operator = input("Pick an operation: ")
        users_second_number = float(input("What's the next number?: "))
        #Sets the result to a calculation variable 
        calculation = operations[users_operator](users_first_number, users_second_number)
        print(f"{users_first_number} {users_operator} {users_second_number} = {calculation}")
        #Asks user if they would like to keep calculating or start over. 
        #Based on user input it will assign the calculation as the first number and start the while loop again OR
        #print out lines to essentially "reset" the calculator and start anew.
        decision = input(f"Type 'y' to continue calculating with {calculation}, or type 'n' to start a new calculation: ")

        if decision == "y":
            users_first_number = calculation
        else:
             if decision == "n":
                new_calculation = False
                print("\n" * 100)
                calculator()

calculator()
