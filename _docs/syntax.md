---
title: Syntax
permalink: /docs/syntax/
---
The following `documentation` provides the `syntax` of various types declared in `Soul` until now.

#### `Soul Registers`
`SOUL_Registers` are file type based recognition data such as where the file is being used, the SOUL file format version.

`SOUL_Registers` start with `¡` and end with `¡`

##### Example:
```
¡ SOUL_VERSION = 0.5.2 ¡
¡ CPP_REVISION = 17 ¡ 
¡ COPYRIGHT = Copyright (C) 2020 Your Company ¡
¡ BUILD = RELEASE ¡
```
These are some example data that can frequently be used with Soul Documents.

#### `Variables`
`Variables` are different types rather than being pre-processed data. They are stored in a different map such as a value or variable map.

##### Advantages
- They can be declared anywhere in the file except in comments
- Easily importable
- Highly accessible

##### Disadvantages
- Variable values are trimmed, be it string or others, that is Whitespace is removed from start and end not between words or numbers. 
  This may change on the coming standards.

Variables must contain a `declaration operator('=')` which correspond to this format:
- `VARIABLE = VALUE`

##### Example:
```
SAMPLESTRING = Hello World
MyNumber = 7
ExampleQuantity = vector<int> MyObject
```
#### `Comments`
In SOUL file format, comments start with `¿` and end with `?`. The comment format acts on both `single` and `multi-line`.

##### Example:
```
¿
This is
a multi-line
comment
?

¿ A sample greeting variable ?
GREET = Namaste
HEHE = 7 ¿ Heya!, don't forget that they can be declared here too. ?
```
#### `Groups`
`Groups` are list like structures that must declare params/parameters they should take in.

`Groups` are declared in this format: `EXAMPLEGROUP1() = {}`

**(i)** `EXAMPLEGROUP2() = {host}` **<-** Note that this group has a param declared. Now this param can be declared as a GROUP_VAR later in the file.

##### Example:
```
query() = {host, username, password, database} ¿ This is a group definition ?
```

#### `Group Vars`
`GROUP_VARS/Group Variables` are declared in this format:

**(i)** `EXAMPLEGROUPVAR@(GROUP) = VALUE` **<-** Note here that a group with the name provided inside the parenthesis must be valid or already declared.
##### Example:
```
query() = {host, username, password, database} ¿ This is a group definition ?
host@(query) = localhost                       ¿ whereas this is a group variable providing value for the param in query ?
username@(query) = root
password@(query) = passwd
database@(query) = db
```
