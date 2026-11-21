# UiPath CSS Selector গাইড

এই উদাহরণগুলো ছবির ইনপুটের attribute ধরে লেখা: `id="i0118"`, `name="passwd"`, এবং `aria-label="Enter the password for ..."`। CSS-এর ভেতরের attribute value-গুলোতে double quote ব্যবহার করা হয়েছে। UiPath-এর `<webctrl>`-এ বাইরের quote single রাখা হয়েছে, যাতে ভেতরের double quote ঠিক থাকে।

## `input` লিখলে কী হয়?

- `#i0118` — যে কোনো tag-এর `id="i0118"` element খোঁজে।
- `input#i0118` — শুধু `input` tag-এর `id="i0118"` খোঁজে।
- `input` বাদ দিলেও চলে, যদি ID-টি পেজে unique হয়। `input` রাখলে selector-টি শুধু input element খোঁজে।

```css
#i0118
input#i0118
```

## ID দিয়ে খোঁজা

`#` হলো ID-এর সংক্ষিপ্ত চিহ্ন। ID পুরোপুরি মেলাতে:

```css
#i0118
```

Attribute selector দিয়েও একই ID লেখা যায়:

```css
[id="i0118"]
```

শুধু input tag-এর মধ্যে খুঁজতে:

```css
input[id="i0118"]
```

## name দিয়ে খোঁজা

`name` attribute-এর জন্য `#` বা `.`-এর মতো সংক্ষিপ্ত চিহ্ন নেই। তাই `[name="..."]` লিখতে হয়। `=` মানে মানটি হুবহু মিলবে:

```css
[name="passwd"]
input[name="passwd"]
```

এখানে `input` রাখলে কেবল input element-এ খোঁজে। বাদ দিলে যে কোনো tag-এর `name="passwd"` মিলতে পারে।

## aria-label দিয়ে খোঁজা

`*=` মানে attribute-এর মানের মধ্যে নির্দিষ্ট লেখাটি থাকলেই মিলবে। তাই পুরো aria-label না লিখে এর একটি স্থায়ী অংশ ব্যবহার করা যায়:

```css
input[aria-label*="Enter the password" i]
```

## `i`-এর মানে ও অবস্থান

`i` ওই একটি attribute condition-এ ইংরেজি অক্ষরের uppercase/lowercase পার্থক্য উপেক্ষা করে। এটি closing `]`-এর আগে, উদ্ধৃত মানের পরে বসে। এটি global নয়; যে condition case-insensitive করতে চান, তার ভেতরে আলাদা করে `i` দিতে হবে।

```css
input[name="PASSWD" i]
input[aria-label*="ENTER THE PASSWORD" i]
```

`i` না থাকলে attribute value case-sensitive থাকে। যেমন `[name="passwd"]` আর `[name="PASSWD"]` আলাদা মান।

একই selector-এ একাধিক attribute case-insensitive করতে হলে প্রতিটিতে `i` দিন:

```css
input[id="i0118" i][name="passwd" i][aria-label*="Enter the password" i]
```

শেষে একবার `i` লিখে সব condition-এ প্রয়োগ করা যায় না।

## OR: যেকোনো একটি শর্ত মিললেই

কমা `,` হলো OR। নিচের তিনটির যেকোনো একটি মিলে গেলে element select হবে:

```xml
<webctrl css-selector='input#i0118, input[name="passwd"], input[aria-label*="Enter the password" i]' />
```

## AND: একই input-এ সব শর্ত মিলতে হবে

একই selector-এ condition-গুলো পাশাপাশি লিখুন; কমা দেবেন না:

```xml
<webctrl css-selector='input[id="i0118"][name="passwd"][aria-label*="Enter the password" i]' />
```

## দ্রুত মনে রাখুন

| লেখা | অর্থ |
|---|---|
| `#i0118` | `id="i0118"` |
| `.username-form` | `class="username-form"` |
| `[name="passwd"]` | `name` হুবহু `passwd` |
| `[aria-label*="Enter the password" i]` | aria-label-এ ওই phrase আছে; case উপেক্ষা করে |
| `A, B` | OR: A অথবা B |
| `A[B]` | AND: A এবং B একই element-এ |
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
