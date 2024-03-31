
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

### Avoiding Restore Page in Chrome

```java
"C:\Users\"+environment.UserName+"\AppData\Local\Google\Chrome\User Data\Default\Preferences"
```

```java
str_preferenceText.Replace(Chr(34)+"exit_type"+Chr(34)+":"+Chr(34)+"Crashed"+Chr(34),Chr(34)+"exit_type"+Chr(34)+":"+Chr(34)+"Normal"+Chr(34))
```

### create start.vbs to wake up machine
```scala
set wsc = CreateObject("WScript.Shell")
Do
     'Three minutes
     WScript.Sleep(3*60*1000)
     wsc.SendKeys("{F13}")
Loop
```
