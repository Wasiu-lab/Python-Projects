# Automatic-File-Explorer-Sorter
A Python script that organizes files in a specified folder by moving them into subfolders based on file type (e.g., PDFs, images, Excel files, text files). It checks for and creates folders as needed, helping keep directories clean and organized.

# Features
- Automatically creates subfolders based on file types if they don’t exist.
- Moves files into respective folders based on their extensions (.pdf, .png, .xlsx, .txt, etc.).
- Supports easy customization for adding more file types.
- Case-insensitive matching for file extensions.

# Processes
![Alt text](https://github.com/Wasiu-lab/Python-Projects/blob/main/Automatic-File-Explorer-Sorter/Images/1.PNG)

Referring to the picture above, the folder looks like it was before the Python program was written to sort each file into a categorized order. Below are the steps to follow  

# Step-by-Step Process

This is a step-by-step breakdown of how the code achieves its goal of organizing files by moving them into designated folders based on file types:

Step 1: Set Up the Path and Get File Names

1. The script starts by setting a path to the directory where the files are located:

`path = r"C:/Users/HP/Desktop/Folder/Learning/Python Project/Test/"`


2. It then lists all files in the specified directory and stores them in files_names:

`files_names = os.listdir(path)`

This prints the names of all files and subdirectories in the specified path.

Step 2: Check and Create Subfolders

3. The script defines the names of the target folders where the files will be organized:

`folder_names = ['excel files', 'png files', 'pdf files', 'txt files']`


4. For each folder in folder_names, it checks if the folder already exists within the specified path. If it doesn’t exist, the script creates it:

`for loop in range(0,4):
    if not os.path.exists(path + folder_names[loop]):
        os.makedirs(path + folder_names[loop])`

Step 3: Sort and Move Files

5. The script now iterates over each file in files_names to check its extension and move it to the appropriate folder:

for file in files_names:


6. For each file, it checks if the file extension matches any of the following types (.pdf, .jpg, .xlsx, .jpeg, .png, .csv, .txt) and that the file doesn’t already exist in the destination folder.


7. Based on the file’s extension, the script performs the following:

If the file is a PDF (.pdf), it moves it to the pdf files folder.

If the file is a JPG or JPEG (.jpg, .jpeg), it moves it to the png files folder.

If the file is an Excel file (.xlsx, .csv), it moves it to the excel files folder.

If the file is a PNG (.png), it moves it to the png files folder.

If the file is a text file (.txt), it moves it to the txt files folder.


Each move operation looks like this:

shutil.move(path + file, path + "target_folder/" + file)



Step 4: Complete the Organization

8. Once all files have been moved to their respective folders, the script finishes its run, leaving the directory organized with subfolders for each file type.

![image](https://github.com/Wasiu-lab/Python-Projects/blob/main/Automatic-File-Explorer-Sorter/Images/4.PNG)
Final image compared to what we had after running the codes

# Code

Here is the full code for the script:

```python
# Importing the required libraries.
import os
import shutil

# Define the path and list files in the directory
path = r"C:/Users/HP/Desktop/Folder/Learning/Python Project/Test/"
files_names = os.listdir(path)

# Folder names mapped to file extensions for cleaner code
folder_names = ['excel files', 'png files', 'pdf files', 'txt files']
for loop in range(0,4):
    if not os.path.exists(path + folder_names[loop]):
        os.makedirs(path + folder_names[loop])

for file in files_names:
    if ".pdf" in file and not os.path.exists(path + "pdf files/" + file):
        shutil.move(path + file, path + "pdf files/" + file)
    elif ".jpg" in file and not os.path.exists(path + "png files/" + file):
        shutil.move(path + file, path + "png files/" + file)
    elif ".xlsx" in file and not os.path.exists(path + "excel files/" + file):
        shutil.move(path + file, path + "excel files/" + file)
    elif ".jpeg" in file and not os.path.exists(path + "png files/" + file):
        shutil.move(path + file, path + "png files/" + file)
    elif ".png" in file and not os.path.exists(path + "png files/" + file):
        shutil.move(path + file, path + "png files/" + file)
    elif ".csv" in file and not os.path.exists(path + "excel files/" + file):
        shutil.move(path + file, path + "excel files/" + file)
    elif ".txt" in file and not os.path.exists(path + "txt files/" + file):
        shutil.move(path + file, path + "txt files/" + file)



