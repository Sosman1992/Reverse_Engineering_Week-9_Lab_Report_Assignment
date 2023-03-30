# Binary Reverse Engineering with Crackmes

The Weeks Lab focus was on Binary Reverse Engineering with crackmes which involves running the crackmes with tools including but not limited to (strings, uftrace) at the terminal, Ghidra- a reverse engineering tool that was developed by the NSA for debugging crackmes etc. to enable in finding of essential information from the crackme basically a PASSWORD.

---
# SOLUTION TO Lab 9-1 [easy_crackme_1] crackme AND EXPLANATION OF HOW I SOLVE IT USING THE TOOLS (strings,uftrace,ghidra) 
## STEPS
After downloading the file from the website, I extracted the downloaded zip file `ezcrackme1` to my Desktop and it provided with a file named `easy_crackme_1`. I proceeded by running the file `easy_crackme_1` in my linux terminal using `file command` to ascertain the type of file; from the output it showed that `easy_crackme_1` is 64-Bit Executable Linux file with a BuildID[sha1]=e098404e1e1cee54cad0e7ad48d2850490b71da7. From the terminal I runned the command `uftrace -a ./easy_crackme_1` to enable me gain more valuable insights into its behavior and performance, which can help me identify the password of this crackme. I then went on to run `strings` command on this executable to see the printable strings contained within this binary and I found out some interesting  strings including but not limited: `picklecucumberl337`, `Please insert the password:`,`First Password: `,`Your password <%s> was incorrect. Time for some more RE...`,`You cracked me! Now make a keygen!`. With these strings, I guessed the string `picklecucumberl337` might be the password for this crackme. I rerun the command `uftrace -a ./easy_crackme_1` on my terminal and when it executed it printed the string 'please insert the password:' and upon typying the string `picklecucumberl337` it outputs the success message `You cracked me! Now make a keygen!`, hence the password was correctly entered.
 
## ANSWER
In conclusion `picklecucumberl337` is the password for `easy_crackme_1`, because it is the string that will make the logic statement `strcmp(" ", "picklecucumberl337")` true whenever the strcmp function is called to make comparison of the string entered by the user when prompted to enter the password  within the main function of the program. 


# SOLUTION TO Lab 9-2 [easy_crackme_2] crackme AND EXPLANATION OF HOW I SOLVE IT USING THE TOOLS (strings,uftrace,ghidra) 
## STEPS
After downloading the file from the website, I extracted the downloaded zip file `ezcrackme2` to my Desktop and it provided with a file named `easy_crackme_2`. I proceeded by running the file `easy_crackme_2` in my linux terminal using `file command` to ascertain the type of file; from the output it showed that `easy_crackme_2` is 64-Bit Executable Linux file with a BuildID[sha1]=4ad617747df6c308470f3aa36589cad35e02d5f3. From the terminal I runned the command `uftrace -a ./easy_crackme_2` to enable me gain more valuable insights into its behavior and performance, which can help me identify the password of this crackme. I then went on to run `strings` command on this executable to see the printable strings contained within this binary and I found out some interesting  strings including but not limited: `artificialtree`, `Please insert the password:`,`First Password: `,`Your password <%s> was incorrect. Time for some more RE...`,`You cracked me! Now make a keygen!`. With these strings, I guessed the string `artificialtree` might be the password for this crackme. I rerun the command `uftrace -a ./easy_crackme_2` on my terminal and when it executed it printed the string 'please insert the password:' and upon typying the string `artificialtree` it outputs the success message `You cracked me! Now make a keygen!`, hence the password was correctly entered.
 
## ANSWER
In conclusion `artificialtree` is the password for `easy_crackme_2`, because it is the string that will make the logic statement `strcmp("", "artificialtree")` true whenever the strcmp function is called to make comparison of the strings entered by the user within the main function of the program.



# SOLUTION TO Lab 9-3 [easy_crackme_3] crackme AND EXPLANATION OF HOW I SOLVE IT USING THE TOOLS (strings,uftrace,ghidra) 
## STEPS
After downloading the file from the website, I extracted the downloaded zip file `ezcrackme3` to my Desktop and it provided with a file named `easy_crackme_3`. I proceeded by running the file `easy_crackme_3` in my linux terminal using `file command` to ascertain the type of file; from the output it showed that `easy_crackme_1` is 64-Bit Executable Linux file with a BuildID[sha1]=1c3d5fd32bfc3026c67c6fa59315e872b61e6d8b. From the terminal I runned the command `uftrace -a ./easy_crackme_3` to enable me gain more valuable insights into its behavior and performance, which can help me identify the password of this crackme. I then went on to run `strings` command on this executable to see the printable strings contained within this binary and I found out some interesting  strings including but not limited: `strawberry`,`kiwi`,`Please insert the password:`,`Password:`,`You cracked me!`,`Your password <%s> was incorrect. Time for some more RE...`,`Now make a keygen!.` With these strings, I guessed the string `strawberry` or `kiwi` might be the password for this crackme. I rerun the command `uftrace -a ./easy_crackme_3` on my terminal and when it executed it printed the string 'please insert the password:' and upon typing the string `strawberry` it outputs the unsuccessful message `Your password <strawberry> was incorrect. Time for some more RE...`, hence the password for this crackme was not strawberry as I assumed. Furthermore, I also assumed the password for this crackme might be `kiwi`, hence went on to rerun `uftrace -a ./easy_crackme_3` again and supplied the password kiwi when prompted to insert the password and upon typing the string `kiwi` it outputs the unsuccessful message `Your password <kiwi> was incorrect. Time for some more RE...`, therefore the password for this crackme was also not kiwi as I assumed. 

I then proceeded to Ghidra to see how best I can decompile and analyze this executable file since running string and uftrace on the file was not providing me the password. First and foremost after launching Ghidra, from the `Symbol Tree` pane I searched for the actual main function which is basically the entry point of the program and double click it to launch. Ghidra launched the program and provide me with C-code like program in the decompiler pane of Ghidra consisting of a main function that takes no arguments and returns a boolean value. The purpose of the program was to ask the user for a password,then compare it to two hardcoded strings ("strawberry" and "kiwi" concatenated together), and print a message indicating whether the password was correct or not. The program then prints the message "Please insert the password:" using the "puts" function. It then calls the "getinput" function, passing it the strings "Password: ", a pointer to the "local_48" variable, and a pointer to the "local_40" variable. So I assumed the password to be `strawberrykiwi`, I rerun the command `uftrace -a ./easy_crackme_2` again on my terminal and when it executed it printed the string 'please insert the password:' and upon typying the string `strawberrykiwi` it outputs the success message `You cracked me! Now make a keygen!`, hence the password for t this crackme.

 
## ANSWER
In conclusion `strawberrykiwi` is the password for `easy_crackme_3`, because it is the string that will make the logic statement `strcmp(" ", "strawberrykiwi")` with the hardcoded string "strawberry" and "kiwi" true whenever the strcmp function is called to make comparison of the string entered by the user when prompted to enter the password  within the main function of the program.


# SOLUTION TO Lab 9-4 [controlflow1-1] crackme AND EXPLANATION OF HOW I SOLVE IT USING THE TOOLS (strings,uftrace,ghidra) 
## STEPS
After downloading the file from the website, I extracted the downloaded zip file `controlflow1-1` to my Desktop and it provided with a file named `control_flow_1`. I then proceeded to Ghidra to see how best I can decompile and analyze this executable file since running string and uftrace on the file was not providing me enough information. First and foremost after launching Ghidra, from the `Symbol Tree` pane I searched for the actual main function which is basically the entry point of the program and double click it to launch. Ghidra launched the program and provide me with C-code like program in its decompiler pane and in this code I found the `main` function and noticed a function call named rock(). Upon double clicking the rock() function it popped up a new window with a C-code within which I also noticed a fuction call named paper(). Clicking on the paper function opened its function and definition and I also noticed a function call within it named scissors(). I further went on to click it and also noticed anothert function called named lizard(). I clicked on the lizard function and it also contains a function named spock(). On clicking the spock() function it opened its function definiton and it also contains another function called win.

The `win()` function takes no arguments and does not return anything. The main purpose of this function is to print two messages using the "puts" function and then exit the program using the "exit" function which causes the program to terminate immediately.

Also, the `spock()` function takes a single argument of type long and does not return anything. The function uses a switch statement to perform different actions based on the value of a byte located at offset 0xF from the memory location pointed to by the argument "param_1". If the byte is equal to 0x2a, the "win" function is called. If the byte is one of the values 0x43, 0x4b, 0x4f, 0x50, or 0x53, the message "!!!" is printed using the "printf" function and then the "lizard" function is called with a specific argument. If the byte is any other value, the "lizard" function is called with the argument "param_1", and then the message "Error: Password was taken out of context." is printed using the "puts" function. Finally, the function calls the "exit" function with the value 6 as an argument. This causes the program to terminate with an error code of 6. 

Moreover, the `lizard()` also takes a single argument of type long and does not return anything. 
The function then uses a switch statement to perform different actions based on the value of a byte located at offset 1 from the memory location pointed to by the argument "param_1". If the byte is equal to 0x36, the "spock" function is called with the argument "param_1". If the byte is one of the values 0x39, 0x41, 0x44, 0x52, or 0x54, the message "Cupcakes!!!" is printed using the "puts" function, and then the "rock" function is called with a specific argument. If the byte is any other value, the "lizard" function is called with the argument "param_1", and then the message "Error: Password was too arrogant." is printed using the "puts" function.

The function `scissors()` takes a single argument, which checks the first character of the input and decides which function to call next. Depending on the character, scissors() may call the functions rock(), lizard(), or exit with an error message. The function lizard() checks the second character of the input and may call the function spock() if the character is '6', or exit with an error message otherwise. The function spock() checks the 16th character of the input and may call the function win() if the character is '*', or call the function lizard() or exit with an error message otherwise.

The `paper()` function also to be performing some sort of check on the eighth byte of param_1/input.


**My solution is shown below:**
<pre><code>
#!/usr/bin/env python3
import string
import random
"""Defining the rules on which for a keygen is to be generated"""
RULES = {
    0: "A",
    1: "6",
    3: "2",
    7: "%",
    15: "*"
}

"""Generating the keygen based on the rules"""
def generate_keygen():
    keygen = ["0"] * 16  
    for position, character in RULES.items():
        keygen[position] = character
        
"""Now replacing the remaining characters prefilled with zeros with random uppercase letters and digits"""
    for i in range(len(keygen)):
        if keygen[i] == "0":
            keygen[i] = random.choice("ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789")
    return "".join(keygen)

print(generate_keygen())

</pre></code>

## ANSWER
This is the keygen A6921AQ%77FI507*

![Screenshot from 2023-03-26 12-48-09](https://user-images.githubusercontent.com/66968869/227797890-90b90eb9-3e58-48eb-8ef0-6ed313f71e8b.png)




# SOLUTION TO Lab 9-5 [controlflow2-1] crackme AND EXPLANATION OF HOW I SOLVE IT USING THE TOOLS (strings,uftrace,ghidra) 
## STEPS
After downloading the file from the website, I extracted the downloaded zip file `controlflow2-1` to my Desktop and it provided with a file named `control_flow_2`. I then proceeded to Ghidra to see how best I can decompile and analyze this executable file since running string and uftrace on the file was not providing me enough information. First and foremost after launching Ghidra, from the `Symbol Tree` pane I searched for the actual main function which is basically the entry point of the program and double click it to launch. Ghidra launched the program and provide me with C-code like program in its decompiler pane and in this code I found the `main` function and noticed a function call named rock(). Upon double clicking the rock() function it popped up a new window with a C-code within which I also noticed a fuction call named paper(). Clicking on the paper function opened its function and definition and I also noticed a function call within it named scissors(). I further went on to click it and also noticed anothert function called named lizard(). I clicked on the lizard function and it also contains a function named spock(). On clicking the spock() function it opened its function definiton and it also contains another function called win.

The `win()` function takes no arguments and does not return anything. The main purpose of this function is to print two messages using the "puts" function and then exit the program using the "exit" function which causes the program to terminate immediately.

Also, the `spock()` function takes a single argument of type long and does not return anything. The function uses a switch statement to check the value of a byte located at the address param_1 + 0xb. If the byte is equal to 0x2a, the "win" function is called. If the byte is one of the values 0x43, 0x4b, 0x4f, 0x50, or 0x53, the message "!!!" is printed using the "printf" function and then the "lizard" function is called with a specific argument. If the byte is any other value, the "lizard" function is called with the argument "param_1", and then the message "Error: Password was taken out of context." is printed using the "puts" function. Finally, the function calls the "exit" function with the value 6 as an argument. This causes the program to terminate with an error code of 6. 

Moreover, the `lizard()` also takes a single argument of type long and does not return anything. The function then uses a switch statement on the value of the byte at the address param_1 + 0xd or the 14th character. If the byte is equal to 0x36, the "spock" function is called with the argument "param_1". If the byte is one of the values 0x39, 0x41, 0x44, 0x52, or 0x54, the message "Cupcakes!!!" is printed using the "puts" function, and then the "rock" function is called with a specific argument. If the byte is any other value, the "lizard" function is called with the argument "param_1", and then the message "Error: Password was too arrogant." is printed using the "puts" function.

The function `scissors()` takes in a long parameter param_1 and and also uses a switch statement to make a decision by making checks if the byte is 0x41 or the character at the 11th position is 'A', it calls the lizard function with param_1 as argument. However, If the byte is 0x25 or 0x2a, it recursively calls itself with param_1 as argument. i.e: Depending on the character present, scissors() may call the functions rock(), lizard(), or exit with an error message. It also checks, If the byte is 0x3c, 0x3e, 0x3f, 0x40, or 0x51, it prints "!!!" and calls the rock function. However, If none of the cases match, it prints an error message and exits with a code of 5. 

The `paper()` function  has two variables namely uvar1 and uvar2 and the function appears to be performing some sort of check on the on the 9th character of the input string to be entered the user who would be playing the game. The uVar1 variable is calculated by subtracting the integer value 0x23 from the integer value stored in the memory address param_1 + 8 which provides the value `#` to be the 9th character. 

The `rock()` function that takes a long parameter param_1 and performs some conditional logic based on the value of the character at memory location (param_1 + 6) or the character at the 7th position and in turn calls either paper(param_1), scissors whose memory location is (&DAT_00102081) or recursively calls rock(param_1) with a printed exclamation point "!!!" for certain conditions.

The `main()` function is the entry point of the program (where program execution commences). It requires that a single command-line argument (the password) to be supplied when it is executed at the terminal and performs a series of operations based on the characters in the password. If the password does not meet certain criteria, the program will exit with an error code. The program starts by checking if there is exactly one command-line argument. If there is not, it prints a usage message and exits with error code 1. However, if there is one command-line argument, the program checks if its length is at least 0x10 (16 in decimal). If it is not, it prints an error message and exits with error code 2. Also, if the password is at least 16 characters long, the program passes it to the rock() function, which performs a series of operations based on the characters in the password. If the password is not valid according to the program's rules, the program will exit with an error code. If the password is valid, the program will print an error message and exit with error code 3.

**My solution is shown below:**
<pre><code>
#!/usr/bin/env python3
import string
import random
"""Defining the rules on which for a keygen is to be generated"""
RULES = {
    0: "A",
    3: "3",
    6: "Y",
    8: "#",
    10: "A",
    11: "*",
    13: "6"
}

"""Generating the keygen based on the rules"""
def generate_keygen():
    keygen = ["0"] * 16  
    for position, character in RULES.items():
        keygen[position] = character
        
"""Now replacing the remaining characters prefilled with zeros with random uppercase letters and digits"""
    for i in range(len(keygen)):
        if keygen[i] == "0":
            keygen[i] = random.choice("ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789")
    return "".join(keygen)

print(generate_keygen())

</pre></code>

## ANSWER
This is the keygen ANF3J4Y7#DA*R6FV

![9_5](https://user-images.githubusercontent.com/66968869/227815821-69dc2ab3-c74b-4ef0-b5b4-3a303da60ee8.png)



# SOLUTION TO Lab 9-6 [controlflow3] crackme AND EXPLANATION OF HOW I SOLVE IT USING THE TOOLS (strings,uftrace,ghidra) 
## STEPS
After downloading the file from the website, I extracted the downloaded zip file `controlflow3` to my Desktop and it provided with a file named `control_flow_3`. I then proceeded to Ghidra to see how best I can decompile and analyze this executable file since running string and uftrace on the file was not providing me enough information. First and foremost after launching Ghidra, from the `Symbol Tree` pane I searched for the actual main function which is basically the entry point of the program and double click it to launch. Ghidra launched the program and provide me with C-code like program in its decompiler pane and in this code I found the `main` function and noticed a function call named rock(). Upon double clicking the rock() function it popped up a new window with a C-code within which I also noticed a fuction call named paper(). Clicking on the paper function opened its function and definition and I also noticed a function call within it named scissors(). I further went on to click it and also noticed anothert function called named lizard(). I clicked on the lizard function and it also contains a function named spock(). On clicking the spock() function it opened its function definiton and it also contains another function called win.

The `win()` function takes no arguments and does not return anything. The main purpose of this function is to print two messages using the "puts" function and then exit the program using the "exit" function which causes the program to terminate immediately.

Also, the `spock()` function checks whether a certain condition holds true for the input password i.e the 8th and 9th character being equal, if they equal it call a function named `die()` which is used to print error messages and terminate the program with an appropriate exit status. Else if the exclusive OR operation of the 13th , 9th and 10th character is not equal the value of the 11th character being less than 3 the win() function is called which prints the success message to the user. i.e either of these conditions needs to be false for the program to be able to proceed to call the win() function.

Moreover, the `lizard()` also takes a single argument of type long and does not return anything. The third line uses bitwise XOR operation to obtain a byte value and compares it to a decimal value of 4. If the byte value (The 9th character XOR the 8th character) is less than the value 4, the function calls the `die()` function with the message "Password was too spicy". The `die()` function is used to print error messages and terminate the program with an appropriate exit status . The function returns without any value.

The function `scissors()` takes a single argument, The third line checks if the byte value at the memory location (param_1 + 10) or the 11th character is equal to the byte value at the memory location (param_1 + 0xc) or the 13th character. If they are equal, the function calls another function called "lizard" with the same parameter. However they are different, the `die()` function with the message "Password was too spicy" is invoked which is used in printing error messages and terminating the program with an appropriate exit status.

The `paper()` function also takes a single argument, The third line uses bitwise XOR operation to obtain a byte value and compares it to a decimal value of 3 i.e (The exclusive of XOR of the 7th and 8th character being less than 3). If the byte value is less than 3, the function invokes another function called "scissors" with the same parameter. If the byte value is not less than 3, the function calls the `die()` function with the message "Password was too sweet", which is used in printing error messages and terminating the program with an successful exit status.

Also the `rock()` function takes a single argument of type long, The third line calculates the sum of the byte values at memory locations (param_1 + 1) and (param_1 + 3), then subtracts the byte value at memory location (param_1 + 5) from the sum. If the result is equal to the byte value at memory location (param_1 + 6), the function calls another function called "paper" with the same parameter.Nonetheless, if the result is not equal to the byte value at memory location (param_1 + 6), the function calls the "die()" function with the message "Password is too ostentatious."

Lastly, the `main()` function is the entry point of the program (where program execution commences). It requires that a single command-line argument (the password) to be supplied when it is executed at the terminal and performs a series of operations based on the characters in the password. If the password does not meet certain criteria, the program will exit with an error code. The program starts by checking if there is exactly one command-line argument. If there is not, it prints a usage message and exits with error code 1. However, if there is one command-line argument, the program checks if its length is at least 0x10 (16 in decimal). If it is not, it prints an error message and exits with error code 2. Also, if the password is at least 16 characters long, the program passes it to the rock() function, which performs a series of operations based on the characters in the password. If the password is not valid according to the program's rules, the program will exit with an error code. If the password is valid, the program will print an error message and exit with error code 3. In summary, the program checks if it is provided with two arguments, a password, and then validates the password length and passes it to the `rock()` function for further validation. If any errors occur, the program terminates with an appropriate exit code and message.


**My solution is shown below:**
<pre><code>
import random

while True:
    password = ''.join(random.choices('abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789', k=13))
    xor_value1 = ord(password[12]) ^ ord(password[8]) ^ ord(password[9])
    xor_value2 = ord(password[8]) ^ ord(password[7])
    xor_value3 = ord(password[6]) ^ ord(password[7])
    sum_value = ord(password[1]) + ord(password[3]) + ord(password[5]) - ord(password[5])
    if xor_value1 != ord(password[10]) and ord(password[10]) < 51 and xor_value2 < 4 and password[10] == password[12] and xor_value3 < 3 and sum_value == ord(password[6]):
        break

print(f"Generated password: {password}")

</pre></code>

## ANSWER
This is the keygen 




