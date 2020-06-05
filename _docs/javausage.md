---
title: Java Usage
permalink: /docs/javausage/
---
This `documentation page` guides you how to use implementations by various people in Java.

### Master-Console Inc.'s implementation(`JSoul`): `format - 0.5.2`

Package : `pd.mime.soul`

Package name: JSoul

#### `SoulParser.java`
- Provides soul extensions as a `String` **array**.
- classes:
  - SoulParser, with one constructor and no params.
  - enums:
    - TypeIdentifiers
  - Provides 
      - `Number`, `Soul_Register`, `Variable, Group`, `Group Variable` and `Comments` identifying `regex`.
      
#### `SoulStreamReader.java`
classes:
  - SoulStreamReader with two constructors, one with filename and one without filename.
  - #### `Methods`:
    - ##### `public SoulStreamReader()`
      Constructs a SoulStreamReader object
    - ##### `public SoulStreamReader(String filename)`
      Constructs a SoulStreamReader object with provided filename
    - ##### `public void startStream()`
      Starts the file stream, parses the soul file and stores values in maps.
    - ##### `public void setFileName(String filename)`
      This method sets the filename of the `SoulStreamReader` object to the provided filename and starts the stream.
    - ##### `public String getFileName()`
      This method returns the current Soul File Document name.
    - ##### `public int typeOf(String key, SoulMaps map)`
      This method returns a `TypeIdentifier` **enum** value.
    - ##### `public String soulVersion()`
      This method returns the Soul file format version used by the document.
    - ##### `public String getVarValue(String variable)`
      This method returns the variable value where the key is the variable name.
    - ##### `public String[] groupDef(String key)`
        This method returns the group definition where key is the group name.
    - ##### `public String groupParams(String key, int index)`
        This method returns group parameters identified by group name.
    - ##### `public String getGrpValue(String group, String param)`
        This method returns the value of group param of a particular group where group is group name and param is parameter name
    - ##### `public Map<String, String> infoMap()`
        This method returns the SOUL_Register map.
    - ##### `public Map<String, String> valueMap()`
        This method returns the variable-value map.
    - ##### `public Map<String, String[]> grpMap()`
        This method returns the group-definition map.
    - ##### `public Map<List<String>, String> grpVarMap()`
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

###### Sample.java
```java
import pd.mime.soul.SoulStreamReader;
import java.util.Arrays;

public class Sample{
  public static void main(String[] args){
    SoulStreamReader soul_reader = new SoulStreamReader("sample.soul");
    System.out.println(soul_reader.getVarValue("value")); // prints 7
    System.out.println(soul_reader.getVarValue("example")); // prints well, hello there!
    
    // This provides a String array, so convert it to string before printing.
    System.out.println(Arrays.toString(soul_reader.groupDef("query"))); // prints [host, username, password, database]
    System.out.println(soul_reader.groupParams("query", 2)); // prints password
    System.out.println(soul_reader.getGrpValue("query", "username")); // prints root
  }
}

```
