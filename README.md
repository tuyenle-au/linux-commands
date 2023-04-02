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
