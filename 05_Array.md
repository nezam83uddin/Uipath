### arr_Rows


```scala
(From row In dtOutput.Select("[ColoumName]='RowValue'")
```

```scala
Where CDate(row("Date").ToString) >= Date.Today.AddDays(-11) And CDate(row("Date").ToString) <= Date.Today.AddDays(-5)
```

```scala
Select row).ToArray
```
### str_Row


```scala
rows.Sum(Function (x) If(Double.TryParse(x.item("Actual_Amount").ToString, Nothing), Double.Parse(x.Item("Actual_Amount").ToString), 0))
```

```scala
Dt.Rows(2).itemArray
```



### groupRows


```scala
(From r In dtConfig.Select()
```

```scala
Group r By rowitem=New With { Key.ROW_NO = r.Item("ROW_NO") } Into Group
```

```scala
Select Group.ToArray).ToArray()
```

```scala
targetLine.ToLower.Contains(parserKeywords(index).ToLower)
```
