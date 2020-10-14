# Windows Process Management Note

## Kill Processes by PID and Name

```
tasklist
tasklist | more
taskkill /F /PID <pid>
taskkill /IM "<ProcessName>" /F
```



## Kill Processes by Port

```
netstat -ano | findstr :<port>
tskill <PID>
```

