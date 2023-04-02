# linux-commands

1. To search for a file in the current directory and move it to a folder within the same directory if found, you can use the following commands:
```bash
file_name="file.txt"; folder_name="destination_folder"; ls | grep -w "$file_name" && mv "$file_name" "$folder_name/"
```
Replace file.txt with the name of the file you're searching for, and destination_folder with the name of the folder within the same directory where you want to move the file.
