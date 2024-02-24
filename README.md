from random import * 
from time import *
while True:

    letters=[] 
    
    # Instead of typing repeatedly in different languages, use this list to copy the characters of the desired language into this list and use it
    eng_letters=['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z']
    tr_letters=['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'ı', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'ö', 'p', 'r', 's', 'ş', 't', 'u', 'ü', 'v', 'y', 'z', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'İ', 'J', 'K', 'L', 'M', 'N', 'O', 'Ö', 'P', 'R', 'S', 'Ş', 'T', 'U', 'Ü', 'V', 'Y', 'Z']
    ger_letters=['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z', 'ä', 'ö', 'ü', 'ß','A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V','W', 'X', 'Y', 'Z', 'Ä', 'Ö', 'Ü', 'ẞ']

    numbers = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9'] 

    symbols = ['!', '#', '$', '%', '&', '(', ')', '*', '+']

    password_list=[] # This empty list is used to hold the characters the user wants.
    
    select=int(input('''**********************************\n1 to start/continue processing
Press 0 to stop/finish.
Process selection: '''))
    if(select==0):
        select2=str(input("you have chosen to stop the transaction, should the transaction be executed? 'yes' or 'no' "))
        if(select2=='yes'):
            break
        else:
            continue
    if select > 1 or select < 0:
        print("Please enter the correct code for selection.")
        continue
    while True:    
        print("In which language do you use the keyboard? ")
        print("1) English\n2) Turkish\n3) German")
        lang_select=int(input("\n--> "))

        if lang_select == 1:
            letters=[i for i in eng_letters]
        elif lang_select == 2:
            letters=[i for i in tr_letters]
        elif lang_select == 3:
            letters=[i for i in ger_letters]
        else:
            print("You have entered an incorrect selection code, please correct it.")
            continue

        # Basit düzeyde random şifre oluşturma 
        nr_letters= int(input("How many characters will be in the password to be created: ")) 
        if(nr_letters > 0):
            for char in range(0, nr_letters): 
                password_list.append(choice(letters))
        elif(nr_letters <= 0):
            print("A password will be created without characters.")
            
        nr_numbers = int(input("How many numeric characters will be in the password to be created: ")) 
        if(nr_numbers > 0):
            for _ in range(0, nr_numbers): 
                password_list.append(choice(numbers)) 
        elif(nr_numbers <= 0):
            print("A password will be created without numeric characters.")

        nr_symbols = int(input("How many symbols will be in the password to be created: ")) 
        if(nr_symbols > 0):
            for _ in range(0, nr_symbols): 
                password_list.append(choice(symbols))
        elif(nr_symbols <= 0):
            print("A password will be generated without a symbol.") 
            
        # Create an empty password variable
        password =""

        # Sort randomly selected characters randomly within the list without returning a new list
        shuffle(password_list) 

        # Listedeki karakterleri oluşturulan password değişkenine ata
        for char in password_list: 
            password += char 

        # Print randomly generated password on screen
        if(nr_symbols == 0 and nr_letters == 0 and nr_numbers == 0):
            print("A minimum number of valid characters must be entered to create a password.")
        else:
            print(f"Your unique password generated: {password}")
        break
