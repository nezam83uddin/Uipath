
## StingManipulation 
String Manipulation ([Link.....](https://forum.uipath.com/t/how-to-manipulate-a-part-of-string-split-trim-substring-replace-remove-left-right/140180))


```scala
strPdfText.Split({Environment.NewLine},StringSplitOptions.None)

```
|Variable Type|Syntax|Reason For Uses|
|:----|:----|:----|
|fileinfo_FileName|new FileInfo(ConfigPath).DirectoryName|Deleting all space, comma, tab and new line from String, Deleting all space, comma, tab and new line from String, Deleting all space, comma, tab and new line from String,|







```scala
str_Vaccine = System.Text.RegularExpressions.Regex.Replace(str_Vaccine,"\s+"," ",System.Text.RegularExpressions.RegexOptions.Multiline).Trim
```

```scala
String.Format("*Test_ToC_{0}.csv", in_ProcessDate.ToString("yyMMdd"))
```

```scala
str_Vaccine = String.Join(vbCrLf,str_Vaccine.Split(Environment.NewLine.ToArray,StringSplitOptions.RemoveEmptyEntries))
```

```scala
str_Vaccine = System.Text.RegularExpressions.Regex.Replace(str_Vaccine,"^-"," ",System.Text.RegularExpressions.RegexOptions.Multiline).Trim
```

```scala
str_Vaccine = System.Text.RegularExpressions.Regex.Replace(str_Vaccine,"-$"," ",System.Text.RegularExpressions.RegexOptions.Multiline).Trim
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

# Link


```scala
System.Text.RegularExpressions.Regex.Replace(Test_Data, "[\r?\n]{2,}", vbcrlf).Trim
```


```scala
If(str_MachineName(0).Groups(1).Value IsNot Nothing, str_MachineName(0).Groups(1).Value, " ")
```
