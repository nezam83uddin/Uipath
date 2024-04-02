
## StingManipulation 
String Manipulation ([Link.....](https://forum.uipath.com/t/how-to-manipulate-a-part-of-string-split-trim-substring-replace-remove-left-right/140180))


### Removing Special Character 
```scala
System.Text.RegularExpressions.Regex.Replace(variable, "[^a-z A-Z 0-9]", "")

```
### Removing white spaces, tab and newline and keeping in the single line
```scala
Regex.Replace(str_Name,"\s","")

```


```scala
strPdfText.Split({Environment.NewLine},StringSplitOptions.None)
```


### Adding Leading Zero

```scala
CInt("".ToString).ToString("000000000")

```
```scala
CurrentRow.Item("str_Name").ToString.PadLeft(9,"0"c)

```

### String Manipulation


```scala
str_GetTextForCredit.Substring(str_GetTextForCredit.LastIndexOf("TOTAL CREDITS")).Replace(",","")
```

```scala
strPdfText.Split({Environment.NewLine},StringSplitOptions.None)
```



### String Manipulation


```scala
String.Format("*Test_ToC_{0}.csv", in_ProcessDate.ToString("yyMMdd"))
```
```scala
Split(Dr, "*** GRAND TOTALS ***")(1)
```

```java
str_Vaccine = String.Join(vbCrLf,str_Vaccine.Split(Environment.NewLine.ToArray,StringSplitOptions.RemoveEmptyEntries))
```


```scala
str_DateField = split(str_RowText,environment.newline)(0)
```

```scala
str_RowText = string.join(environment.newline,CurrentRow.ItemArray)
```

```scala
arrStrSplit.Reverse.ToArray
```

```scala
(from item in arrStrSplit where Not item.Contains("Page")).ToArray
```

```scala
(from item in arrStrSplit where Not String.IsNullOrWhiteSpace(item.Trim)).ToArray
```

```scala
String.Join(" ", regexMatch.Cast(Of match).Select(function(d) d.ToString).ToArray)
```

```scala
(from item in lstNewData where item.Contains("3059 Subtotal") or item.Contains("8155 Subtotal")).ToList
```

```scala
String.Join(Environment.NewLine,lstNewData.ToArray)
```

```scala
split(PDF_Data,environment.NewLine).ToList
```

```scala
split(PDF_Data,environment.NewLine).Reverse
```

```scala
split(line.ToString,"Account")(1).Replace("Batch Number","")
```

```scala
String.Format("Reading email subject - [{0}]", in_TransactionItem.Subject)
```

```scala
string.format("{0}\{1}\",Config("ReportFolder").ToString.Trim, "ExceptionScreenshots")
```

```scala
System.Text.RegularExpressions.Regex.Replace(str_RowText,"\s+"," ",System.Text.RegularExpressions.RegexOptions.Multiline).Trim
```

