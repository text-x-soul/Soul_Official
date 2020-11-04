---
title: Python Usage
permalink: /docs/pyusage/
---
This documentation page guides you how to use implementations by various people in Python.

### teamYetZio's implementation(`PySoul`) : `format - 0.5.2`

Package: `PySoul`

#### `SoulParser.py`

Provides soul extensions as a list.

enums:
  - TypeIdentifiers

classes:
  - SoulParser, constructor with no params.
    - `Number`, `Soul_Register`, `Variable, Group`, `Group Variable` and `Comments` identifying `regex`.
    
#### `SoulStreamReader.py`

enums:
  - SoulMaps
  
classes:
  - SoulStreamReader constructor with default filename value empty, here we can't use two constructors.
    So better use filenames on using variables.
    - #### `Methods`:
      - ##### `def __init__(self, filename = "")`
        Initialization method, please provide filename while constructing a object based on SoulStreamReader.
      - ##### `def startStream(self)`
        This method runs everytime a soul file is configured with the current
        SoulStreamReader object. This can occur on setting filenames or while
        initializing one.
      - ##### `def setFileName(self, filename)`
        Sets the current filename
      - ##### `def getFileName(self)`
        Returns the current filename
      - ##### `def typeOf(self, key, mapvalue)`
        Returns the type of value in Map
      - ##### `def soulVersion(self)`
        Returns the Soul Version of the current soul document
      - ##### `def getVarValue(self, key)`
        Returns the variable value
      - ##### `def groupDef(self, key)`
        Returns the group Definition
      - ##### `def groupParams(self, key, index)`
        Returns the group params/parameters
      - ##### `def getGrpValue(self, group, param)`
        Returns the group value of a particular param
      - ##### `def infoMap(self)`
        Returns the SOUL_Registers map
      - ##### `def valueMap(self)`
        Returns the variable map
      - ##### `def grpMap(self)`
        Returns the Group map
      - ##### `def grpVarMap(self)`
        Returns the Group-Variable map

###### sample.soul
```
¡ SOUL_VERSION = 0.5.2 ¡

¿
These are
comments
?

¿ greeting = Hello World ?

value = 7 ¿ This is a comment, comments can be single and multi-line ?

example = well, hello there!

query() = {host, username, password, database}

host@(query) = localhost ¿ This is a comment, comments can be single and multi-line ?
username@(query) = root
password@(query) = passwd
database@(query) = db
```

###### `sample.py`
```py
import PySoul

soul_reader = PySoul.SoulStreamReader("sample.soul")

print(soul_reader.getVarValue("value")) # prints 7
print(soul_reader.getVarValue("example")) # prints well, hello there!
print(soul_reader.groupDef("query")) # prints [host, username, password, database]
print(soul_reader.groupParams("query", 2)) # prints password
print(soul_reader.getGrpValue("query", "username")) # prints root
```
