# Windows Process Management Note

## Kill Processes

### Kill Specific Port Processes

```
netstat -ano | findstr :<port>
tskill <PID>
```

