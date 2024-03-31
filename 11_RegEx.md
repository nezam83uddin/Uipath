## List
Regular Expressions ([https://regex101.com/r/bSpvIF/1](https://regex101.com/r/bSpvIF/1))


```java
\w{1,}\@\w{1,}\D\w{1,3}
```

### Getting All value after extracting from the web page
```java
IEnu<Match>_last_line_fields="\s*(.*)"
Condition=last_line_fields(2).Value.StartsWith(".")
```
### Getting 1st value 
```java
if(Name(0).Groups(1).Value IsNot Nothing, Name(0).Groups(1).Value, " ")
```
### Putting in quotation
```java
If(o_MemberName IsNot Nothing, """"+o_MemberName+"""", """"+" "+"""" )
```
### Regex | String
```java
str_Vaccine = System.Text.RegularExpressions.Regex.Replace(str_GetTextForCredit,"\s+"," ")
```
```java
str_Vaccine = System.Text.RegularExpressions.Regex.Match(str_GetTextForCredit,"(?<=TOTAL\sCREDITS\*\s)(\d+\.\d+|\.\d+)").Value
```

```java
str_Vaccine = System.Text.RegularExpressions.Regex.Replace(str_Vaccine,"\s+"," ",System.Text.RegularExpressions.RegexOptions.Multiline).Trim
```
```java
str_Vaccine =System.Text.RegularExpressions.Regex.Replace(strPdfText,"\s+"," ",System.Text.RegularExpressions.RegexOptions.Singleline).Trim

```
```java
str_Vaccine = System.Text.RegularExpressions.Regex.Replace(str_Vaccine,"^-"," ",System.Text.RegularExpressions.RegexOptions.Multiline).Trim
```

```java
str_Vaccine = System.Text.RegularExpressions.Regex.Replace(str_Vaccine,"-$"," ",System.Text.RegularExpressions.RegexOptions.Multiline).Trim
```
