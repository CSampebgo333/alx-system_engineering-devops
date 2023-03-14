#Description of my 0x02-shell redirections project

Shell I/O Redirections, Filters


Task_0 : Write a script that prints “Hello, World”, followed by a new line to the standard output.
0-hello_world
#!/bin/bash
echo "Hello, World"

Task_01 : Write a script that displays a confused smiley "(Ôo)'.
1-confused_smiley
#!/bin/bash
echo "\"(Ôo)'"

Task_02 : Display the content of the /etc/passwd file.
2-hellofile
#!/bin/bash
cat /etc/passwd

Task_03 : Display the content of /etc/passwd and /etc/hosts
3-twofiles
#!/bin/bash
cat /etc/passwd /etc/hosts

Task_04 : Display the last 10 lines of /etc/passwd. Tips: “Thinks of it as a cat, what is at the end of it?”
4-lastlines
#!/bin/bash
tail -n 10 /etc/passwd

Task_05 : Display the first 10 lines of /etc/passwd
5-firstlines
#!/bin/bash
head -n 10 /etc/passwd

Task_06 : Write a script that displays the third line of the file iacta. The file iacta will be in the working directory. You’re not allowed to use sed
6-third_line
#!/bin/bash
head -n 3 iacta | tail -n 1

Task_07 : Write a shell script that creates a file named exactly \*\\'"Best School"\'\\*$\?\*\*\*\*\*:) containing the text Best School ending by a new line.
7-file
#!/bin/bash
echo "Best School" > \\\*\\\\"'\"Best School\"\\'"\\\\\*\$\\\?\\\*\\\*\\\*\\\*\\\*\:\)

Task_08 : Write a script that writes into the file ls_cwd_content the result of the command ls -la. If the file ls_cwd_content already exists, it should be overwritten. If the file ls_cwd_content does not exist, create it.
8-cwd_state
#!/bin/bash
ls -la > ls_cwd_content

Task_09 : Write a script that duplicates the last line of the file iacta. The file iacta will be in the working directory
9-duplicate_last_line
#!/bin/bash
tail -n 1 iacta >> iacta

Task_10 : Write a script that deletes all the regular files (not the directories) with a .js extension that are present in the current directory and all its subfolders.
10-no_more_js
#!/bin/bash
find . -type f -name "*.js" -delete

Task_11 : Write a script that counts the number of directories and sub-directories in the current directory. The current and parent directories should not be taken into account. Hidden directories should be counted
11-directories
#!/bin/bash
find . -type d -not -name '.' | wc -l

Task_12 : Create a script that displays the 10 newest files in the current directory.
Requirements:
@One file per line
@Sorted from the newest to the oldest
12-newest_files
#!/bin/bash
ls -t1 | head -n 10

Task_13 : Create a script that takes a list of words as input and prints only words that appear exactly once.
 @ Input format: One line, one word
 @ Output format: One line, one word
 @ Words should be sorted
13-unique
#!/bin/bash
sort | uniq -u

Task_14 : Display lines containing the pattern “root” from the file /etc/passwd
14-findthatword
#!/bin/bash
grep -i "root" /etc/passwd

Task_15 : Display the number of lines that contain the pattern “bin” in the file /etc/passwd
15-countthatword
#!/bin/bash
grep -c -i "bin" /etc/passwd

Task_16 : Display lines containing the pattern “root” and 3 lines after them in the file /etc/passwd.
16-whatsnext
#!/bin/bash
grep -i "root" -A 3 /etc/passwd

Task_17 : Display all the lines in the file /etc/passwd that do not contain the pattern “bin”.
17-hidethisword
#!/bin/bash
grep -i -v "bin" /etc/passwd

Task_18 : Display all lines of the file /etc/ssh/sshd_config starting with a letter.
 @ include capital letters as well
18-letteronly
#!/bin/bash
grep -i "^[a-z]" /etc/ssh/sshd_config

Task_19 : Replace all characters A and c from input to Z and e respectively
19-AZ
#!/bin/bash
tr "A" "Z" | tr "c" "e"

Task_20 : Create a script that removes all letters c and C from input.
#!/bin/bash
tr -d "cC"

Task_21 :  Write a script that reverse its input.
21-reverse
#!/bin/bash
rev


Task_22 : Write a script that displays all users and their home directories, sorted by users.
 @ Based on the the /etc/passwd file
22-users_and_homes
#!/bin/bash
cut -d ':' -f 1,6 /etc/passwd | sort


Task_23 : Write a command that finds all empty files and directories in the current directory and all sub-directories.
 @ Only the names of the files and directories should be displayed (not the entire path)
 @ Hidden files should be listed
 @ One file name per line
 @ The listing should end with a new line
 @ You are not allowed to use basename, grep, egrep, fgrep or rgrep
100-empty_casks
#!/bin/bash
find . -empty | rev | cut -d '/' -f 1 | rev


Task_24 : Write a script that lists all the files with a .gif extension in the current directory and all its sub-directories.
 @Hidden files should be listed
 @Only regular files (not directories) should be listed
 @The names of the files should be displayed without their extensions
 @The files should be sorted by byte values, but case-insensitive (file aaa should be listed before file bbb, file .b should be listed before file a, and file Rona should be listed after file jay)
 @One file name per line
 @The listing should end with a new line
 @You are not allowed to use basename, grep, egrep, fgrep or rgrep
102-acrostic
101-gifs
#!/bin/bash
find -type f -name "*.gif" | rev | cut -d "/" -f 1 | cut -d '.' -f 2- | rev | LC_ALL=C sort -f


Task_25 : An acrostic is a poem (or other form of writing) in which the first letter (or syllable, or word) of each line (or paragraph, or other recurring feature in the text) spells out a word, message or the alphabet. The word comes from the French acrostiche from post-classical Latin acrostichis). As a form of constrained    writing, an acrostic can be used as a mnemonic device to aid memory retrieval. Read more.
 @ Create a script that decodes acrostics that use the first letter of each line.
 @ The ‘decoded’ message has to end with a new line
 @ You are not allowed to use grep, egrep, fgrep or rgrep
103-the_biggest_fan
#!/bin/bash
cut -c 1 | paste -s -d ''

Task_26 : Write a script that parses web servers logs in TSV format as input and displays the 11 hosts or IP addresses which did the most requests.
 @ Order by number of requests, most active host or IP at the top
 @ You are not allowed to use grep, egrep, fgrep or rgrep
#!/bin/bash
tail -n +2 | cut -f -1 | sort -k 1 | uniq -c | sort -rnk 1 | head -n 11 | rev | cut -d ' ' -f -1 | rev
