# command-line-exercises

[Learn Enough Command Line to be Dangerous Tutorial](https://www.learnenough.com/command-line-tutorial) - Exercise Answers

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

---
## 3.3 Less is More

### Exercise 1
Q: Run less on sonnets.txt. Go down three pages and then back up three pages. Go to the end of the file, then to the beginning, then quit.

A: `less sonnets.txt` advance with `^F` or `spacebar`, go back with `^B`, go to end with `G`, go to beginning with `1G`, quit with `q` 

### Exercise 2
Q: Search for the string “All” (case-sensitive). Go forward a few occurrences, then back a few occurrences. Then go to the beginning of the file and count the occurrences by searching forward until you hit the end. Compare your count to the result of running grep All sonnets.txt | wc. (We’ll learn about grep in Section 3.4.)

A: `less sonnets.txt` wait, then search for `\All` advance with `n` go back with `N`, go back to beginning with `G`, and advance `n` to count 10 instances of "All". Compare with `grep All sonnets.txt | wc` which also yields 10 instances of "All". Hooray!

### Exercise 3
Q: Using less and / (“slash”), find the sonnet that begins with the line “Let me not”. Are there any other occurrences of this string in the Sonnets? 

A: `less sonnets.txt` wait, then enter `\Let me not`. Pressing `n` to advance results in "Pattern not found" thereby indicating that there are no other occurances of the string "Let me not" in the sonnet.

### Exercise 4
Q: Because man uses less, we are now in a position to search man pages interactively. By searching for the string “sort” in the man page for ls, discover the option to sort files by size. What is the command to display the long form of files sorted so the largest files appear at the bottom? Hint: Use ls -rtl as a model.

---
## 3.4 Greping

### Exercise 1
Q: By searching man grep for “line number”, construct a command to find the line numbers in sonnets.txt where the string “rose” appears.

A: `grep -n rose sonnets.txt`

### Exercise 2
Q: You should find that the last occurrences of “rose” is (via “roses”) on line 2203. Figure out how to go directly to this line when running less sonnets.txt. Hint: Recall from Table 4 that 1G goes to the top of the file, i.e., line 1. Similarly, 17G goes to line 17. Etc.

A: `less sonnets.txt` wait, then enter `2203G`

### Exercise 3
Q: By piping the output of grep to head, print out the first (and only the first) line in sonnets.txt containing “rose”. Hint: Use the result of the second exercise in Section 3.2.2.

A: `grep rose sonnets.txt | head -1`

### Exercise 4
Q: In Listing 18, we saw two additional lines that case-insensitively matched “rose”. Execute a command confirming that both of the lines contain the string “Rose” (and not, e.g., “rOSe”). 

A: `grep Rose sonnets.txt | wc`

### Exercise 5
Q: You should find in the previous exercise that there are three lines matching “Rose” instead of the two you might have expected from Listing 18. This is because there is one line that contains both “Rose” and “rose”, and thus shows up in both grep rose and grep -i rose. Write a command confirming that the number of lines matching “Rose” but not matching “rose” is equal to the expected 2.

A: `grep Rose sonnets.txt | grep -v rose | wc` grep Rose sonnets selects all the lines with "Rose". We then pipe this output through grep -v rose, which REMOVES the lines that also have "rose". We then pipe this output to wc to determine the number of lines (2).

---
## Summary

### Exercise 1
Q: The history command prints the history of commands in a particular terminal shell (subject to some limit, which is typically large). Pipe history to less to examine your command history. What was your 17th command?
A: `history | less`

### Exercise 2
Q: By piping the output of history to wc, count how many commands you’ve executed so far.
A: `history | wc`

### Exercise 3
Q: One use of history is to grep your commands to find useful ones you’ve used before, with each command preceded by the corresponding number in the command history. By piping the output of history to grep, determine the number for the last occurrence of curl.
A: `history | grep curl -n`

### Exercise 3
Q: What do the O and L options in Listing 8 mean?
A: `-O` = remote-output = write output to a file named as the remote file, `-L` = location/follows redirects

---
# 4: Directories

## 4.1 Directory Structure
Home directory is abbreviated as `~` therefore /Users/Joanne/ruby/projects is the same as ~/ruby/projects

### Exercise 3
