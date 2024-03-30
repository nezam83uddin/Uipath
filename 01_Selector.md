## Selector
Fuzzy Selectors Video  ([https://youtu.be/1pYN3q4n_lU?t=422](https://youtu.be/1pYN3q4n_lU?t=422))
### Title
```java
title='abc*' casesensitive:title='false' />
```
### CSS Selector
```java
css-selector='span[uipath_custom_id="12"]' 
```

### Fuzzy Selector
```java
aaname='Monitoring' matching:aaname='fuzzy' fuzzylevel:aaname='0.8'
```
```java
innerText='{{in_str_Name}}' matching:innerText='fuzzy' fuzzylevel:innerText='0.8' 
```
### RegEx
```java
innerText='^Monitoring$' matching:innerText='regex' 
```

