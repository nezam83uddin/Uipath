
## List

```scala
new Exception(String.Format("The asset name [{0}] doesn't exist or no access", "ConfigPath"))
```

```scala
new BusinessRuleException(String.Format("The config file [{0}] doesn't exist", ConfigPath))
```


```scala
SystemException IsNot Nothing AndAlso (Config Is Nothing OrElse Convert.ToBoolean(Config("ShouldMarkJobAsFaulted")))
```
