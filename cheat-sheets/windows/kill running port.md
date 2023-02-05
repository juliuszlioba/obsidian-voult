To find <PID> number of running process for port

```shell
netstat -ano | findstr :<PORT>
```

To kill process
```shell
taskkill /PID <PID> /F
```