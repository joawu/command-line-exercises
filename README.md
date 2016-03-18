# command-line-exercises

<a href="https://www.learnenough.com/command-line-tutorial">Learn Enough Command Line to be Dangerous Tutorial</a> - Exercise Answers

# Preliminary Stuff

**command + T** new tab

**ctrl - C** gets you out of trouble! *note: ctrl is often written as '^'

**man <command>** provides documentation - press down to advance, q to quit



**ctrl - A** takes you to beginning of line

**ctrl - E** takes you to the end of line

**ctrl - U** clears line

**option-click** takes you to location of clicking

**ctrl - L** or **clear** clears your screen



**ls** lists files

**ls *.txt** lists all txt files

**ls -l** lists in long format

**ls -rtl** lists by reversed time of modification

**ls a*** lists all files that begin with the letter 'a'

**ls *saucy*** lists all files that contain the string 'saucy'



**mv** <old> <new>, move

**cp** <old> <new>, copy

**rm** <file>, removes

**rm -f** <file>, removes WITHOUT confirmation

# 2: Manipulating files
## 2.1: Redirecting and appending

### Exercise 1
Q: Using echo and >, make files called line_1.txt and line_2.txt containing the first and second lines of Sonnet 1, respectively.

A: `echo "From fairest creatures we desire increase," > line_1.txt` , 
   `echo "That thereby beauty's rose might never die," > line_2.txt`

### Exercise 2
Q: Replicate the original sonnet_1.txt (containing the first two lines of the sonnet) by first redirecting the contents of line_1.txt and then appending the contents of line_2.txt. Call the new file sonnet_1_copy.txt, and confirm using diff that it’s identical to sonnet_1.txt.

A: `echo "From fairest creatures we desire increase," > sonnet_1_copy.txt` ,
   `echo "That thereby beauty's rose might never die," >> sonnet_1_copy.txt` , 
   `diff sonnet_1.txt sonnet_1_copy.txt`

### Exercise 3
Q: Use cat to combine the contents of line_1.txt and line_2.txt in reverse order using a single command, yielding the file sonnet_1_reversed.txt.

A: `cat line_2.txt line_1.txt > sonnet_1_reversed.txt`

---
## 2.2: Listing

### Exercise 1
Q: What’s the command to list all the files (and directories) that start with the letter “s”? 

A: `ls s*`

### Exercise 2
Q: What is the command to list all the files that contain the string “onnet”, long-form by reverse modification time?

A: `ls -rtl *onnet*`

### Exercise 3
Q: What is the command to list all files (including hidden ones) by reverse modification time, in long form?

A: `ls -artl`

---
## 2.3: Renaming, copying, deleting

### Exercise 1
Q: Use the echo command and the redirect operator > to make a file called foo.txt containing the text “hello, world”. Then, using the cp command, make a copy of foo.txt called bar.txt. Using the diff command, confirm that the contents of both files are the same.

A: `echo "hello, world" > foo.txt` , `cp foo.txt bar.txt` , `diff foo.txt bar.txt`

### Exercise 2
Q: By combining the cat command and the redirect operator >, create a copy of foo.txt called baz.txt without using the cp command.

A: `cat foo.txt > baz.txt`

### Exercise 3
Q: Create a file called quux.txt containing the contents of foo.txt followed by the contents of bar.txt.

A: `cat foo.txt bar.txt > quux.txt`

### Exercise 4
Q: How do rm nonexistent and rm -f nonexistent differ for a nonexistent file?

A: `rm` nonexistant asks for confirmation, `rm -f` nonexistant does not ask for comfirmation

---
## 2.4: Summary

### Exercise 1
Q: By copying and pasting the text from the HTML version of Figure 15, use echo to make a file called sonnet_1_complete.txt containing the full (original) text of Shakespeare’s first sonnet.

A: `echo "FRom faireſt creatures we deſire increaſe, That thereby beauties Roſe might neuer die, But as the riper ſhould by time deceaſe, His tender heire might beare his memory: But thou contracted to thine owne bright eyes, Feed’ſt thy lights flame with ſelfe ſubſtantiall fewell, Making a famine where aboundance lies, Thy ſelfe thy foe,to thy ſweet ſelfe too cruell: Thou that art now the worlds freſh ornament, And only herauld to the gaudy ſpring, Within thine owne bud burieſt thy content, And tender chorle makſt waſt in niggarding:    Pitty the world,or elſe this glutton be,    To eate the worlds due,by the graue and thee." > sonnet_1_complete.txt` , `cat sonnet_1_complete.txt`

### Exercise 2
Q: Type the sequence of commands needed to create an empty file called foo, rename it to bar, and copy it to baz. 

A: `touch foo`, `mv foo bar`, `cp bar baz`

### Exercise 3
Q: What is the command to list only the files starting with the letter “b”?

A: `ls b*`

### Exercise 4

Q: Remove both bar and baz using a single call to rm.

A: `rm ba*`

---
# 3: Inspecting files

## 3.1: Downloading a file

### Exercise 3
Q: Using the -h (“human-readable”) option to ls, list the long form of the sonnets file with a human-readable byte count. 

A:`ls -lh sonnets.txt`

### Exercise 4
Q: Suppose you wanted to list the files and directories using human-readable byte counts, all, by reverse time-sorted long-form. 

A: `ls -hartl` 

---
## 3.2 Making Heads and Tails of it all

### Exercise 1
Q: By piping the results of tail sonnets.txt through wc, confirm that (like head) the tail command outputs 10 lines by default.

A: `tail sonnets.txt | wc`

### Exercise 2
Q: By running man head, learn how to look at the first n lines of the file. By experimenting with different values of n, find a head command to print out just enough lines to display the first sonnet in its entirety (Figure 12).

A: `head -18 sonnets.txt`

### Exercise 3
Q: Pipe the results of the previous exercise through tail (with the appropriate options) to print out only the 14 lines composing Sonnet 1. 

A: `head -18 sonnets.txt | tail -14`


