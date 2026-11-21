# UiPath CSS Selector গাইড

## ১. UiPath-এ লেখার নিয়ম

```xml
<webctrl css-selector='input[name="passwd"]' />
```

এখানে `css-selector`-এর বাইরের quote single (`'`) এবং CSS-এর attribute value-র quote double (`"`)। `Enter the password`-এর মতো মানে স্পেস থাকলে CSS-এ মানটিকে quote-এর মধ্যে রাখুন।

প্রথম কয়েকটি উদাহরণ এই HTML ধরে লেখা:

```html
<form class="username-form">
  <input id="i0118" name="passwd" class="form-control ext-input"
         type="password" aria-label="Enter the password for this account">
</form>
```

পরের কিছু অংশে নিয়ম বোঝাতে `name="user-login"` বা `aria-label="Enter the password"`-এর মতো আলাদা মান ব্যবহার করা হয়েছে। যে পেজে কাজ করবেন, তার আসল attribute value বসান।

## ২. `input`, `#id`, `.class`, `name` ও `aria-label`

- `input` দিলে শুধু `<input>` element খোঁজে। বাদ দিলে যেকোনো tag মিলতে পারে।
- `#i0118` হলো `id="i0118"`-এর সংক্ষিপ্ত রূপ। `[id="i0118"]` দিয়েও একই মান খোঁজা যায়।
- `.username-form` ওই class-যুক্ত element খোঁজে। উদাহরণে এটি `<form>`। `.username-form input` ওই form-এর ভেতরের input খোঁজে।
- `name` ও `aria-label`-এর জন্য `[name="..."]` ও `[aria-label="..."]` লিখুন।
- `#i0118 i` লিখলে CSS ওই ID-যুক্ত element-এর ভেতরে `<i>` tag খোঁজে। ID-তে case উপেক্ষা করতে `[id="I0118" i]` লিখুন। Class-এর জন্য একইভাবে `[class~="FORM-CONTROL" i]` ব্যবহার করুন।

```xml
<webctrl css-selector='#i0118' />
<webctrl css-selector='input#i0118' />
<webctrl css-selector='input[id="i0118"]' />
<webctrl css-selector='input[id="I0118" i]' />
<webctrl css-selector='.username-form' />
<webctrl css-selector='.username-form input' />
<webctrl css-selector='[name="passwd"]' />
<webctrl css-selector='input[aria-label*="Enter the password" i]' />
```

## ৩. OR, AND ও `i` পড়ার নিয়ম

- **OR** — কমা `,` দিয়ে বিকল্প আলাদা করুন। যেকোনো একটি বিকল্প মিললেই element match করে। দুই বিকল্পে দুইটি আলাদা element-ও মিলতে পারে। কমা দিয়ে কোনটি আগে খুঁজবে তা ঠিক হয় না।
- **AND** — একই element-এর শর্ত পাশাপাশি লিখুন, মাঝখানে স্পেস বা কমা ছাড়া। যেমন `input[id="i0118"][name="passwd"]`।
- **`i`** — ওই একটিমাত্র attribute value তুলনার সময় ইংরেজি অক্ষরের বড় ও ছোট হাতের পার্থক্য উপেক্ষা করে। উদ্ধৃত value-র পরে, `]`-এর আগে বসে। পুরো selector-এর জন্য শেষে একবার `i` বসানো যায় না।
- **`i` ছাড়া** — এই উদাহরণের `id`, `name`, `class` ও `aria-label`-এ অক্ষরের case মেলাতে হবে। যেমন `[name="PASSWD"]` দিয়ে `name="passwd"` মিলবে না।
- নিচের প্রতিটি চার লাইনের ব্লকের ক্রম — **১. কোথাও `i` নেই, ২. শুধু প্রথমে `i`, ৩. শুধু দ্বিতীয়টিতে `i`, ৪. দুটোতেই `i`**। প্রতিটি লাইন আলাদা selector।

## ৪. ID ও class একসঙ্গে — `#`, `.` ও `i`

`input#i0118.ext-input` একই input-এর ID ও class দুটোই মেলায়। শুধু একটি class মেলাতে `[class~="ext-input"]` ব্যবহার করা যায়, এমনকি element-এ আরও class থাকলেও।

### OR — ID অথবা class

```xml
<webctrl css-selector='input#i0118, input.ext-input' />
<webctrl css-selector='input[id="I0118" i], input.ext-input' />
<webctrl css-selector='input#i0118, input[class~="EXT-INPUT" i]' />
<webctrl css-selector='input[id="I0118" i], input[class~="EXT-INPUT" i]' />
```

### AND — একই input-এ ID ও class

```xml
<webctrl css-selector='input#i0118.ext-input' />
<webctrl css-selector='input[id="I0118" i].ext-input' />
<webctrl css-selector='input#i0118[class~="EXT-INPUT" i]' />
<webctrl css-selector='input[id="I0118" i][class~="EXT-INPUT" i]' />
```

## ৫. `=` — হুবহু মিল

`[name="passwd"]` দিয়ে `name="passwd"` মিলবে। `name="my-passwd"` মিলবে না।

### OR — ID অথবা name

```xml
<webctrl css-selector='input[id="i0118"], input[name="passwd"]' />
<webctrl css-selector='input[id="I0118" i], input[name="passwd"]' />
<webctrl css-selector='input[id="i0118"], input[name="PASSWD" i]' />
<webctrl css-selector='input[id="I0118" i], input[name="PASSWD" i]' />
```

### AND — একই input-এ ID ও name

```xml
<webctrl css-selector='input[id="i0118"][name="passwd"]' />
<webctrl css-selector='input[id="I0118" i][name="passwd"]' />
<webctrl css-selector='input[id="i0118"][name="PASSWD" i]' />
<webctrl css-selector='input[id="I0118" i][name="PASSWD" i]' />
```

## ৬. `*=` — মানের যেকোনো জায়গায় লেখাটি থাকলে

`[name*="pass"]` দিয়ে `name="my-passwd"` মিলবে। খোঁজা অক্ষরগুলো পরপর থাকতে হবে।

### OR — name-এ `pass` অথবা aria-label-এ `password`

```xml
<webctrl css-selector='input[name*="pass"], input[aria-label*="password"]' />
<webctrl css-selector='input[name*="PASS" i], input[aria-label*="password"]' />
<webctrl css-selector='input[name*="pass"], input[aria-label*="PASSWORD" i]' />
<webctrl css-selector='input[name*="PASS" i], input[aria-label*="PASSWORD" i]' />
```

### AND — দুটো attribute-এই খোঁজা অংশ আছে

```xml
<webctrl css-selector='input[name*="pass"][aria-label*="password"]' />
<webctrl css-selector='input[name*="PASS" i][aria-label*="password"]' />
<webctrl css-selector='input[name*="pass"][aria-label*="PASSWORD" i]' />
<webctrl css-selector='input[name*="PASS" i][aria-label*="PASSWORD" i]' />
```

## ৭. `^=` — মানের শুরুতে লেখাটি থাকলে

`[aria-label^="Enter the password"]` দিয়ে `aria-label="Enter the password for this account"` মিলবে।

### OR — name `pass` দিয়ে শুরু অথবা aria-label ওই বাক্যাংশ দিয়ে শুরু

```xml
<webctrl css-selector='input[name^="pass"], input[aria-label^="Enter the password"]' />
<webctrl css-selector='input[name^="PASS" i], input[aria-label^="Enter the password"]' />
<webctrl css-selector='input[name^="pass"], input[aria-label^="ENTER THE PASSWORD" i]' />
<webctrl css-selector='input[name^="PASS" i], input[aria-label^="ENTER THE PASSWORD" i]' />
```

### AND — দুটো attribute-এর শুরুই মেলে

```xml
<webctrl css-selector='input[name^="pass"][aria-label^="Enter the password"]' />
<webctrl css-selector='input[name^="PASS" i][aria-label^="Enter the password"]' />
<webctrl css-selector='input[name^="pass"][aria-label^="ENTER THE PASSWORD" i]' />
<webctrl css-selector='input[name^="PASS" i][aria-label^="ENTER THE PASSWORD" i]' />
```

## ৮. `$=` — মানের শেষে লেখাটি থাকলে

`[name$="wd"]` দিয়ে `name="passwd"` মিলবে। `[aria-label$="password"]` দিয়ে `aria-label="Enter the password"` মিলবে। শেষে `for this account` থাকলে ওই aria-label শর্তটি মিলবে না।

### OR — name `wd` দিয়ে শেষ অথবা aria-label `password` দিয়ে শেষ

```xml
<webctrl css-selector='input[name$="wd"], input[aria-label$="password"]' />
<webctrl css-selector='input[name$="WD" i], input[aria-label$="password"]' />
<webctrl css-selector='input[name$="wd"], input[aria-label$="PASSWORD" i]' />
<webctrl css-selector='input[name$="WD" i], input[aria-label$="PASSWORD" i]' />
```

### AND — দুটো attribute-এর শেষই মেলে

```xml
<webctrl css-selector='input[name$="wd"][aria-label$="password"]' />
<webctrl css-selector='input[name$="WD" i][aria-label$="password"]' />
<webctrl css-selector='input[name$="wd"][aria-label$="PASSWORD" i]' />
<webctrl css-selector='input[name$="WD" i][aria-label$="PASSWORD" i]' />
```

## ৯. `~=` — স্পেস দিয়ে আলাদা করা পুরো শব্দ

`[class~="ext-input"]` দিয়ে `class="form-control ext-input"` মিলবে। `class="ext-input-large"` মিলবে না। `aria-label="Enter the password for this account"`-এ `password` আলাদা শব্দ, তাই `[aria-label~="password"]` মিলবে।

### OR — class-এ `ext-input` অথবা aria-label-এ `password`

```xml
<webctrl css-selector='input[class~="ext-input"], input[aria-label~="password"]' />
<webctrl css-selector='input[class~="EXT-INPUT" i], input[aria-label~="password"]' />
<webctrl css-selector='input[class~="ext-input"], input[aria-label~="PASSWORD" i]' />
<webctrl css-selector='input[class~="EXT-INPUT" i], input[aria-label~="PASSWORD" i]' />
```

### AND — দুটো attribute-এই পুরো শব্দ মেলে

```xml
<webctrl css-selector='input[class~="ext-input"][aria-label~="password"]' />
<webctrl css-selector='input[class~="EXT-INPUT" i][aria-label~="password"]' />
<webctrl css-selector='input[class~="ext-input"][aria-label~="PASSWORD" i]' />
<webctrl css-selector='input[class~="EXT-INPUT" i][aria-label~="PASSWORD" i]' />
```

## ১০. `|=` — হুবহু মান অথবা তার ঠিক পরে হাইফেন

`[name|="user"]` দিয়ে `name="user"` ও `name="user-login"` মিলবে। `name="username"` মিলবে না। নিচে নমুনা হিসেবে `name="user-login"` ও `id="login-field"` ধরা হয়েছে।

### OR — name `user`/`user-…` অথবা ID `login`/`login-…`

```xml
<webctrl css-selector='input[name|="user"], input[id|="login"]' />
<webctrl css-selector='input[name|="USER" i], input[id|="login"]' />
<webctrl css-selector='input[name|="user"], input[id|="LOGIN" i]' />
<webctrl css-selector='input[name|="USER" i], input[id|="LOGIN" i]' />
```

### AND — দুটো attribute-এই হুবহু মান বা হাইফেনসহ শুরু মেলে

```xml
<webctrl css-selector='input[name|="user"][id|="login"]' />
<webctrl css-selector='input[name|="USER" i][id|="login"]' />
<webctrl css-selector='input[name|="user"][id|="LOGIN" i]' />
<webctrl css-selector='input[name|="USER" i][id|="LOGIN" i]' />
```

## ১১. `[attribute]` — attribute আছে কি না

`[aria-label]` দিয়ে `aria-label=""`-ও মিলবে, কারণ attribute-টি আছে। এই শর্তে `i` বসে না, কারণ কোনো value তুলনা হচ্ছে না। পাশের value শর্তে `i` ব্যবহার করা যায়।

```xml
<webctrl css-selector='input[name]' />
<webctrl css-selector='input[aria-label]' />
<webctrl css-selector='input[name], input[aria-label]' />
<webctrl css-selector='input[name][aria-label]' />
<webctrl css-selector='input[aria-label], input[name="passwd"]' />
<webctrl css-selector='input[aria-label], input[name="PASSWD" i]' />
<webctrl css-selector='input[aria-label][name="passwd"]' />
<webctrl css-selector='input[aria-label][name="PASSWD" i]' />
```

## ১২. `s` — স্পষ্টভাবে case মেলানোর flag

CSS-এ `s` মানে ওই attribute value-র বড় ও ছোট হাতের অক্ষর আলাদা ধরা। Chrome/UiPath-এ `s` ব্যবহারের আগে Validate করুন, কারণ সমর্থন পরিবেশভেদে বদলাতে পারে। `id`, `name` ও `aria-label`-এর ক্ষেত্রে `s` ছাড়াই ডিফল্ট case-sensitive মিল ব্যবহার করতে পারেন। একই `[...]`-এ `s` এবং `i` একসঙ্গে বসে না, তবে আলাদা শর্তে একটি করে ব্যবহার করা যায়।

এখানে চার লাইনের ক্রম — **১. `s` ও `s`, ২. `i` ও `s`, ৩. `s` ও `i`, ৪. `i` ও `i`**।

### OR — name অথবা ID

```xml
<webctrl css-selector='input[name="passwd" s], input[id="i0118" s]' />
<webctrl css-selector='input[name="PASSWD" i], input[id="i0118" s]' />
<webctrl css-selector='input[name="passwd" s], input[id="I0118" i]' />
<webctrl css-selector='input[name="PASSWD" i], input[id="I0118" i]' />
```

### AND — একই input-এ name ও ID

```xml
<webctrl css-selector='input[name="passwd" s][id="i0118" s]' />
<webctrl css-selector='input[name="PASSWD" i][id="i0118" s]' />
<webctrl css-selector='input[name="passwd" s][id="I0118" i]' />
<webctrl css-selector='input[name="PASSWD" i][id="I0118" i]' />
```

## ১৩. তিনটি attribute একসঙ্গে — ID, name ও aria-label

এখানে একই selector-এ `=`, `*=` ও `^=` মেশানো হয়েছে। প্রতিটি ব্লকে `i`-এর আটটি অবস্থান আছে।

### OR — যেকোনো একটি শর্ত মিললেই

```xml
<webctrl css-selector='input[id="i0118"], input[name*="pass"], input[aria-label^="Enter the password"]' />
<webctrl css-selector='input[id="I0118" i], input[name*="pass"], input[aria-label^="Enter the password"]' />
<webctrl css-selector='input[id="i0118"], input[name*="PASS" i], input[aria-label^="Enter the password"]' />
<webctrl css-selector='input[id="i0118"], input[name*="pass"], input[aria-label^="ENTER THE PASSWORD" i]' />
<webctrl css-selector='input[id="I0118" i], input[name*="PASS" i], input[aria-label^="Enter the password"]' />
<webctrl css-selector='input[id="I0118" i], input[name*="pass"], input[aria-label^="ENTER THE PASSWORD" i]' />
<webctrl css-selector='input[id="i0118"], input[name*="PASS" i], input[aria-label^="ENTER THE PASSWORD" i]' />
<webctrl css-selector='input[id="I0118" i], input[name*="PASS" i], input[aria-label^="ENTER THE PASSWORD" i]' />
```

### AND — একই input-এ তিনটি শর্তই মিলতে হবে

```xml
<webctrl css-selector='input[id="i0118"][name*="pass"][aria-label^="Enter the password"]' />
<webctrl css-selector='input[id="I0118" i][name*="pass"][aria-label^="Enter the password"]' />
<webctrl css-selector='input[id="i0118"][name*="PASS" i][aria-label^="Enter the password"]' />
<webctrl css-selector='input[id="i0118"][name*="pass"][aria-label^="ENTER THE PASSWORD" i]' />
<webctrl css-selector='input[id="I0118" i][name*="PASS" i][aria-label^="Enter the password"]' />
<webctrl css-selector='input[id="I0118" i][name*="pass"][aria-label^="ENTER THE PASSWORD" i]' />
<webctrl css-selector='input[id="i0118"][name*="PASS" i][aria-label^="ENTER THE PASSWORD" i]' />
<webctrl css-selector='input[id="I0118" i][name*="PASS" i][aria-label^="ENTER THE PASSWORD" i]' />
```

## ১৪. `username`, `user name` ও `user  name`

`i` অক্ষরের case উপেক্ষা করে। স্পেসের সংখ্যা বদলায় না। শূন্য, এক বা দুইটি স্পেসের জন্য প্রতিটি মান OR দিয়ে লিখুন।

```xml
<webctrl css-selector='input[name="username"], input[name="user name"], input[name="user  name"]' />
<webctrl css-selector='input[name="USERNAME" i], input[name="USER NAME" i], input[name="USER  NAME" i]' />
<webctrl css-selector='input[name*="username"], input[name*="user name"], input[name*="user  name"]' />
<webctrl css-selector='input[name*="USERNAME" i], input[name*="USER NAME" i], input[name*="USER  NAME" i]' />
<webctrl css-selector='input[name*="user" i][name*="name" i]' />
```

শেষ উদাহরণে `user` ও `name` দুটো অংশই থাকতে হবে। এটি তাদের ক্রম বা মাঝের অক্ষর যাচাই করে না, তাই `name-user` এবং `user-other-name`-ও মিলবে।

## ১৫. দ্রুত মনে রাখুন

| CSS | অর্থ |
|---|---|
| `input` | শুধু `<input>` tag |
| `#i0118` | ওই ID-যুক্ত element |
| `.ext-input` | ওই class-যুক্ত element |
| `[name]` | `name` attribute আছে |
| `[name="passwd"]` | হুবহু মান |
| `[name*="pass"]` | মানের যেকোনো জায়গায় |
| `[name^="pass"]` | মানের শুরুতে |
| `[name$="wd"]` | মানের শেষে |
| `[class~="ext-input"]` | স্পেস দিয়ে আলাদা করা পুরো শব্দ |
| `[name\|="user"]` | `user` অথবা `user-` দিয়ে শুরু |
| `[name="PASSWD" i]` | এই একটি শর্তে case উপেক্ষা |
| `[name="passwd" s]` | এই একটি শর্তে case মেলাতে হবে, যেখানে `s` সমর্থিত |
| `A, B` | OR — A অথবা B |
| `[a="x"][b="y"]` | AND — একই element-এ দুই শর্ত |
| `A B` | A-এর ভেতরের B |

UiPath UI Explorer-এ একটি selector লাইন বসিয়ে **Validate → Highlight** করুন। এতে কোন element ধরা পড়ছে দেখতে পাবেন।
