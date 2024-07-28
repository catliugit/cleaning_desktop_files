## File Organizer Script
This Python script helps you keep your Downloads folder organized by automatically categorizing files based on their type and creation date.

## Overview
The script moves files into folders based on their file type (e.g., Images, PDFs) and further organizes them into subfolders named by the creation date (Month_Year). It also includes a logging feature to track the script's actions and any issues encountered.

## File Organization
Files are categorized into predefined folders such as Images, PDFs, Excel, etc.
Within each category, files are sorted into subfolders based on their creation date, formatted as Month_Year.
Conflict Handling:

If a file with the same name exists in the target folder, the script appends a counter to the filename (e.g., file_copy1.pdf) to prevent overwriting.

## Logging
The script uses Python's logging module to record detailed logs of the organization process.
Logs include the timestamp, log level (e.g., DEBUG, INFO, WARNING, ERROR), and a descriptive message.

## Logging Configuration
The logging is configured at the DEBUG level, which means all levels of logs are captured.
The log format includes the date and time, log level, and message.

## Directory and File Handling:
The script uses the os module for interacting with the file system and shutil for moving files.
It checks if a directory exists before creating it using os.makedirs() and uses shutil.move() to relocate files.

## Steps to Use
## Download the Script
[File Organizer Python Script](https://github.com/catliugit/organizing_desktop_files/blob/main/src/organizing_files.py).

## Run the Script
Ensure Python is installed on your system.
Place the script in your desired directory and execute it. The script will organize files in your Downloads folder.

## View Organized Files
After execution, check the Downloads folder to see your files neatly organized into the new structure.

## Example
The Downloads folder may appear cluttered with various file types as displayed in this [example](https://github.com/catliugit/organizing_desktop_files/blob/main/Before_Script_Run.PNG).
After Running the Script: Files are organized into categorized and dated subfolders. Here are the expected outputs:
[Month Year Folders, ](https://github.com/catliugit/organizing_desktop_files/blob/main/After_Script_Run_Month_Year_Folders.PNG)
[File Type Folders, ](https://github.com/catliugit/organizing_desktop_files/blob/main/After_Script_Run_File_Type_Folders.PNG)
[File Classified in the Folder](https://github.com/catliugit/organizing_desktop_files/blob/main/After_Script_Run_File_Organized.PNG).

## Logging Output
[The log messages provide feedback on the actions taken](https://github.com/catliugit/organizing_desktop_files/blob/main/After_Script_Run_Log_Message.PNG).

## Creation of folders
Moving of files
Handling of name conflicts
Any issues or warnings
This output is useful for verifying the script's behavior and troubleshooting if necessary.

## Conclusion
This is a great script for anyone looking to automate tedious file organization tasks.


