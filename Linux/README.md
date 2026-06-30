# Linux Command Guide

## Video Links
- [Basic Linux Commands](https://www.youtube.com/watch?v=tJehQ9tw5tk)

## Basic Navigation and Directory Management
- **Present Working Directory:**
  ```bash
  pwd
  ```
  Displays the current directory path.

- **Username:**
  ```bash
  whoami
  ```
  Shows the current logged-in user's name.

- **List Files and Directories:**
  ```bash
  ls
  ```
  Lists files and directories in the current directory.

- **Create Directories:**
  ```bash
  mkdir <directory_name> <directory_name> ...
  ```
  Creates one or more directories.

- **Change Directory:**
  ```bash
  cd <directory_name>
  ```
  Changes the current directory to the specified one.

- **To Go Back to the Parent Directory:**
  ```bash
  cd ..
  ```
  Moves up one directory level.

- **Clear Screen:**
  ```bash
  clear
  ```
  Clears the terminal screen.

- **Create Files:**
  ```bash
  touch <file_name> <file_name> ...
  ```
  Creates one or more empty files.

## Basic Text Editing Commands
- **Overwrite File Content:**
  ```bash
  echo "<info>" > <file_name>
  ```
  Overwrites the content of a file with the specified information.

- **Append to File Content:**
  ```bash
  echo "<info>" >> <file_name>
  ```
  Appends the specified information to a file.

- **Edit with Nano Editor:**
  ```bash
  nano <file_name>
  ```
  Opens the file in the Nano text editor.

  - **Save Changes:** Ctrl + O, then press Enter
  - **Exit:** Ctrl + X

- **Edit with Vi Editor:**
  ```bash
  vi <file_name>
  ```
  Opens the file in the Vi text editor.

  - **Enter Insert Mode:** i
  - **Save Changes:** :w
  - **Quit:** :q
  - **Quit Without Saving:** :q!

## Basic Commands to Remove Files
- **Delete Empty Folder:**
  ```bash
  rmdir <folder_name> <folder_name> ...
  ```
  Deletes one or more empty directories.

- **Delete Files/Non-empty Folders:**
  ```bash
  rm -rf <file_name/folder_name> <file_name/folder_name> ...
  ```
  Removes files or directories recursively and forcefully.

## List Contents of a Folder
- **Detailed Information:**
  ```bash
  ls -l
  ```
  Lists files with detailed information (permissions, owner, size, etc.).

- **Reverse Order:**
  ```bash
  ls -lr
  ```
  Lists files in reverse order.

- **Sorted by Modification Time:**
  ```bash
  ls -lt
  ```
  Lists files sorted by modification time (most recent first).

- **Reverse Sorted by Modification Time:**
  ```bash
  ls -ltr
  ```
  Lists files sorted by modification time in reverse.

- **Including Hidden Files:**
  ```bash
  ls -la
  ```
  Lists all files, including hidden ones (files starting with a dot).

- **Human-Readable Sizes:**
  ```bash
  ls -lh
  ```
  Lists files with sizes in human-readable format (KB, MB, etc.).

## Cat Command
- **Display Multiple Files:**
  ```bash
  cat <file_name_1> <file_name_2> ...
  ```
  Displays the content of multiple files.

- **Create and Write to File:**
  ```bash
  cat > <file_name>
  ```
  Creates a file and writes content to it. End with Ctrl + D.

- **Append Content:**
  ```bash
  cat <file_name_1> >> <file_name_2>
  ```
  Appends the content of one file to another.

- **Display with Line Numbers:**
  ```bash
  cat -n <file_name>
  ```
  Displays the content of a file with line numbers.

## Understanding `head` and `tail` Commands
- **Top 10 Rows of Data:**
  ```bash
  head <file_name>
  ```
  Displays the first 10 rows of data from a file.

- **Last 10 Rows of Data:**
  ```bash
  tail <file_name>
  ```
  Displays the last 10 rows of data from a file.

- **Top 15 Rows of Data:**
  ```bash
  head -n 15 <file_name>
  ```
  Displays the first 15 rows of data from a file.

- **Last 15 Rows of Data:**
  ```bash
  tail -n 15 <file_name>
  ```
  Displays the last 15 rows of data from a file.

## Understanding `cp` and `mv` Commands
- **Copy a File:**
  ```bash
  cp <file_to_be_copied> <destination>
  ```
  Copies a file to another location.

- **Copy a Directory:**
  ```bash
  cp -r <dir_to_be_copied> <destination>
  ```
  Copies a directory and its contents.

- **Move a File/Folder:**
  ```bash
  mv <source> <destination>
  ```
  Moves a file or folder to another location.

- **Rename a File/Folder:**
  ```bash
  mv <old_name> <new_name>
  ```
  Renames a file or folder.

## Pattern Matching using `grep`
- **Search for a Pattern:**
  ```bash
  grep "pattern" <file_name>
  ```
  Searches for a pattern in a file.

- **Search for a Case-Insensitive Pattern:**
  ```bash
  grep -i "pattern" <file_name>
  ```
  Searches for a pattern in a file, ignoring case.

- **List Files Containing the Pattern:**
  ```bash
  grep -l "pattern" <file_name>
  ```
  Lists files containing the specified pattern.

- **Count Occurrences of a Pattern:**
  ```bash
  grep -c "pattern" <file_name>
  ```
  Counts the occurrences of a pattern in a file.

- **Show Lines After a Matching Pattern:**
  ```bash
  grep -A 2 -i "pattern" <file_name>
  ```
  Displays the matched line and 2 lines after the matching pattern, ignoring case.

- **Show Lines Before a Matching Pattern:**
  ```bash
  grep -B 2 -i "pattern" <file_name>
  ```
  Displays the matched line and 2 lines before the matching pattern, ignoring case.

- **Show Context Around a Matching Pattern:**
  ```bash
  grep -C 2 -i "pattern" <file_name>
  ```
  Displays the matched line and 2 lines before and after the matching pattern, ignoring case.

- **Search for an Exact Word:**
  ```bash
  grep -w "exact_word" <file_name>
  ```
  Searches for an exact word in a file, matching whole words only.

- **Using Wildcards:**
  ```bash
  grep "*.txt" <directory>
  ```
  Searches within all text files in a directory.

## Using the `find` Command
- **Find Files or Directories by Name:**
  ```bash
  find <directory> -name "pattern"
  ```
  Searches for files or directories matching the specified pattern.

- **Find Directories Only:**
  ```bash
  find <directory> -type d
  ```
  Searches for directories only.

- **Find Files Only:**
  ```bash
  find <directory> -type f
  ```
  Searches for files only.

- **Search in the Current Directory:**
  ```bash
  find . -name "pattern"
  ```
  Searches in the current directory.

## `sort` Command
- **Sort Lines in a File:**
  ```bash
  sort <file_name>
  ```
  Sorts the lines in the specified file in ascending order.

- **Sort Lines in Reverse Order:**
  ```bash
  sort -r <file_name>
  ```
  Sorts the lines in the specified file in descending order.

## Process Management Commands
- **View Processes:**
  ```bash
  ps
  ```
  Displays the currently running processes.

- **View All Processes:**
  ```bash
  ps -e
  ```
  Displays all running processes.

- **View Processes with Full Details:**
  ```bash
  ps -f
  ```
  Displays processes with full details (e.g., PID, PPID, etc.).

- **View All Processes with Full Details:**
  ```bash
  ps -ef
  ```
  Displays all processes with full details.

- **To Kill a Process:**
  ```bash
  kill <processID>
  ```
  Terminates a process by its ID.

## Jenkins and AWS Configuration
- **Download a File:**
  ```bash
  wget <url>
  ```
  Downloads a file from the specified URL.

- **Update Package Lists:**
  ```bash
  sudo apt update
  ```
  Updates the list of available packages and their versions.

- **Install Java:**
  ```bash
  sudo apt install openjdk-11-jdk
  ```
  Installs Java.

- **Check Java Version:**
  ```bash
  java --version
  ```
  Checks and displays the installed Java version.

- **Start a WAR File as Main Process:**
  ```bash
  java -jar <war_file_name>.war
  ```
  Starts a WAR (Web Application Archive) file.

  - **To stop:** press Ctrl + C.

- **AWS Configuration for Accessing Jenkins (Enabling Port 8080):**
  - In the EC2 Dashboard:
    - Select the instance ID.
    - Scroll to "Security" and click on "Security Groups".
    - Scroll to "Inbound Rules" and click "Edit Inbound Rules".
    - Add a new rule with "Port Range = 8080" and save the changes.

- **Accessing Jenkins:**
  Access Jenkins at `<ip_address>:8080` using the generated password.

- **Run a WAR File as a Background Process:**
  - **Create a Shell Script:**
    ```bash
    echo "java -jar <war_file_name>.war" > run_war.sh
    ```
    Creates a script to run the WAR file.

  - **Run the Script in the Background:**
    ```bash
    nohup sh run_war.sh &
    ```
    Runs the script in the background.

  - **To Kill the Background Process:**
    - **Find the Process ID:**
      ```bash
      ps
      ```
      Lists processes to find the process ID.

    - **Kill the Process:**
      ```bash
      kill <ProcessID>
      ```
      Terminates the process by its ID.

## To Zip and Unzip Files
- **To Zip a File:**
  ```bash
  gzip <file_name> <file_name> ...
  ```
  Compresses files.

- **To Unzip a File:**
  ```bash
  gunzip <file_name> <file_name> ...
  ```
  Decompresses files.

- **To Zip a Folder:**
  ```bash
  tar -czvf <new_folder_name>.tar.gz <folder_to_be_compressed>
  ```
  Compresses a folder.

- **To Unzip a Folder:**
  ```bash
  tar -xzvf <new_folder_name>.tar.gz
  ```
  Decompresses a folder.

## Comparison Commands
- **To Compare Byte by Byte (usually for binary files):**
  ```bash
  cmp <file1> <file2>
  ```

- **To Compare Line by Line (usually for text files):**
  ```bash
  diff <file1> <file2>
  ```

## `at` Command
- **To Install `at`:**
  ```bash
  sudo apt install at
  ```

- **Use `at` Command:**
  ```bash
  at <time_eg_5:00 AM>
  ```
  Write the commands that have to be executed in future and press Ctrl + D to exit.

- **To Get Job Schedules:**
  ```bash
  atq
  ```

- **To Remove a Job:**
  ```bash
  atrm <job_id>
  ```

---
