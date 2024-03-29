# DateTime


# Filter different formation of date

```scala
ImmunizationDT= (from row In immunizationdt Order By DateTime.ParseExact(row(0).ToString, "MM/dd/yyyy", System.Globalization.CultureInfo.InvariantCulture) Ascending Select row).CopyToDataTable
```

```scala
ImmunizationDT= (from row In immunizationdt Order By DateTime.ParseExact(row(0).ToString, "M/d/yyyy", System.Globalization.CultureInfo.InvariantCulture) Ascending Select row).CopyToDataTable
```

# Taking 1st 7th row from DataTable
```scala
ImmunizationDT= dt_OutPutDataTable_Email.AsEnumerable().Take(7).CopyToDataTable
```
