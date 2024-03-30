
### Place Uipath Assistance in Startup

```scala
shell:startup
```
### Checking Uipath log
```scala
%appdata%
```


### Setting for Services
```scala
Services
```
```scala
UIPATH_USER_SERVICE_PATH = C:\Users\Sajib\AppData\Local\Programs\UiPath\Studio\UiPath.Service.UserHost.exe
```

### creat start.vbs to wake up machine
```scala
set wsc = CreateObject("WScript.Shell")
Do
     'Three minutes
     WScript.Sleep(3*60*1000)
     wsc.SendKeys("{F13}")
Loop
```
