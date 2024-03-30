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

### For GetTransaction Data

|Variable Type|Syntax|
|:----|:----|
|Condtion|IsNothing(out_TransactionData) or out_TransactionData.RowCount = 0|
|Condtion|io_TransactionData.RowCount >= in_TransactionNumber|
|o_str_TransactionItem|io_TransactionData.Rows(in_TransactionNumber-1).Item("Trans1").ToString|
|o_str_TransactionItemRequire|Convert.ToBoolean(io_TransactionData.Rows(in_TransactionNumber-1).Item("IsRequired"))|

