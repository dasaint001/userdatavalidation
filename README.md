# import from library
import string
import random

# collection of details from the user


def collect_details():
    first_name = input("Enter your first name: ")
    last_name = input("Enter your last name: ")
    user_email = input("Enter you email address: ")
    details = [first_name, last_name, user_email]
    return details

# Generation of password


def generate_password(details):
    characters = string.ascii_letters
    length = 5
    random_password = ''.join(random.choice(characters) for i in range(length))
    # making first two letters of the first name and last two letters of the user's last name password
    password = str(details[0][0:2] + details[1][-2:] + random_password)
    return password


status = True
# This is the container for the user's details
container = []

users = {}
usernumber = 1

while status:
    details = collect_details()
    password = generate_password(details)
    print("Your password is: " + str(password))
    satisfied_with_password = input(str("satisfied with the generated password? Yes or NO "))

    password_loop = True

    while password_loop:

        if satisfied_with_password == "Yes":
            details.append(password)

            container.append(details)

            users[usernumber] = details
            password_loop = False

        else:
            user_password = input(str("Enter password longer than or equal to 7: "))

            password_length = True

            while password_length:
                # This set the password length
                if len(user_password) >= 7:

                    details.append(user_password)

                    container.append(details)
                    users[usernumber] = details

                    password_length = False

                    password_loop = False

                else:

                    print("Your password is less than 7")

                    user_password = input(str("Enter password longer than or equal to 7"))
# This prompt new user's input.
    new_user = input(str("Would you like to enter a new user? Yes or NO "))

    if new_user == "No":

        status = False
        for item in users:
            print(users.get(item))
    else:

        status = True
        usernumber = usernumber + 1






