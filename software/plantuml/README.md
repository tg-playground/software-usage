# Plantuml Note

- Download plantuml.jar
- Installing graphviz
- Using PlantUML
- PlantUML Documentation

## Download plantuml.jar

[Download PlantUML](https://plantuml.com/download)

Writing HelloWorld.txt

```
@startuml
Bob->Alice : hello
@enduml
```

Generating HelloWorld UML Diagram

```shell
java -jar plantuml.jar HelloWorld.txt
```

Open HelloWorld.png

## Installing graphviz

- Download [graphviz.zip](https://graphviz.gitlab.io/download/)
- unzip
- Set environment variable `GRAPHVIZ_DOT={your_path}\graphviz-2.38\release\bin\dot.exe`
- Verify by `java -jar plantuml.jar -testdot`

## Using Plantuml

### Using by command line generating UML diagram picture

```shell
java -jar plantuml.jar {your_plantuml}.txt
```

### Using by Intellij IDEA Plugins

installing plugins `PlantUML integration`, `PlantUML Syntax Check`

Writing plantuml language text, open Plantuml window searching by  `Ctrl + Shift + A` to display the diagram.

## PlantUML Documentation

[PlantUML Getting Started](https://plantuml.com/starting)

[PlantUML Language Reference Guide](https://plantuml.com/download)

## Reference

[1] [plantuml](https://plantuml.com)