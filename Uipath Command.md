# Uipath Assistance


## Place Uipath Assistance in Startup

```scala
shell:startup
```

```scala
%appdata%
```

```scala
UIPATH_USER_SERVICE_PATH = C:\Users\Sajib\AppData\Local\Programs\UiPath\Studio\UiPath.Service.UserHost.exe
```

## start.vbs 
```scala
set wsc = CreateObject("WScript.Shell")
Do
     'Three minutes
     WScript.Sleep(3*60*1000)
     wsc.SendKeys("{F13}")
Loop
```
