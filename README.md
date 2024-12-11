# IT-Operations-Administrator-Assignment
PS1 Scripting


**The run-restart-service-windows PowerShell script used for checking and managing the status of a Windows service. Here's what it does, step by step:**

**Define the Service Name**
The variable $ServiceName is defined and should be replaced with the actual service name (e.g., InventorySvc).

**Get the Status of the Service**
It retrieves the service's status using the Get-Service cmdlet with the specified service name.
The -ErrorAction SilentlyContinue ensures that no errors are displayed if the service does not exist.

**Check if the Service Exists**
If the service exists ($Service is not null), the script proceeds to check its status.

**Check if the Service is Running**
If the service's status is not Running, it attempts to restart the service.
Displays a message that the service is not running and will be restarted (text displayed in yellow).

**Uses a try-catch block to handle errors when attempting to restart the service**
If successful, a success message is displayed in green.
If it fails, an error message is displayed in red, showing the error details.

**Check if the Service is Already Running:**
If the service is already running, a message confirming its running state is displayed in green.

**Handle the Case Where the Service Does Not Exist**
If the service does not exist ($Service is null), a message is displayed in red stating that the service name is invalid and needs to be confirmed.

**Key Features:**
Provides feedback to the user about the service's status and actions performed.
Uses color coding to make messages more visually distinguishable:
Yellow: Informational messages (e.g., restarting the service).
Green: Success messages (e.g., service is running or restarted successfully).
Red: Error or failure messages (e.g., service does not exist or failed to restart).


**Here's what windows-running-process-cvs script does, explained in bullet points:**

**Define Output File Path**
Specifies the file path (C:\Temp\RunningProcesses.csv) where the list of running processes will be exported.

**Check and Create Directory**
Checks if the directory for the output file exists using Test-Path.
If the directory does not exist, it creates the directory using New-Item.

**Retrieve Running Processes**
Uses the Get-Process cmdlet to retrieve details of all currently running processes.

**Select Relevant Properties**
Filters the process data to include specific properties: Name, Id, CPU, WorkingSet, StartTime, and ProcessName.

**Export Data to CSV**
Exports the selected process details to the specified CSV file using Export-Csv.
The -NoTypeInformation parameter omits type information from the CSV.
The -Force parameter ensures the file is overwritten if it already exists.

**Display Completion Message**
Outputs a confirmation message to the console indicating the process list has been exported and specifies the file location.


**The windows-find-read-replace-word script performs the following tasks:**

**Defines Inputs**
Specifies the folder path ($folderPath) where the script will look for text files.
Defines the word to find ($wordToFind) and its replacement ($replacementWord).

**Creates a Tracking List**
Initializes an empty array ($modifiedFiles) to store the names of files that are modified.

**Handles Errors Gracefully**
Wraps the operations in a Try-Catch block to manage unexpected errors.

**Searches for Text Files**
Recursively retrieves all .txt files in the specified folder using Get-ChildItem.
If no text files are found, displays a warning message.

**Processes Each File**
Reads the content of each text file.
Checks if the file contains the word to be replaced ($wordToFind).

**If the word is found**
Replaces it with the specified replacement word ($replacementWord).
Saves the updated content back to the same file using Set-Content.
Adds the file's name to the $modifiedFiles list and logs the modification.

**Displays Results**
If no files were modified, shows a message indicating no changes were made.
If files were modified, lists the names of the modified files.

**Error Reporting**
In case of an error, displays a message with details of the exception.
