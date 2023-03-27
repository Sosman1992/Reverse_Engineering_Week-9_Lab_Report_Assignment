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
After downloading the file from the website, I extracted the downloaded zip file `controlflow1-1` to my Desktop and it provided with a file named `controlflow1`. I then proceeded to Ghidra to see how best I can decompile and analyze this executable file since running string and uftrace on the file was not providing me enough information. First and foremost after launching Ghidra, from the `Symbol Tree` pane I searched for the actual main function which is basically the entry point of the program and double click it to launch. Ghidra launched the program and provide me with C-code like program in its decompiler pane and in this code I found the `main` function and noticed a function call named rock(). Upon double clicking the rock() function it popped up a new window with a C-code within which I also noticed a fuction call named paper(). Clicking on the paper function opened its function and definition and I also noticed a function call within it named scissors(). I further went on to click it and also noticed anothert function called named lizard(). I clicked on the lizard function and it also contains a function named spock(). On clicking the spock() function it opened its function definiton and it also contains another function called win.

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
After downloading the file from the website, I extracted the downloaded zip file `controlflow2-1` to my Desktop and it provided with a file named `controlflow2`. I then proceeded to Ghidra to see how best I can decompile and analyze this executable file since running string and uftrace on the file was not providing me enough information. First and foremost after launching Ghidra, from the `Symbol Tree` pane I searched for the actual main function which is basically the entry point of the program and double click it to launch. Ghidra launched the program and provide me with C-code like program in its decompiler pane and in this code I found the `main` function and noticed a function call named rock(). Upon double clicking the rock() function it popped up a new window with a C-code within which I also noticed a fuction call named paper(). Clicking on the paper function opened its function and definition and I also noticed a function call within it named scissors(). I further went on to click it and also noticed anothert function called named lizard(). I clicked on the lizard function and it also contains a function named spock(). On clicking the spock() function it opened its function definiton and it also contains another function called win.

The `win()` function takes no arguments and does not return anything. The main purpose of this function is to print two messages using the "puts" function and then exit the program using the "exit" function which causes the program to terminate immediately.

Also, the `spock()` function takes a single argument of type long and does not return anything. The function uses a switch statement to check the value of a byte located at the address param_1 + 0xb. If the byte is equal to 0x2a, the "win" function is called. If the byte is one of the values 0x43, 0x4b, 0x4f, 0x50, or 0x53, the message "!!!" is printed using the "printf" function and then the "lizard" function is called with a specific argument. If the byte is any other value, the "lizard" function is called with the argument "param_1", and then the message "Error: Password was taken out of context." is printed using the "puts" function. Finally, the function calls the "exit" function with the value 6 as an argument. This causes the program to terminate with an error code of 6. 

Moreover, the `lizard()` also takes a single argument of type long and does not return anything. The function then uses a switch statement on the value of the byte at the address param_1 + 0xd or the 14th character. If the byte is equal to 0x36, the "spock" function is called with the argument "param_1". If the byte is one of the values 0x39, 0x41, 0x44, 0x52, or 0x54, the message "Cupcakes!!!" is printed using the "puts" function, and then the "rock" function is called with a specific argument. If the byte is any other value, the "lizard" function is called with the argument "param_1", and then the message "Error: Password was too arrogant." is printed using the "puts" function.

scissors If the user input does not match any of the above, it passes the input to the function scissors(), which checks the first character of the input and decides which function to call next. Depending on the character, scissors() may call the functions rock(), lizard(), or exit with an error message.
The function lizard() checks the second character of the input and may call the function spock() if the character is '6', or exit with an error message otherwise. The function spock() checks the 16th character of the input and may call the function win() if the character is '*', or call the function lizard() or exit with an error message otherwise.

The `paper()` function appears to be performing some sort of check on the eighth byte of param_1 and branching based on the bit values.


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

