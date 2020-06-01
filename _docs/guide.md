---
title: Guide
permalink: /docs/guide/
---
This guide walks you through how the Soul file format works and how easy it is to implement it.
### Types
`Please note that types can be declared anywhere in the file`

#### Soul Registers

The most important type in Soul file format is the pre-processed information of a file or the data available by telling 
what this file is used for and what this file is. It is analogous to constants in various aspects of programming.

It is referred to `SOUL Registers` in Soul.

These can for example be referring to the Soul file format version, the programming language version being used or the 
type of file or content being used.

#### Variables

A `Variable` can be any type of data that can assign a value and later be changed. 

For Soul, you don't have to declare types. 
There are `no direct types` in Soul, you can however identify data of variable
if you wish to. For this Parsers implement data type identifier groups if the user wishes to know the type.

##### For your information

These are the type identifiers:
- `Unknown`: Unknown type of data.
- `Soul String`: A string.
- `Number`: An integer or decimal.
- [`Group`](https://text-x-soul.tk/docs/guide/#groups): A list like structure.
- [`Group Variables`](https://text-x-soul.tk/docs/guide/#group-varsgroup-variables): Variables that assign values to Group parameters.
- [`Info`](https://github.com/Master-Console/Soul_Official/new/master/_docs#soul-registers) : Soul Registers

#### Comments
`Comments` are points or annotations of text data that can used to refer to code. They are ignored by parsers and readers. 
Most programming languages and interfaces today have implemented comments for the easiness of the programmer.

There are no single comments for the soul file format till now. Comments here are both single and mutli-line, follows
only one rule.

#### Groups
`Groups` are list like structures that must declare `params/parameters` they should take in.
The parameters should finally take in a value that is assigned by a group variable that corresponds to
the specific parameter of that group.

#### Group Vars/Group Variables
The parameter values/`GROUP_VARS` are just like variables, they are assigned a value. They are later stored in a
`group-variable map` where the `GROUP_VAR` and the `group name` is the `key` to access the `value`.
