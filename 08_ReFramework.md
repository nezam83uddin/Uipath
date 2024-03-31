# ReFramwork

### For Using in the Condition in state
```scala
Successfull = SystemException is Nothing And BusinessException is Nothing
```

```scala
Exception = SystemException isNot Nothing or BusinessException IsNot Nothing
```

```scala
Log Message = if(SystemException IsNot Nothing, "System exception at initialization: " + SystemException.Message + " at Source: " + SystemException.Source, "Business exception at initialization: " + BusinessException.Message + " at Source: " + BusinessException.Source)
```

### For Browser or Report
```scala
in_Config.Keys.Contains("Browser_Name")
DirectCast(in_Config("Browser_Eport"),Browser)
Config.Keys.Contains("dt_ReportTemplate") And Config.Keys.Contains("OutputPath") And Config.Keys.Contains("FileFourReport")
DirectCast(Config("dt_ReportTemplate"),DataTable)
```



### For Single Transaction (GetTransaction Data)

|Variable Type|Syntax|
|:----|:----|
|Condtion|IsNothing(out_TransactionData) or out_TransactionData.RowCount = 0|
|Condtion|io_TransactionData.RowCount >= in_TransactionNumber|
|o_str_TransactionItem|io_TransactionData.Rows(in_TransactionNumber-1).Item("Trans1").ToString|
|o_str_TransactionItemRequire|Convert.ToBoolean(io_TransactionData.Rows(in_TransactionNumber-1).Item("IsRequired"))|

