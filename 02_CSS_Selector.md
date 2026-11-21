
## CSS Attribute Selector: `name`

### `=` — হুবহু মিল

```css
input[name="username"]
```

উদাহরণ: `<input name="username">` মিলবে।

### `*=` — মানের যেকোনো অংশে লেখাটি থাকলে মিল

```css
input[name*="username"]
```

উদাহরণ: `<input name="login-username-field">` মিলবে, কারণ `username` মাঝখানে আছে।

### `$=` — মানের শেষে লেখাটি থাকলে মিল

```css
input[name$="username"]
```

উদাহরণ: `<input name="login-username">` মিলবে, কারণ মানটি `username` দিয়ে শেষ হয়েছে।

### `i` — বড়-ছোট হাতের পার্থক্য উপেক্ষা

```css
input[name*="username" i]
```

উদাহরণ: `<input name="LOGIN-USERNAME-FIELD">` মিলবে, কারণ `i` অক্ষরের case উপেক্ষা করে।

### UiPath selector

```xml
<webctrl css-selector='input[name="username"], input[name*="username" i], input[name$="username" i]' />
```

কমা `,` হলো OR: যেকোনো একটি শর্ত মিললেই ইনপুটটি match হবে।


### CSS Selector
```java
css-selector='span[uipath_custom_id="12"]' 
```

### UiPath Or operator
```java
তফাত হলো, Or হলে কমা থাকবে।
<webctrl css-selector='input[id="id1"], input[name*="id2" i]' casesensitive:css-selector='false' />
<webctrl css-selector='input[id=&quot;id1&quot;], input[name*=&quot;id2&quot; i]' casesensitive:css-selector='false' />
```

### UiPath And operator
```java
তফাত হলো, And হলে কমা থাকবে না।
<webctrl css-selector='input[id="username"][name="username"]' casesensitive:css-selector='false' />
<webctrl css-selector='input[id=&quot;id1&quot;][name=&quot;id2&quot;]' casesensitive:css-selector='false' />
```


# CSS Selector

|tagName[attributename=attributeValue]|
|:----|
|Example 1: input[id=email]|
|Example 2: input[name=email][type=text]|
|css=input[name=email][type=text]|
|1. '^' symbol, represents the starting text in a string.|
|2. '$' symbol represents the ending text in a string.|
|3. '*' symbol represents contains text in a string.|
|a:nth-of-type(2)[class='put class value']|
|button:nth-of-type(2).js-submit|
|form>label>input[id=PersistentCookie]|
|div[class$=Error i]|
|<webctrl aaname='First name:' css-selector='label:nth-of-type(4)' />|

<webctrl css-selector='input[id="id1"], input[name*="id2" i]' />
 <input
      type="text"
      id="id3"
      name="id2"
      placeholder="Enter your username"
      aria-label="usernames"
<webctrl css-selector='input[id="id1"], input[name*="id2" i]' />




### CSS Selector Link
https://www.seleniumeasy.com/selenium-tutorials/css-selectors-tutorial-for-selenium-with-examples
### CSS Selector Link
https://www.swtestacademy.com/css-selenium/#:~:text=13)%20Using%20*%3Alast%2Dof,child%20of%20the%20parent%20tag.&text=Example-,Syntax%3A%20.,parent%20tag%20%E2%80%9Cul%E2%80%9D.)
### CSS Selector Link
https://developer.mozilla.org/en-US/docs/Web/CSS/:nth-last-child
### CSS Selector Link
https://youtu.be/1pYN3q4n_lU?t=423
### CSS Selector Link
https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_win_open
