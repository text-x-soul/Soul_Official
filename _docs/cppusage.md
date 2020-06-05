---
title: C++ Usage
permalink: /docs/cppusage/
---
This `documentation page` guides you how to use implementations by various people.

### Master-Console Inc.'s implementation : `format - 0.5.2`

Classes use namespace `Soul`
#### `SoulParser.h`

- Uses Regex Library known as [`SRELL`](http://www.akenotsuki.com/misc/srell/en/)
- Provides soul extensions as a std::vector<<std::string>>

classes:
  - SoulParser with one **constructor**, no params
    - Contains TypeIdentifiers **enum**.
    - Provides 
      - `Number`, `Soul_Register`, `Variable, Group`, `Group Variable` and `Comments` identifying `regex`.

#### `SoulStreamReader.h`
classes:
  - `SoulStreamReader` with two **constructors**, one `with filename` and one without `filename`.
    - `SoulMaps` enum
    - #### `Methods`:
      - #### void startStream()
        This method runs on constructing or reading a soul configuration file.
      - #### int typeOf(std::string key, SoulMaps map)
        This method returns a `TypeIdentifier` **enum** value.
      - #### void setFileName(std::string filename)
        This method sets the filename of the `SoulStreamReader` object to the provided filename and starts the stream
        using `startStream()`
      - #### void getFileName()
        This method returns the current Soul File Document name.
      - #### std::string soulVersion() const
        This method returns the Soul file format version used by the document.
      - #### std::string getVarValue(std::string key)
        This method returns the variable value where the key is the variable name.
      - #### std::vector<<std::string>> groupDef(std::string key)
        This method returns the group definition where key is the group name.
      - #### std::string groupParams(std::string key, int index)
        This method returns group parameters identified by group name.
      - #### std::string getGrpValue(std::string group, std::string param)
        This method returns the value of group param of a particular group where group is group name and param is parameter name
      - #### std::map<std::string, std::string> infoMap()
        This method returns the SOUL_Register map.
      - #### std::map<std::string, std::string> valueMap()
        This method returns the variable-value map.
      - #### std::map<std::string, std::vector<<std::string>>> grpMap()
        This method returns the group-definition map.
      - #### std::map<std::vector<<std::string>>, std::string> grpVarMap()
        This method returns the group-variable map.
        
##### Sample Program

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

###### sample.cpp
```c++
#include <iostream>
#include <SoulStreamReader.h>

using namespace Soul;

int main(){
  SoulStreamReader *soul_reader = new SoulStreamReader("sample.soul");
  std::cout << soul_reader.getVarValue("value") << std::endl; // prints 7
  std::cout << soul_reader.getVarValue("example") << std::endl; // prints well, hello there!
  std::cout << soul_reader.groupDef("query") << std::endl; // prints {host, username, password, database}
  std::cout << soul_reader.groupParams("query", 2) << std::endl; // prints password
  std::cout << soul_reader.getGrpValue("query", "username") << std::endl; // prints root
  return 0;
}
```

`IMPORTANT NOTE:` If you have any implementations, please open up a issue on our [Github repo](https://github.com/text-x-soul/text-x-soul)and submit a Documentation like above one/ones.
