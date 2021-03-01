# Intellij Idea Settings

## Structure for New Projects

File -> New Project Settings -> Structure for New Projects

- Project Settings --> Project --> Project SDK: 1.8, Project language level: 8

## Settings for New Projects

File -> New Project Settings -> Settings for New Projects

- Appearance
  - Font Size
    - Change font size with Ctrl+Mouse Wheel
    - Change font size permanently
- Keymap
  
  - [x] Recent Files
- Editor
  - General
    - Editor Tabs
      - [x] Uncheck Show tabs in one row
      - [x] Uncheck Match case
    
  - File Encodings
  
    - Global Encoding: UTF-8, Project Encoding: UTF-8, Properties Files: UTF-8
  
  - [x] File and Code Templates
  
    ```
    #if (${PACKAGE_NAME} && ${PACKAGE_NAME} != "")package ${PACKAGE_NAME};#end
    #parse("File Header.java")
    /**
     * 
     * @author ${USER}
     */
    public class ${NAME} {
    }
    ```
- Build, Execution, Deployement
  - Build Tools
    - Maven
      - [x] Maven home directory: $M2_HTOM
      - [x] User settings file: $M2_HOME/conf/settings.xml
      - [x] Local repository: `D:\$UserData\.m2\repository`
  - Compiler
    - [x] Project bytecode version: 8
  - [ ] Code completion
  - File Template
  - Live Templates

## Install Plugins

## Update Shortcuts



## Appearance

### Font Size

#### Change font size with Ctrl+Mouse Wheel

File → Settings → Editor → General → (checked) Change font size (Zoom) with Ctrl+Mouse Wheel

#### Change font size permanently

File → Settings → Editor -> Font -> Size: 14

## Coding

### code completion

#### Case-insensitive code completion

Preferences -> Editor -> General -> Code Completion

or search "Code Completion" in settings

#### Match Case All letters

Uncheck `Match case`

### Maven Settings

- Maven home directory, maven settings file, maven local repository
- Auto import pom.xml change

### File Template

File templates are specifications of the default contents to be generated when creating a new file.

My Template

```
#if (${PACKAGE_NAME} && ${PACKAGE_NAME} != "")package ${PACKAGE_NAME};#end
#parse("File Header.java")
/** 
 * 
 * @author ${USER}
 */
public class ${NAME} {
}
```

Create a new file template, or copy an existing file template

- In the **Settings/Preferences** dialog Ctrl+Alt+S, select **Editor | File and Code Templates**

File and code templates are written in the [Velocity Template Language](http://velocity.apache.org/) (VTL), which enables using the following constructs:

- Fixed text (markup, code, comments, and so on), which is rendered as-is.
- [Variables](https://www.jetbrains.com/help/idea/file-template-variables.html), which are replaced by their values.
- Various directives, including [#parse](https://www.jetbrains.com/help/idea/parse-directive.html), `#set`, `#if`, and others.

Fore more information, see the [VTL reference guide](http://velocity.apache.org/engine/2.0/vtl-reference.html).

Reference:

- [File and code templates](https://www.jetbrains.com/help/idea/using-file-and-code-templates.html)

### Live Templates

| Abbreviation     | Expands to                                  |
| ---------------- | ------------------------------------------- |
| `psfs`           | `public static final String`                |
| `main` or `psvm` | `public static void main(String[] args){ }` |
| `sout`           | `System.out.println();`                     |
| `fori`           | `for (int i = 0; i < ; i++) { }`            |
| `ifn`            | `if (var == null) { }`                      |

References:

- [Live templates](https://www.jetbrains.com/help/idea/using-live-templates.html)