

### List 

```scala
dtWhitelistData.Select().Where(Function(x) x.Item("DomainName").ToString.ToLower.Equals(emailSenderHost.ToLower)).ToArray
```
```scala
dtData.AsEnumerable.Where(Function (x) x("CCode").toString.Trim.ToUpper.Equals(strCCFilter.ToUpper)).ToList
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
(from item in lstNewData where item.Contains("3059 Subtotal") or item.Contains("8155 Subtotal")).ToList
```



### DataTable


```scala
customersDT.AsEnumerable().Where(Function (row) row("First Name").ToString().StartsWith("J")).CopyToDataTable
```


### int


```scala
customersDT.AsEnumerable().Min(Function (row) row("First Name").ToString().Length)
```


### DataTable


```scala
if(dtData.RowCount=0,dtData.clone,Result.CopyToDataTable)
```

```scala
String.Join(", ", customersDT.AsEnumerable().Where(Function (row) row.Field(of String)("First Name").Length=4).Select(Function (row) row.Field(Of String)("Email")))
```

```scala
string.Join(Environment.NewLine, customersDT.AsEnumerable().Where(Function (row) row.Field(Of String)("First Name").Length = 4).Select(Function (row) row.Field(of String)("First Name")))
```

```scala
dt_OutPutDataTable_Email.AsEnumerable().Take(7).CopyToDataTable
```


### array


```scala
dt_items.AsEnumerable().Select(Function(x) x.Field(Of String)("name")).Distinct().ToArray()
```

### list


```scala
dt_items.AsEnumerable().Select(Function(x) x.Field(Of String)("name")).Distinct().ToList()
```

```scala
dt_items.AsEnumerable().GroupBy(Function(x) x.Field(Of String)("name")).Where(Function(y) y.Count() > 1).Select(Function(z) z.Key).ToList()
```

```scala
dt_items.AsEnumerable().GroupBy(Function(x) x.Field(Of String)("name")).Where(Function(y) y.Count() > 1).Select(Function(z) z.Key).ToArray()
```

```scala
dt_items.AsEnumerable().GroupBy(Function(i) i.Field(Of String)("name")).Where(Function(g) g.Count() > 1).SelectMany(Function(g) g).CopyToDataTable()
```

```scala
dt_items.AsEnumerable().GroupBy(Function(row) row.Field(Of string)("id")).Select(Function(x) x.First).CopyToDatatable
```

```scala
dt_items.AsEnumerable().GroupBy(Function(i) i.Field(Of String)("name")).Where(Function(g) g.Count() > 1).SelectMany(Function(g) g).CopyToDataTable()
```

```scala
dt_items.AsEnumerable().GroupBy(Function(i) i.Field(Of String)("name")).Where(Function(g) g.Count() = 1).SelectMany(Function(g) g).CopyToDataTable()
```

```scala
dt_items.DefaultView.ToTable(True,"Col1","Col2")
```

```scala
dt_items.AsEnumerable().GroupBy(Function(x) x.Field(Of String)("name")).Where(Function(y) y.Count() = 1).Select(Function(z) z.Key).ToArray()
```

```scala
dt_items.AsEnumerable().GroupBy(Function(x) x.Field(Of String)("name")).Where(Function(y) y.Count() = 1).Select(Function(z) z.Key).ToList()
```

```scala
dt_items.AsEnumerable().GroupBy(Function(i) i.Field(Of String)("name")).Where(Function(g) g.Count() = 1).SelectMany(Function(g) g).CopyToDataTable()
```

```scala
dt_items.AsEnumerable().GroupBy(Function(x) x.Field(Of String)("name")).Where(Function(y) y.Count() > 1).Select(Function(z) z.Key).ToList()
```

```scala
dt_items.AsEnumerable().GroupBy(Function(x) x.Field(Of String)("name")).Where(Function(y) y.Count() > 1).Select(Function(z) z.Key).ToArray()
```

```scala
dt_items.AsEnumerable().GroupBy(Function(i) i.Field(Of String)("name")).Where(Function(g) g.Count() > 1).SelectMany(Function(g) g).CopyToDataTable()
```

```scala
dt_items.AsEnumerable().Select(Function(x) x.Field(Of String)("name")).Distinct().ToArray()
```

```scala
dt_items.AsEnumerable().Select(Function(x) x.Field(Of String)("name")).Distinct().ToList()
```

```scala
dt_items.AsEnumerable().GroupBy(Function(row) row.Field(Of string)("id")).Select(Function(x) x.First).CopyToDatatable
```


### Double


```scala
dt_items.AsEnumerable().Sum(Function(x) Convert.ToDouble(x.Field(Of Object)("id")))
```



### IEnu - DataRow


```scala
customersDT.AsEnumerable.Where(Function (row) row.Field(Of String)("Email").Contains("shamm@sugarwell.org"))
```

```scala
customersDT.AsEnumerable.Where(Function (row) row.Field(Of String)("Email").Contains("shamm@sugarwell.org")).ToList()
```

```scala
dt.AsEnumerable().Where(Function(row) row("ColName").ToString="abc").CopyToDataTable()
```
