# Idea Enable Spring DevTools

1. Add Spring Boot Dev Tools

`pom.xml`

```
<!-- hot swapping, enable live reload -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
    <optional>true</optional>
</dependency>
```

2. Build Project Automatically

File –> Setting –> Build, Execution, Deployment –> Compiler –> check this `Build project automatically`

3. Intellij Registry

Press `SHIFT+CTRL+A` (Win/*nix) or `Command+SHIFT+A` (Mac) to open a pop-up windows, type `registry`

Find and enabled this option `compiler.automake.allow.when.app.running`

4. Spring Boot Run/Debug configuration

To change `On Update action` in the Run/Debug configuration.

On Update action: update classes and resources.



Done. Now, the hot swapping & static files auto reload should be enabled.

---



Follow below simple steps, you will be up and running in less than 2 minutes.

1. Press Ctrl+Shift+A
2. Search for Registry ...
3. scroll and find "compiler.automake.allow.when.app.running" then select the checkbox to make it active.
4. Click close
5. File Menu -> settings ...
6. Expand Build, Execution, Deployment
7. Select Compiler
8. Select checkbox Build project automatically
9. Apply
10. Click Ok

Now stop your application server and then start your application, that's it you will find automatic restart/reload activated when any changes are detected in the project.

## References

[1] [IntelliJ 15, SpringBoot devtools livereload not working](https://stackoverflow.com/questions/33869606/intellij-15-springboot-devtools-livereload-not-working)