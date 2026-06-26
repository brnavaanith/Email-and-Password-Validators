# Email-and-Password-Validators

import csv


def write():
    """Function to store new email-password pairs."""
    with open("email.csv", "a+", newline="") as e:
        writer = csv.writer(e, delimiter=",")

        n = int(input("Enter number of entries: "))

        for i in range(n):
            email = input("Enter email ID: ")
            pswd = input("Enter password for the email: ")
            writer.writerow([email, pswd])

        print("Successfully added!")
        print("--------------------------------------")


def read():
    """Function to validate entered email and password."""
    with open("email.csv", "r", newline="") as e:
        reader = csv.reader(e, delimiter=",")

        email = input("Enter email to check: ")
        pswd = input("Enter password to check: ")

        flag = False

        for row in reader:
            if len(row) >= 2 and row[0] == email and row[1] == pswd:
                flag = True
                break

        if flag:
            print("Email and password are validated.")
        else:
            print("You have entered either a wrong email or password.")

        print("--------------------------------------")


def main():
    """Main menu-driven function."""
    while True:
        print("===== EMAIL & PASSWORD VALIDATOR =====")
        print("1. Add new email and password")
        print("2. Check existing email and password")
        print("3. Exit")
        print("--------------------------------------")

        try:
            ch = int(input("Enter your choice (1/2/3): "))

            if ch == 1:
                write()

            elif ch == 2:
                read()

            elif ch == 3:
                print("Exiting program... Goodbye!")
                break

            else:
                print("Invalid choice. Please enter 1, 2, or 3.\n")

        except ValueError:
            print("Please enter a valid number (1, 2, or 3).\n")


main()
