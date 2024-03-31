## List
Regular Expressions ([https://regex101.com/r/bSpvIF/1](https://regex101.com/r/bSpvIF/1))


```java
\w{1,}\@\w{1,}\D\w{1,3}
```

### Getting All value after extracting from the web page
```java
"\s*(.*)"
```
### Getting 1st value 
```java
if(Name(0).Groups(1).Value IsNot Nothing, Name(0).Groups(1).Value, " ")
```
### Putting in quotation
```java
If(o_MemberName IsNot Nothing, """"+o_MemberName+"""", """"+" "+"""" )
```
