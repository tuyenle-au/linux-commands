# linux-commands
The ```man``` command is used to display the manual pages for a command. For example, to view the manual page for the ls command, you can type ```man ls``` in the terminal. The manual pages provide detailed information on the usage, options, and examples of the command.
using man more efficiently to find the commands you need:

# Important Linux Commands for Using `man`

| Command | Description | Example |
|---------|-------------|---------|
| `man` | Display the manual pages for a command | `man ls` |
| `man -k` | Search for commands based on keywords | `man -k search` |
| `apropos` | Search for commands based on keywords | `apropos search` |
| `man -f` | Search for commands based on their function | `man -f file` |
| `man -a` | Display all manual pages that match a specific keyword or command | `man -a search` |
| `manpath` | Display the current search path for manual pages | `manpath` |

# Important Linux Commands

| Command | Description | Example |
|---------|-------------|---------|
| `ls` | List directory contents | `ls /home/user/Documents` |
| `cd` | Change the current working directory | `cd /home/user/Documents` |
| `pwd` | Print the current working directory | `pwd` |
| `mkdir` | Create a new directory | `mkdir /home/user/new_directory` |
| `rm` | Remove a file or directory | `rm file.txt` or `rm -r directory` |
| `cp` | Copy files or directories | `cp file.txt /home/user/Documents` |
| `mv` | Move or rename files or directories | `mv file.txt newname.txt` or `mv directory new_directory` |
| `cat` | Concatenate and display files | `cat file.txt` |
| `grep` | Search for a pattern in a file or files | `grep "pattern" file.txt` |
| `find` | Search for files in a directory hierarchy | `find /home/user/Documents -name "*.txt"` |
| `tar` | Create or extract a tar archive | `tar -cvf archive.tar file.txt` or `tar -xvf archive.tar` |
| `ssh` | Securely connect to a remote machine | `ssh user@remote_host` |
| `scp` | Copy files securely between machines | `scp file.txt user@remote_host:/home/user/` |
| `sudo` | Run a command with elevated privileges | `sudo command` |
| `top` | Display system resource usage | `top` |
| `ps` | Display information about running processes | `ps -aux` |
| `kill` | Send a signal to a process | `kill PID` |
| `df` | Display disk usage | `df -h` |
| `du` | Display disk usage of a file or directory | `du -h file.txt` |


# Optional Parameters for the `find` Command

| Parameter | Description | Example |
|-----------|-------------|---------|
| `-name` | Searches for files with a specific name. | `find . -name file.txt` |
| `-iname` | Searches for files with a specific name, ignoring case. | `find . -iname FILE.txt` |
| `-type` | Searches for files of a specific type, such as directories or files. | `find . -type f` |
| `-size` | Searches for files of a specific size, such as larger or smaller than a certain value. | `find . -size +1M` |
| `-mtime` | Searches for files that have been modified within a specific time frame. | `find . -mtime -7` |
| `-perm` | Searches for files with specific permissions. | `find . -perm 644` |
| `-exec` | Executes a command on the files found by `find`. | `find . -name "*.txt" -exec grep "pattern" {} \;` |
| `-maxdepth` | Limits the search to a specified depth in the directory hierarchy. | `find . -maxdepth 1 -type d` |





# Linux Commands that Use `xargs`

| Command | Description | Example |
|---------|-------------|---------|
| `find` | Search for files in a directory hierarchy | `find . -type f -name "*.txt" -print0 \| xargs -0 grep "search_term"` |
| `grep` | Search for a pattern in a file or files | `grep "pattern" file.txt \| xargs sed -i 's/pattern/replacement/g'` |
| `locate` | Search for files or directories on the system | `locate file.txt \| xargs rm -rf` |
| `ps` | Display information about running processes | `ps -ef \| grep process_name \| awk '{print $2}' \| xargs kill` |
| `chmod` | Change the permissions of files or directories | `chmod -R 755 directory \| find directory -type d -print0 \| xargs -0 chmod 775` |



# 1. > To search for a file in the current directory and move it to a folder within the same directory if found, you can use the following commands:
```bash
file_name="file.txt"; folder_name="destination_folder"; ls | grep -w "$file_name" && mv "$file_name" "$folder_name/"
```
* file_name="file.txt": Sets a variable file_name with the value "file.txt". Replace "file.txt" with the name of the file you're searching for.

* folder_name="destination_folder": Sets a variable folder_name with the value "destination_folder". Replace "destination_folder" with the name of the folder within the same directory where you want to move the file.

* ls: Lists the files and directories in the current directory.

* grep -w "$file_name": Filters the output of the ls command using the grep command with the -w option. The -w option tells grep to perform a whole-word search, which means it will only match lines containing the exact word specified in the file_name variable.

* &&: A shell control operator that executes the following command only if the previous command succeeds (i.e., if the file is found by grep).

* mv "$file_name" "$folder_name/": Moves the found file to the specified folder. The mv command takes two arguments: the source file path (in this case, the value of the file_name variable) and the destination folder path (the value of the folder_name variable followed by a "/").

The command uses a pipeline (|) to pass the output of the ls command to the grep command, which then filters the list of files and directories to find the specified file. If the file is found, the mv command is executed to move the file to the specified folder.


# 2. > To search for files that match a specific word and open them with vim, you can use the grep command in combination with the find command and the xargs command. Here's an example:

```bash
find /path/to/search -type f -name "*input_word*" -print0 | xargs -0 grep -l "input_word" | xargs -o vim
```

Here's what each part of the command does:

* `find /path/to/search`: This starts the `find` command and specifies the directory to search for files in.
* `-type f`: This tells `find` to only look for files, not directories.
* `-name "*input_word*"`: This tells find to look for files whose name matches the pattern *input_word*, where input_word is the word you want to search for.
* `-print0`: This tells find to print the results separated by null characters, which is necessary when using the xargs command later on.
* `| xargs -0 grep -l "input_word"`: This takes the results from find and passes them to the xargs command, which then runs the grep command on each file to search for the word. The -l option tells grep to only print the names of files that contain the word.
* `| xargs -o vim`: This takes the names of the files that contain the word and passes them to the xargs command again, which then opens them in vim.

Note that you can replace vim with any other text editor that you prefer.
