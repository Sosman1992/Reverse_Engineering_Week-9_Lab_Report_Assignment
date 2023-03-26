# Binary Reverse Engineering with Crackmes

The Weeks Lab focus was on Binary Reverse Engineering with crackmes which involves running the crackmes with tools including but not limited to (strings, uftrace) at the terminal, Ghidra- a reverse engineering tool that was developed by the NSA for debugging crackmes etc. to enable in finding of essential information from the crackme basically a PASSWORD.

---
# SOLUTION TO Lab 9-1 [easy_crackme_1] crackme AND EXPLANATION OF HOW I SOLVE IT USING THE TOOLS (strings,uftrace,ghidra) 
## STEPS
After downloading the file from the website, I extracted the downloaded zip file `ezcrackme1` to my Desktop and it provided with a file named `easy_crackme_1`. I proceeded by running the file `easy_crackme_1` in my linux terminal using `file command` to ascertain the type of file; from the output it showed that `easy_crackme_1` is 64-Bit Executable Linux file with a BuildID[sha1]=e098404e1e1cee54cad0e7ad48d2850490b71da7. I then went on to run `strings` command on this executable to see the printable strings contained within this binary and I found out some interesting  strings including but not limited: `picklecucumberl337`, `Please insert the password:`,`First Password: `,`Your password <%s> was incorrect. Time for some more RE...`,`You cracked me! Now make a keygen!`.
 



