# BetterDataManagement
The BDM ( Better Data Management ) Library is a Python Library designed to provide a better data management when it comes to files and directories.

# Installation

```python
pip install betterdatamanagement
```

# Library Usage

The library includes two new objects; The Bdir and the Bfile, referring to Better Directory and Better File, respectively.

## Better Directories

```python
from betterdatamanagement.bdir import Bdir

# Using a better directory is simple.
b = Bdir("path_to_directory")  # Initializes

# Object Attributes
b.path  # path_to_directory (C://Path//to//dir//MyDir)
b.dirname  # MyDir
b.contents  # Returns a JSON Serializable structure of the directory tree

# Deleting the directory
b.remove()  # This not only deletes the directory and all its contents but also turns the class useless. All the attributes are set to None from then on.

# Renaming a directory
b.rename('ILikeThisDir')  # C://Path//to//dir//MyDir -> C://Path//to//dir//ILikeThisDir
# All the attributes are updates accordingly

# Finding a specific item inside a directory
b.find('LovePoem.txt')  # This will only return the path of the first match.

# Finding more than one item inside a directory
b.find_all('Poem.txt')  # Returns a list of all the paths of the matched items.

# Moving the directory
b.move_to("new_path")  # Moves the directory physically to a new location and updates all the attributes accordingly

# Copying the directory to a new location
b.copy_to("new_path")  # Copies the directory to a new location.
# Checks if the directory already exists there, and if so adds a serial to the copy
# Ex.: MyPoems-1, MyPoems-2 and so on

```

### Bdir Contents Example

```python
# Raw_Response.py

>>> b.contents
{'MyPoems': {'*path': 'C:\\Users\\Alex\\Desktop\\MyPoems', 'FriendlyPoems': {'*path': 'C:\\Users\\Alex\\Desktop\\MyPoems\\FriendlyPoems', 'Poem1.txt': 'C:\\Users\\Alex\\Desktop\\MyPoems\\FriendlyPoems\\Poem1.txt', 'Poem2.txt': 'C:\\Users\\Alex\\Desktop\\MyPoems\\FriendlyPoems\\Poem2.txt'}, 'LovePoems': {'*path': 'C:\\Users\\Alex\\Desktop\\MyPoems\\LovePoems', 'Poem1.txt': 'C:\\Users\\Alex\\Desktop\\MyPoems\\LovePoems\\Poem1.txt', 'Poem2.txt': 'C:\\Users\\Alex\\Desktop\\MyPoems\\LovePoems\\Poem2.txt', 'Poem3.txt': 'C:\\Users\\Alex\\Desktop\\MyPoems\\LovePoems\\Poem3.txt'}, 'No i am not a poet.txt': 'C:\\Users\\Alex\\Desktop\\MyPoems\\No i am not a poet.txt'}
```

```json
// ContentsExample.json - Serialized JSON with (indent=4)
// *path is the directory path

{
    "MyPoems": {
        "*path": "C:\\Users\\Alex\\Desktop\\MyPoems",
        "FriendlyPoems": {
            "*path": "C:\\Users\\Alex\\Desktop\\MyPoems\\FriendlyPoems",
            "Poem1.txt": "C:\\Users\\Alex\\Desktop\\MyPoems\\FriendlyPoems\\Poem1.txt",
            "Poem2.txt": "C:\\Users\\Alex\\Desktop\\MyPoems\\FriendlyPoems\\Poem2.txt"
        },
        "LovePoems": {
            "*path": "C:\\Users\\Alex\\Desktop\\MyPoems\\LovePoems",
            "Poem1.txt": "C:\\Users\\Alex\\Desktop\\MyPoems\\LovePoems\\Poem1.txt",
            "Poem2.txt": "C:\\Users\\Alex\\Desktop\\MyPoems\\LovePoems\\Poem2.txt",
            "Poem3.txt": "C:\\Users\\Alex\\Desktop\\MyPoems\\LovePoems\\Poem3.txt"
        },
        "No i am not a poet.txt": "C:\\Users\\Alex\\Desktop\\MyPoems\\No i am not a poet.txt"
    }
}
```

## Better Files

```python
from betterdatamanagement.bfile import Bfile

# Using a better file is simple
b = Bfile("path_to_file")

# Objects Attributes
b.path  # filepath (C://path//to//file//MyFile.txt)
b.filename  # MyFile
b.binary  # Boolean - Returns True if file is binary and False if not.
b.extension  # .txt

# Deleting the file
b.remove()

# Renaming the file
b.rename("Buttercup Lyrics.txt")  # C://path//to//file//MyFile.txt -> C://path//to//file//Buttercup Lyrics.txt
# All the attributes are updated accordingly

# Moving the file
b.move_to("new_path")  # Moves the file to the new path and updates all the attributes accordingly

# Copying the file to a new location
b.copy_to("new_path")  # Copies the file to a new location.
# Checks if the file already exists there, and if so adds a serial to the copy
# Ex.: Poem-1, Poem-2 and so on.
```

### Quick Data Editing

It's recommended to use normal file editing if you wish to be more specific with the content. These methods are to be used for a quick edit.

```python
# Writing data to the file
b.write("Text")  # Writes data to the file, this will overwrite any existant data within.
# It has binary support and is able to write binary data too.

# Appending data to the file
b.append("Text")  # Appends data to the file, this will add in any data at the end of the file.
# It has binary support and is able to write binary data too.

# Retrieve the contents from the file
content, lines = b.get_contents()  # This method returns two values, the file content, and the file content in lines. (file.read, file.readlines())
# You may iterate over the lines for the content of each.
# It has binary support and is able to read binary data too.

```

