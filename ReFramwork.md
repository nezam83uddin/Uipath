# About 


## Condition in state
```scala
Successfull = SystemException is Nothing And BusinessException is Nothing
```

```scala
Exception = SystemException isNot Nothing or BusinessException IsNot Nothing
```

```scala
Log Message = if(SystemException IsNot Nothing, "System exception at initialization: " + SystemException.Message + " at Source: " + SystemException.Source, "Business exception at initialization: " + BusinessException.Message + " at Source: " + BusinessException.Source)
```
