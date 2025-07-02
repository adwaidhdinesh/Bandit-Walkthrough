# OverTheWire Bandit Levels 0-7 Walkthrough
## Level 0 → Level 1
**Objective**
SSH into the Bandit server using the provided credentials and find the password for the next level in a file called readme.
**Command**
ssh bandit0@bandit.labs.overthewire.org -p 2220
cat readme
**Explanation**
•	ssh: Connects to the remote Bandit server.
•	cat readme: Reads the contents of the readme file.
**Password Output** Your own password
________________________________________
## Level 1 → Level 2
**Objective**
Read the contents of a file literally named -.
**Command(s)**
cat ./-
OR
cat -- -
**Explanation**
•	./-: Refers to the file named - in the current directory.
•	--: Tells cat to stop interpreting flags and treat - as a filename.
**Password Output** Your own password
________________________________________
## Level 2 → Level 3
**Objective** Read a file with spaces in its name: "spaces in this filename".
**Command(s)**
cat 'spaces in this filename'
 OR
cat spaces\ in\ this\ filename
**Explanation**
•	Quotes or backslashes escape spaces in the filename.
**Password Output** Your own password
________________________________________
## Level 3 → Level 4
**Objective** Find a hidden file (starts with .) in the inhere directory.
**Command(s)**
cd inhere
ls -a
cat .hidden
**Explanation**
•	ls -a: Lists all files including hidden ones.
•	.hidden: The hidden file containing the password.
**Password Output** Your own password
________________________________________
## Level 4 → Level 5
**Objective** Find the only human-readable file in the inhere directory.
**Command(s)**
cd inhere
ls
file ./*
cat ./-file07
**Explanation**
•	cd inhere: Changes to the /home/bandit4/inhere directory.
•	ls: Lists files (e.g., -file00 to -file09).
•	file ./*: Checks the file types to identify the human-readable (ASCII text) file. In this case, -file07 is the only ASCII text file.
•	cat ./-file07: Reads the contents of -file07, which contains the password for Level 5.
**Password Output** Your own password
________________________________________
## Level 5 → Level 6
**Objective** Find a file in the inhere directory that is:
•	human-readable
•	1033 bytes in size
•	not executable
**Command(s)**
cd inhere
find / -type f -user bandit5 -group bandit5 -size 1033c 2>/dev/null
*OR*
find . -type f -size 1033c -readable ! -executable
cat ./maybehere07/.file2
**Explanation**
•	find: Searches files with specific conditions.
•	2>/dev/null: Suppresses permission denied errors.
•	1033c: Means 1033 bytes exactly.
*OR*
•	find: Searches files with specific conditions.
•	-size 1033c: Means 1033 bytes exactly.
•	-readable ! -executable: Human-readable and not executable.
**Password Output** Your own password
________________________________________
## Level 6 → Level 7
**Objective** Find a file somewhere on the server that is:
•	owned by user bandit7
•	owned by group bandit6
•	33 bytes in size
**Command(s)**
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password
**Explanation**
•	find /: Searches the entire filesystem.
•	-user bandit7 -group bandit6: Specifies ownership requirements.
•	-size 33c: 33 bytes exactly.
•	2>/dev/null: Suppresses permission denied errors.
**Password Output** Your own password
 
