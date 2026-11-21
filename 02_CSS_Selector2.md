
# UiPath CSS Selector গাইড

প্রতিটি কোড ব্লকে একটি selector আছে। Markdown ফাইলটি GitHub-এ খুললে একবারে একটি selector কপি করা যাবে। UiPath-এর `css-selector`-এ বাইরে single quote এবং CSS attribute value-তে double quote রাখা হয়েছে।

প্রথম উদাহরণগুলোর নমুনা input-এ `id="i0118"`, `name="passwd"`, `class="form-control ext-input"` এবং `aria-label="Enter the password for this account"` আছে। `username-form` হলো তার parent form-এর class। অন্য উদাহরণে নিয়ম শেখাতে আলাদা নমুনা মান ব্যবহার করা হয়েছে।

## ID দিয়ে খোঁজা

`#` হলো `id`-এর সংক্ষিপ্ত রূপ। `#i0118 i` লিখলে ওই ID-র ভেতরের `<i>` tag খোঁজে। ID-এর মানে case উপেক্ষা করতে `[id="..." i]` লিখুন।

**যেকোনো tag-এর ID**

```xml
<webctrl css-selector='#i0118' />
```

**শুধু input-এর ID**

```xml
<webctrl css-selector='input#i0118' />
```

**Attribute দিয়ে ID**

```xml
<webctrl css-selector='[id="i0118"]' />
```

**শুধু input-এর ID, attribute দিয়ে**

```xml
<webctrl css-selector='input[id="i0118"]' />
```

**ID হুবহু মেলান, case উপেক্ষা করে**

```xml
<webctrl css-selector='input[id="I0118" i]' />
```

**ID-এর শুরু মেলান**

```xml
<webctrl css-selector='input[id^="i01"]' />
```

**ID-এর শেষ মেলান**

```xml
<webctrl css-selector='input[id$="118"]' />
```

**ID-এর ভেতরের অংশ মেলান**

```xml
<webctrl css-selector='input[id*="011"]' />
```

## name দিয়ে খোঁজা

`name`-এর জন্য `#` বা `.`-এর মতো সংক্ষিপ্ত চিহ্ন নেই। `[name="..."]` ব্যবহার করুন। শুরুতে `input` লিখলে খোঁজ শুধু `<input>` tag-এর মধ্যে সীমিত হয়।

**যেকোনো tag-এ হুবহু name**

```xml
<webctrl css-selector='[name="passwd"]' />
```

**শুধু input-এ হুবহু name**

```xml
<webctrl css-selector='input[name="passwd"]' />
```

**হুবহু name, case উপেক্ষা করে**

```xml
<webctrl css-selector='input[name="PASSWD" i]' />
```

**name-এর যেকোনো অংশে**

```xml
<webctrl css-selector='input[name*="pass"]' />
```

**name-এর শুরুতে**

```xml
<webctrl css-selector='input[name^="pass"]' />
```

**name-এর শেষে**

```xml
<webctrl css-selector='input[name$="wd"]' />
```

**name attribute আছে**

```xml
<webctrl css-selector='input[name]' />
```

## Class দিয়ে খোঁজা

`.` হলো class-এর সংক্ষিপ্ত রূপ। Element-এ একাধিক class থাকতে পারে। `[class~="ext-input"]` তালিকার একটি পুরো class মেলায়। `[class="..."]` পুরো class attribute হুবহু মেলায়।

**Class দিয়ে form**

```xml
<webctrl css-selector='.username-form' />
```

**শুধু form tag-এ class**

```xml
<webctrl css-selector='form.username-form' />
```

**ওই form-এর ভেতরের input**

```xml
<webctrl css-selector='.username-form input' />
```

**input-এর নিজের class**

```xml
<webctrl css-selector='input.ext-input' />
```

**একটি পুরো class-এর নাম**

```xml
<webctrl css-selector='input[class~="ext-input"]' />
```

**একটি পুরো class, case উপেক্ষা করে**

```xml
<webctrl css-selector='input[class~="EXT-INPUT" i]' />
```

**একই input-এ দুইটি class**

```xml
<webctrl css-selector='input.form-control.ext-input' />
```

## aria-label দিয়ে খোঁজা

পর্দায় লেবেল বদলালেও তার স্থায়ী অংশ ব্যবহার করা যায়। `aria-label="Enter the password for this account"` থাকলে `^="Enter the password"` বা `*="Enter the password"` মিলবে। শুধু ওই বাক্যাংশ দিয়ে `=` মিলবে যখন সেটিই পুরো মান।

**পুরো aria-label হুবহু**

```xml
<webctrl css-selector='input[aria-label="Enter the password"]' />
```

**পুরো মান, case উপেক্ষা করে**

```xml
<webctrl css-selector='input[aria-label="ENTER THE PASSWORD" i]' />
```

**aria-label-এর যেকোনো অংশে**

```xml
<webctrl css-selector='input[aria-label*="Enter the password"]' />
```

**aria-label যেটি দিয়ে শুরু, case উপেক্ষা করে**

```xml
<webctrl css-selector='input[aria-label^="ENTER THE PASSWORD" i]' />
```

**aria-label যেটি দিয়ে শেষ**

```xml
<webctrl css-selector='input[aria-label$="this account"]' />
```

**আলাদা পুরো শব্দ**

```xml
<webctrl css-selector='input[aria-label~="password"]' />
```

**aria-label attribute আছে**

```xml
<webctrl css-selector='input[aria-label]' />
```

## আরও attribute ও CSS চিহ্ন

`type`, `placeholder`, `data-testid`, `role`, `href`, `title` ও `for`-এর জন্য সাধারণ `[attribute="value"]` নিয়ম ব্যবহার করুন। Attribute ও তার মান পেজের HTML-এ থাকতে হবে। নিচের মানগুলো নমুনা। `:checked` এবং `:disabled` হলো element-এর অবস্থা বোঝানোর আলাদা CSS syntax।

**Input-এর ধরন**

```xml
<webctrl css-selector='input[type="password"]' />
```

**Placeholder**

```xml
<webctrl css-selector='input[placeholder="Password"]' />
```

**Data attribute**

```xml
<webctrl css-selector='[data-testid="password-field"]' />
```

**HTML-এ লেখা role**

```xml
<webctrl css-selector='[role="textbox"]' />
```

**Link-এর href-এর শেষ**

```xml
<webctrl css-selector='a[href$="/login"]' />
```

**Title-এর অংশ**

```xml
<webctrl css-selector='[title*="Sign in" i]' />
```

**ID-র সঙ্গে যুক্ত HTML label**

```xml
<webctrl css-selector='label[for="i0118"]' />
```

**iframe-এর title**

```xml
<webctrl css-selector='iframe[title="Sign in"]' />
```

**Tick দেওয়া checkbox**

```xml
<webctrl css-selector='input[type="checkbox"]:checked' />
```

**Disabled button**

```xml
<webctrl css-selector='button:disabled' />
```

## OR, AND ও case

- **OR** — কমা দিয়ে বিকল্প আলাদা করুন। যেকোনো একটি শর্ত মিললেই element match করবে। একাধিক element-ও মিলতে পারে। কমা অগ্রাধিকার ঠিক করে না।
- **AND** — একই element-এর শর্ত পাশাপাশি লিখুন, মাঝখানে স্পেস বা কমা ছাড়া। যেমন `input[id="i0118"][name="passwd"]`।
- **`i`** — উদ্ধৃত মানের পরে, `]`-এর আগে লিখুন। ওই একটি শর্তে ইংরেজি অক্ষরের বড় ও ছোট হাতের পার্থক্য উপেক্ষা করবে। প্রতিটি শর্তে আলাদা করে প্রয়োগ হয়।
- **`i` ছাড়া** — এই গাইডের ID, name, class ও aria-label-এর মানে case মিলতে হবে।
- **`s`** — CSS-এ স্পষ্টভাবে case মেলানোর flag। Browser ও UiPath-এ সমর্থন যাচাই করে ব্যবহার করুন। ID, name, class ও aria-label-এর জন্য সাধারণত flag ছাড়াই ডিফল্ট case-sensitive মিল যথেষ্ট।

## ID ও class একসঙ্গে

ID ও class একই input-এ থাকতে পারে। `i` যোগ করতে চাইলে shorthand-এর বদলে attribute syntax ব্যবহার করুন।

### OR

**`i` ছাড়া**

```xml
<webctrl css-selector='input#i0118, input.ext-input' />
```

**শুধু প্রথম শর্তে `i`**

```xml
<webctrl css-selector='input[id="I0118" i], input.ext-input' />
```

**শুধু দ্বিতীয় শর্তে `i`**

```xml
<webctrl css-selector='input#i0118, input[class~="EXT-INPUT" i]' />
```

**দুই শর্তেই `i`**

```xml
<webctrl css-selector='input[id="I0118" i], input[class~="EXT-INPUT" i]' />
```

### AND

**`i` ছাড়া**

```xml
<webctrl css-selector='input#i0118.ext-input' />
```

**শুধু প্রথম শর্তে `i`**

```xml
<webctrl css-selector='input[id="I0118" i].ext-input' />
```

**শুধু দ্বিতীয় শর্তে `i`**

```xml
<webctrl css-selector='input#i0118[class~="EXT-INPUT" i]' />
```

**দুই শর্তেই `i`**

```xml
<webctrl css-selector='input[id="I0118" i][class~="EXT-INPUT" i]' />
```

## `=` — হুবহু মান

`passwd` মিলবে, `my-passwd` মিলবে না।

### OR

**`i` ছাড়া**

```xml
<webctrl css-selector='input[id="i0118"], input[name="passwd"]' />
```

**শুধু প্রথম শর্তে `i`**

```xml
<webctrl css-selector='input[id="I0118" i], input[name="passwd"]' />
```

**শুধু দ্বিতীয় শর্তে `i`**

```xml
<webctrl css-selector='input[id="i0118"], input[name="PASSWD" i]' />
```

**দুই শর্তেই `i`**

```xml
<webctrl css-selector='input[id="I0118" i], input[name="PASSWD" i]' />
```

### AND

**`i` ছাড়া**

```xml
<webctrl css-selector='input[id="i0118"][name="passwd"]' />
```

**শুধু প্রথম শর্তে `i`**

```xml
<webctrl css-selector='input[id="I0118" i][name="passwd"]' />
```

**শুধু দ্বিতীয় শর্তে `i`**

```xml
<webctrl css-selector='input[id="i0118"][name="PASSWD" i]' />
```

**দুই শর্তেই `i`**

```xml
<webctrl css-selector='input[id="I0118" i][name="PASSWD" i]' />
```

## `*=` — মানের যেকোনো অংশ

`my-passwd`-এ `pass` আছে। অক্ষরগুলো পরপর থাকতে হবে।

### OR

**`i` ছাড়া**

```xml
<webctrl css-selector='input[name*="pass"], input[aria-label*="password"]' />
```

**শুধু প্রথম শর্তে `i`**

```xml
<webctrl css-selector='input[name*="PASS" i], input[aria-label*="password"]' />
```

**শুধু দ্বিতীয় শর্তে `i`**

```xml
<webctrl css-selector='input[name*="pass"], input[aria-label*="PASSWORD" i]' />
```

**দুই শর্তেই `i`**

```xml
<webctrl css-selector='input[name*="PASS" i], input[aria-label*="PASSWORD" i]' />
```

### AND

**`i` ছাড়া**

```xml
<webctrl css-selector='input[name*="pass"][aria-label*="password"]' />
```

**শুধু প্রথম শর্তে `i`**

```xml
<webctrl css-selector='input[name*="PASS" i][aria-label*="password"]' />
```

**শুধু দ্বিতীয় শর্তে `i`**

```xml
<webctrl css-selector='input[name*="pass"][aria-label*="PASSWORD" i]' />
```

**দুই শর্তেই `i`**

```xml
<webctrl css-selector='input[name*="PASS" i][aria-label*="PASSWORD" i]' />
```

## `^=` — মানের শুরু

`Enter the password for this account` মানটি `Enter the password` দিয়ে শুরু।

### OR

**`i` ছাড়া**

```xml
<webctrl css-selector='input[name^="pass"], input[aria-label^="Enter the password"]' />
```

**শুধু প্রথম শর্তে `i`**

```xml
<webctrl css-selector='input[name^="PASS" i], input[aria-label^="Enter the password"]' />
```

**শুধু দ্বিতীয় শর্তে `i`**

```xml
<webctrl css-selector='input[name^="pass"], input[aria-label^="ENTER THE PASSWORD" i]' />
```

**দুই শর্তেই `i`**

```xml
<webctrl css-selector='input[name^="PASS" i], input[aria-label^="ENTER THE PASSWORD" i]' />
```

### AND

**`i` ছাড়া**

```xml
<webctrl css-selector='input[name^="pass"][aria-label^="Enter the password"]' />
```

**শুধু প্রথম শর্তে `i`**

```xml
<webctrl css-selector='input[name^="PASS" i][aria-label^="Enter the password"]' />
```

**শুধু দ্বিতীয় শর্তে `i`**

```xml
<webctrl css-selector='input[name^="pass"][aria-label^="ENTER THE PASSWORD" i]' />
```

**দুই শর্তেই `i`**

```xml
<webctrl css-selector='input[name^="PASS" i][aria-label^="ENTER THE PASSWORD" i]' />
```

## `$=` — মানের শেষ

`Enter the password` মানটি `password` দিয়ে শেষ। পরে `for this account` থাকলে ওই শর্ত মিলবে না।

### OR

**`i` ছাড়া**

```xml
<webctrl css-selector='input[name$="wd"], input[aria-label$="password"]' />
```

**শুধু প্রথম শর্তে `i`**

```xml
<webctrl css-selector='input[name$="WD" i], input[aria-label$="password"]' />
```

**শুধু দ্বিতীয় শর্তে `i`**

```xml
<webctrl css-selector='input[name$="wd"], input[aria-label$="PASSWORD" i]' />
```

**দুই শর্তেই `i`**

```xml
<webctrl css-selector='input[name$="WD" i], input[aria-label$="PASSWORD" i]' />
```

### AND

**`i` ছাড়া**

```xml
<webctrl css-selector='input[name$="wd"][aria-label$="password"]' />
```

**শুধু প্রথম শর্তে `i`**

```xml
<webctrl css-selector='input[name$="WD" i][aria-label$="password"]' />
```

**শুধু দ্বিতীয় শর্তে `i`**

```xml
<webctrl css-selector='input[name$="wd"][aria-label$="PASSWORD" i]' />
```

**দুই শর্তেই `i`**

```xml
<webctrl css-selector='input[name$="WD" i][aria-label$="PASSWORD" i]' />
```

## `~=` — স্পেস দিয়ে আলাদা পুরো শব্দ

`ext-input` মেলে `form-control ext-input`-এ। `ext-input-large`-এ মেলে না।

### OR

**`i` ছাড়া**

```xml
<webctrl css-selector='input[class~="ext-input"], input[aria-label~="password"]' />
```

**শুধু প্রথম শর্তে `i`**

```xml
<webctrl css-selector='input[class~="EXT-INPUT" i], input[aria-label~="password"]' />
```

**শুধু দ্বিতীয় শর্তে `i`**

```xml
<webctrl css-selector='input[class~="ext-input"], input[aria-label~="PASSWORD" i]' />
```

**দুই শর্তেই `i`**

```xml
<webctrl css-selector='input[class~="EXT-INPUT" i], input[aria-label~="PASSWORD" i]' />
```

### AND

**`i` ছাড়া**

```xml
<webctrl css-selector='input[class~="ext-input"][aria-label~="password"]' />
```

**শুধু প্রথম শর্তে `i`**

```xml
<webctrl css-selector='input[class~="EXT-INPUT" i][aria-label~="password"]' />
```

**শুধু দ্বিতীয় শর্তে `i`**

```xml
<webctrl css-selector='input[class~="ext-input"][aria-label~="PASSWORD" i]' />
```

**দুই শর্তেই `i`**

```xml
<webctrl css-selector='input[class~="EXT-INPUT" i][aria-label~="PASSWORD" i]' />
```

## `|=` — হুবহু মান অথবা তার ঠিক পরে হাইফেন

`[name|="user"]` দিয়ে `user` ও `user-login` মিলবে। `username` মিলবে না।

### OR

**`i` ছাড়া**

```xml
<webctrl css-selector='input[name|="user"], input[id|="login"]' />
```

**শুধু প্রথম শর্তে `i`**

```xml
<webctrl css-selector='input[name|="USER" i], input[id|="login"]' />
```

**শুধু দ্বিতীয় শর্তে `i`**

```xml
<webctrl css-selector='input[name|="user"], input[id|="LOGIN" i]' />
```

**দুই শর্তেই `i`**

```xml
<webctrl css-selector='input[name|="USER" i], input[id|="LOGIN" i]' />
```

### AND

**`i` ছাড়া**

```xml
<webctrl css-selector='input[name|="user"][id|="login"]' />
```

**শুধু প্রথম শর্তে `i`**

```xml
<webctrl css-selector='input[name|="USER" i][id|="login"]' />
```

**শুধু দ্বিতীয় শর্তে `i`**

```xml
<webctrl css-selector='input[name|="user"][id|="LOGIN" i]' />
```

**দুই শর্তেই `i`**

```xml
<webctrl css-selector='input[name|="USER" i][id|="LOGIN" i]' />
```

## [attribute] — attribute আছে কি না

খালি মানও উপস্থিত হিসেবে গণ্য হয়। `[aria-label]` নিজে কোনো মান তুলনা করে না। পাশের value শর্তে `i` বসাতে পারেন।

**name আছে**

```xml
<webctrl css-selector='input[name]' />
```

**aria-label আছে**

```xml
<webctrl css-selector='input[aria-label]' />
```

**name অথবা aria-label আছে**

```xml
<webctrl css-selector='input[name], input[aria-label]' />
```

**name ও aria-label দুটোই আছে**

```xml
<webctrl css-selector='input[name][aria-label]' />
```

**OR, case স্বাভাবিক নিয়মে**

```xml
<webctrl css-selector='input[aria-label], input[name="passwd"]' />
```

**OR, name-এ case উপেক্ষা**

```xml
<webctrl css-selector='input[aria-label], input[name="PASSWD" i]' />
```

**AND, case স্বাভাবিক নিয়মে**

```xml
<webctrl css-selector='input[aria-label][name="passwd"]' />
```

**AND, name-এ case উপেক্ষা**

```xml
<webctrl css-selector='input[aria-label][name="PASSWD" i]' />
```

## স্পষ্ট case flag দিয়ে OR ও AND

`s` ব্যবহার করলে আপনার UiPath ও browser সেটি গ্রহণ করছে কি না Validate করুন। একটি `[...]`-এ একটি flag বসে।

**OR — প্রথমে `s`, দ্বিতীয়টিতে `s`**

```xml
<webctrl css-selector='input[name="passwd" s], input[id="i0118" s]' />
```

**OR — প্রথমে `i`, দ্বিতীয়টিতে `s`**

```xml
<webctrl css-selector='input[name="PASSWD" i], input[id="i0118" s]' />
```

**OR — প্রথমে `s`, দ্বিতীয়টিতে `i`**

```xml
<webctrl css-selector='input[name="passwd" s], input[id="I0118" i]' />
```

**OR — প্রথমে `i`, দ্বিতীয়টিতে `i`**

```xml
<webctrl css-selector='input[name="PASSWD" i], input[id="I0118" i]' />
```

**AND — প্রথমে `s`, দ্বিতীয়টিতে `s`**

```xml
<webctrl css-selector='input[name="passwd" s][id="i0118" s]' />
```

**AND — প্রথমে `i`, দ্বিতীয়টিতে `s`**

```xml
<webctrl css-selector='input[name="PASSWD" i][id="i0118" s]' />
```

**AND — প্রথমে `s`, দ্বিতীয়টিতে `i`**

```xml
<webctrl css-selector='input[name="passwd" s][id="I0118" i]' />
```

**AND — প্রথমে `i`, দ্বিতীয়টিতে `i`**

```xml
<webctrl css-selector='input[name="PASSWD" i][id="I0118" i]' />
```

## ID, name ও aria-label — OR

তিনটির যেকোনো একটি শর্ত মিললেই হবে।

**`i` ছাড়া**

```xml
<webctrl css-selector='input[id="i0118"], input[name*="pass"], input[aria-label^="Enter the password"]' />
```

**`i` আছে — ID**

```xml
<webctrl css-selector='input[id="I0118" i], input[name*="pass"], input[aria-label^="Enter the password"]' />
```

**`i` আছে — name**

```xml
<webctrl css-selector='input[id="i0118"], input[name*="PASS" i], input[aria-label^="Enter the password"]' />
```

**`i` আছে — aria-label**

```xml
<webctrl css-selector='input[id="i0118"], input[name*="pass"], input[aria-label^="ENTER THE PASSWORD" i]' />
```

**`i` আছে — ID, name**

```xml
<webctrl css-selector='input[id="I0118" i], input[name*="PASS" i], input[aria-label^="Enter the password"]' />
```

**`i` আছে — ID, aria-label**

```xml
<webctrl css-selector='input[id="I0118" i], input[name*="pass"], input[aria-label^="ENTER THE PASSWORD" i]' />
```

**`i` আছে — name, aria-label**

```xml
<webctrl css-selector='input[id="i0118"], input[name*="PASS" i], input[aria-label^="ENTER THE PASSWORD" i]' />
```

**`i` আছে — ID, name, aria-label**

```xml
<webctrl css-selector='input[id="I0118" i], input[name*="PASS" i], input[aria-label^="ENTER THE PASSWORD" i]' />
```

## ID, name ও aria-label — AND

একই input-এ তিনটি শর্তই মিলতে হবে।

**`i` ছাড়া**

```xml
<webctrl css-selector='input[id="i0118"][name*="pass"][aria-label^="Enter the password"]' />
```

**`i` আছে — ID**

```xml
<webctrl css-selector='input[id="I0118" i][name*="pass"][aria-label^="Enter the password"]' />
```

**`i` আছে — name**

```xml
<webctrl css-selector='input[id="i0118"][name*="PASS" i][aria-label^="Enter the password"]' />
```

**`i` আছে — aria-label**

```xml
<webctrl css-selector='input[id="i0118"][name*="pass"][aria-label^="ENTER THE PASSWORD" i]' />
```

**`i` আছে — ID, name**

```xml
<webctrl css-selector='input[id="I0118" i][name*="PASS" i][aria-label^="Enter the password"]' />
```

**`i` আছে — ID, aria-label**

```xml
<webctrl css-selector='input[id="I0118" i][name*="pass"][aria-label^="ENTER THE PASSWORD" i]' />
```

**`i` আছে — name, aria-label**

```xml
<webctrl css-selector='input[id="i0118"][name*="PASS" i][aria-label^="ENTER THE PASSWORD" i]' />
```

**`i` আছে — ID, name, aria-label**

```xml
<webctrl css-selector='input[id="I0118" i][name*="PASS" i][aria-label^="ENTER THE PASSWORD" i]' />
```

## username-এর মাঝখানে স্পেস

`i` স্পেসের সংখ্যা বদলায় না। শূন্য, এক ও দুইটি স্পেস মেলাতে আলাদা বিকল্প লিখুন। AND দিয়ে `user` ও `name` আলাদা করে খুঁজলে `name-user` এবং `user-other-name`-ও মিলে যাবে।

**হুবহু তিনটি বিকল্প**

```xml
<webctrl css-selector='input[name="username"], input[name="user name"], input[name="user  name"]' />
```

**হুবহু তিনটি বিকল্প, case উপেক্ষা**

```xml
<webctrl css-selector='input[name="USERNAME" i], input[name="USER NAME" i], input[name="USER  NAME" i]' />
```

**মানের যেকোনো অংশে তিনটি বিকল্প**

```xml
<webctrl css-selector='input[name*="username"], input[name*="user name"], input[name*="user  name"]' />
```

**মানের যেকোনো অংশে তিনটি বিকল্প, case উপেক্ষা**

```xml
<webctrl css-selector='input[name*="USERNAME" i], input[name*="USER NAME" i], input[name*="USER  NAME" i]' />
```

**AND — যেকোনো ক্রমে দুটো অংশই আছে**

```xml
<webctrl css-selector='input[name*="user"][name*="name"]' />
```

**AND — যেকোনো ক্রমে দুটো অংশ, case উপেক্ষা**

```xml
<webctrl css-selector='input[name*="USER" i][name*="NAME" i]' />
```

## UiPath-এ ব্যবহার

UI Explorer-এ একটি selector কপি করে **Validate → Highlight** করুন। Highlight দেখে নিশ্চিত করুন যে আপনার চাওয়া element-টি ধরা পড়েছে।
