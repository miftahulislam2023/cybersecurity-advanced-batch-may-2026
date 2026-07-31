# Linux Commands Covered Till Now

## Commands
### Class 7
1. `pwd`
2. `cd`
3. `ls -lsah`
4. `clear` or `ctrl + l`
5. `mkdir <directory_name>`
6. `rmdir <directory_name>`
7. `whoami`
8. `mkdir -p dir1/dir2/dir3`
9. `echo "<text>"` (display a line of text)
10. `cat <file_name>` (display file contents)
11. `>` (redirect output, creating or overwriting a file)
12. `>>` (redirect output, appending to an existing file)

### Class 8
1. `rm <file_name>` (remove/delete files)
2. `rm -rf <directory_name>` (forcefully and recursively remove directories and files)
3. `rm -i <file_pattern>` (interactive removal, prompts before deleting)
4. `cat <file1> <file2> ...` (concatenate and display multiple files or content)
5. `*` (wildcard representing zero or more characters)
6. `?` (wildcard representing exactly one character)
7. `\` (escape character used to escape special characters in filenames)
8. `more` & `less` (pagers used to view file content page by page)

### Class 9
1. `wc -l` (line count)
2. `nano` (text editor)
3. `|` (pipe)
4. `man` (manual)
5. `uniq` (it only works on adjacent matching lines.)
6. `sort`
7. `su` (‘superuser’ or ‘switch user’)
8. `sudo` (as in “switch user and do this command”)

### Class 10
1. bash history (**~/.bash_history**, **clear**, **CTRL + R**)
2. redirection (**>** , **>>** , **<** , **<<** , **<<<**)
  -  `>` -> output redirection (overwriting)
     -  `ls -lsah > files.txt`
  -  `>>` -> output redirection (appending)
     -  `ls -lsah >> files.txt`
  -  `<` -> standard input redirection (from a file)
     -  **Syntax**: `command < filename`
     -  Use Cases: 
        - `sort < unsorted.txt` (Reads from file, sorts, outputs to terminal)
        - `mysql -u root -p db_name < backup.sql` (Load SQL commands)
  -  `<<` -> Here-Docoment Redirection (multi-line input)
     -  **Syntax**:
        ```bash
            command << DELIMITTER
            line 1
            line 2
            ...
            DELIMITTER
        ```
     - Use Cases:
       - Creating a multi-line file
         ```bash
         cat << EOF > test.txt
         Miftahul
         Islam
         Cyber Security
         EOF
         ```
       - Counting lines, words, and characters (Example: using `wc`)
         ```bash
            wc << goku
            line 1
            line 2
            ...
            goku
         ```
  -  `<<<` -> Here-String Redirection (single-line input)
     -  **Syntax**:
        ```bash
            command <<< "string"
        ```
     -  **Use Case**:
        -  Counting lines, words, and characters (Example: using `wc`)
           ```bash
           wc <<< "Miftahul Islam Cyber Security"
           ```
3. streams (**stdin** (0), **stdout** (1), **stderr** (2), **> /dev/null**)
4. bash configuration file (**/etc/skel**)
5. aliases (**alias c, install**)
6. seeing system usage (**top, htop, nload**)
7. permissions (**d** -> directory, **-** -> file)
8. `sudo adduser newuser`
9. `passwd`
10. `groups goku`
11. `sudo usermod -aG sudo goku`

### Class 11
- Working with Commands (type, which, man, whatis, alias)
  - which -> show path of a command
  - type -> show type of a command
  - man -> show manual of a command
  - whatis -> show one-line description of a command
  - alias -> create an alias for a command
- System Usages
  - top
  - htop
  - btop
  - uptime
  - df -h -i
  - free -m
  - nload
- Installing Softwares
  - sudo apt install apache
  - apt
    - search -> package search in repositories
    - install -> install a package
    - remove -> remove a package
    - autoremove -> remove unnecessary packages
    - dist-upgrade -> upgrade the system
    - show [package-name] -> show information about a package
- Text Editing Basic
  - nano
  - vim
  - mousepad
- find

### Class 12