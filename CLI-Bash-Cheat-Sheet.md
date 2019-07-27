# CLI Primer / Cheat Sheet

**USEFUL LINKS / SOURCES:**

[https://lifehacker.com/a-command-line-primer-for-beginners-5633909](https://lifehacker.com/a-command-line-primer-for-beginners-5633909)

[https://learn.co/tracks/fswd-prework-2-0/cli-essentials/cli-essentials/bash-navigation](https://learn.co/tracks/fswd-prework-2-0/cli-essentials/cli-essentials/bash-navigation)

[https://www.thegeekstuff.com/2010/08/bash-shell-builtin-commands/](https://www.thegeekstuff.com/2010/08/bash-shell-builtin-commands/)

**Identify Logged-In Username**

- `whoami` reveals the user account you're logged in to from the CLI

**Identify the "Current Working Directory"**

- `pwd` ("print working directory") will return where you currently are

**Change Directories**

- `cd ..` to change to parent folder ("change directory")
- `~` shortcuts to home directory (as in `cd ~`)
- if in `/path/to` type `cd stuff` to get to the `stuff` folder
- `cd /another/path` to move to another path
- ex: in path `folder1/folder2` type `cd..` to get to `folder1`
    - move to `folder4` inside `folder3` from `folder1` by typing `cd folder3/folder4` etc.
- `-` to swap directories
    - ex: if you were in the `/first/folder/path/` directory and then switched over to `/etc/` to make a configuration change, you might not want to type in the full path to switch back. You can quickly switch back to the previous working directory with this command: `cd -`

**List files:** 

- `ls`
- add `-l` to see a detailed listing
- `-t` sort by time
- `-s` sort by size
- `-r` reverse sort
- ls `-lsr` will show files sorted by size with largest at the bottom
- `-a` shows hidden files
- `-h` an option for "**h**uman readable formats"
- `.` = folder
- `..` = parent folder

**Move or Rename Files and Directories**

- `mv` moves one or more files or directories from one place to another.
- `mv*filename /dirloc`* will move the specified *filename* file to the specified location (*/dirloc*)
- `mv` can also rename a file or directory
- `mv original_program.rb renamed_program.rb` will rename `original_program` to `renamed_program`
- `mv temp_download.gif ~/Desktop/cats_with_weapons/ninja_cat.gif` combines the two uses to move *and* rename the specified file

**Copy Files**

- `cp` is similar to mv but instead of renaming the original file, it makes a copy of it with a new name
- `cp letter_to_mom.txt letter_to_mom_2019.txt` creates a copy with a new name and retains the original `letter_to_mom.txt` file
- to copy a directory and its file contents, use the `-r` flag

**Creating or Removing Folders:** 

- `mkdir foldername` create a new folder
- `rmdir foldername` remove any folder, as long as the folder is empty (if there are files in the folder, you must delete those first to remove the folder)

**Creating and Removing Files:**

- `touch filename` creates a new blank file
- `rm filename` to delete files
- `rm *` to quickly remove all files in a directory
- `-r` for recursive, `-f` for force, to delete a list of files and folders including all files from subdirectories.
    - ex: `rm -rf filename.*`

**Edit Plain Text Files**

- `nano /path/to/file`

**Display Files**

- `cat` to display file contents directly on screen
- `more` or `less` will display contents of file and prompt you to scroll through the file one screen at a time
- ex: `more filename`
- `open` will trigger the default action associated with the file type
    - `open .` will popup a Finder window with the current directory in finder
- `echo` will have a program display a message or instructions
    - echo can also redirect text to a file as in

    `echo "I'm printing to the screen" >> *filename*`

Set `PATH` and Environment Variables

- An *environment variable* is a variable that can be configured to change the way the shell works and used by multiple applications or processes.
- `PATH` is an important environment variable. Directories whose names are listing in the `PATH` variable can have their programs run without having to `cd` to the directory where they are to run them
- Paths are assigned to `PATH` and separated by `:`

**Look Up Bash Documentation**

- `man` brings up the **man**ual pages for almost any command. Just type `man` and then the command you want information about
- `man ps` will give you info about the `ps` command
- 

**Command Redirection**

- use `>` or `|` operators to redirect output from one command into another to chain commands together

    **Examples:**

- `ls -l | more` will display a long list of files but it from scrolling off screen
- `ls -l > filename.list` will save the output of that list to a file, instead of displaying it on screen
- finally: `cat filename.list | grep *keyword* > filefound.list` to display the contents of that file, pipe that into the `grep` command, and then redirect to output into a separate file

**Running a Script in the Current Folder**

- `./scriptname.sh` , you must include the `./` because in Bash the current directory is not included in the system path.

**Using History**

- use the *`history`* command to show a list of all recently used commands, or the up/down arrows to loop through them
- `CTRL + R` shortcut key will start a search mode where you can search for a specific command

**Looping Over a Set of Files**

- Use the *for* command to loop through a set of files.

    **Example:** 

- `for f in *.txt;do echo $f;done` will loop through all the .txt files in the current directory and display them on the console.

**Find Files**

- the `find` command is very powerful, and can be used to search for files on your system.

    **Example:** 

- `find . -name "*.txt" -mtime 5` will find all files with .txt in the name that were modified in the last 5 days

**Find a Text String in Files**

- the grep command can quickly find text within files, even in subdirectories

    **Example:** 

- `grep -ir "text string" *` will search through all files in the current directory and below it for the specified "text string"

**Batch Rename Files**

- use the rename command to change file names using RegEx pattern

    **Example:** 

- `rename -v 's/foo/bar/g' *` will rename all files containing `foo` to contain `bar` instead

**Bash Shortcut Keys**

- `Ctrl + U` : clears the line from the cursor point back to the beginning
- `Ctrl + A` : moves the cursor to the beginning of the line
- `Ctrl + E` : Moves the cursor to the end of the line
- `Ctrl + R` : search through previous commands

**Tab Completion**

- in Bash you can use tab to allow the shell to try and guess what command you want to run.
- If there is one logical way to complete your command, Bash will fill in the rest for you, or show you the possibilities and you can add more letters until you can tab-complete your command.

**Using Aliases** 

- Aliases save time by shortening long complicated commands down to really simple ones, or by setting default parameters so you don't have to type them every time

    **Example:** 

- `alias agi='sudo apt-get install'` will set up an alias for installing packages on your setup that's quicker and simpler than `apt-get install *packagename`.* With the alias this becomes `agi *packagename*`
- `alias ls='ls -l'` sets up an alias so `ls` automatically includes the detail
- without arguments, or with the `-p` option, `alias` prints the list of aliases on the standard output in a form that allows them to be reused as input.
- `unalias` removes the specific alias from the list of aliases

**Bind**

- Display current Readline key and function bindings, bind a key sequence to a Readline function or macro, or set a Readline variable.
- Options, if supplied, have the following meanings:
    - `- m *keymap`* use *keymap* as the keymap to be affected by the subsequent bindings. Acceptable *keymap* names are: *emacs, emacs-standard, emacs-meta, emacs-ctlx, vi, vi-move, vi-command, and vi-insert. vi* is equivalent to *vi-comand*. *emacs* is equivalent to *emacs-standard*.
    - `-l` lists the names of all Readline functions
    - `-p` displays Readline function names and bindings in a way that they can be used as input or in a Readline initialization file.
    - `-P` lists current Readline function names and bindings
    - `-v` displays Readline variable names and values in a way that they can be used as input or in a Readline initialization file
    - `-V` lists current Readline variable names and values
    - `-s` displays Readline key sequences bound to macros and the strings they output in a way that they can be used as input or in a Readline initialization file
    - `-S` displays Readline key sequences bound to macros and the strings they output
    - `-f *filename`*  reads key bindings from *filename*
    - `-q *function`* query about which keys invoke the name *function*
    - `-u *function`* unbinds all keys bound to the named *function*
    - `-r *keyseq`* removes any current binding for *keyseq*
    - `-x *keyseq:shell-command`* causes *shell-command* to be executed whenever *keyseq* is entered.
    - `-X` lists all key sequences bound to the shell commands and the associated commands in a format that can be reused as input

**Control Your System from the Shell** 

- the `ps` command returns a list of system processes like this : `ps aux`
- the `kill <pid>` command will get rid of any processes you want to kill.
- `top` will easily kill processes in a more graphical list, simply by using the `K` key

**P.S.** 

- `q` to quit and return to command prompt, ya dummy