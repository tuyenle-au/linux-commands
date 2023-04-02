# linux-commands

1. To search for a file in the current directory and move it to a folder within the same directory if found, you can use the following commands:
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


2. To search for files that match a specific word and open them with vim, you can use the grep command in combination with the find command and the xargs command. Here's an example:

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
