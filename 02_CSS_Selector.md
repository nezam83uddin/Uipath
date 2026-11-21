# UiPath CSS Selector গাইড

CSS selector-গুলো `<webctrl css-selector='...' />`-এর ভেতরে লিখুন।  
বাইরের quote single (`'`), CSS-এর attribute value-র quote double (`"`)।

উদাহরণগুলোতে ছবির মতো `id="i0118"`, `name="passwd"` এবং `aria-label="Enter the password for ..."` ধরা হয়েছে।

## ১. ID দিয়ে খোঁজা

`#` হলো ID-এর সংক্ষিপ্ত চিহ্ন। `#i0118` মানে `id="i0118"`। `input` যোগ করলে শুধু input tag-এ খুঁজবে।

1. `id` দিয়ে:

   ```xml
   <webctrl css-selector='#i0118' />
   ```

2. শুধু input-এর মধ্যে `id` খুঁজতে:

   ```xml
   <webctrl css-selector='input#i0118' />
   ```

3. Attribute selector দিয়ে একই ID:

   ```xml
   <webctrl css-selector='[id="i0118"]' />
   ```

4. Input tag এবং attribute selector দিয়ে:

   ```xml
   <webctrl css-selector='input[id="i0118"]' />
   ```

5. ID-কে case-insensitive করে খুঁজতে:

   ```xml
   <webctrl css-selector='[id="i0118" i]' />
   ```

সাধারণত `#i0118` case-sensitive। `#i0118`-এর শেষে `i` যোগ করবেন না। `#i0118 i` লিখলে এটি `#i0118` element-এর ভেতরের `<i>` tag খুঁজবে।

## ২. `name` দিয়ে খোঁজা

`name`-এর জন্য `#` বা `.`-এর মতো সংক্ষিপ্ত চিহ্ন নেই। তাই `[name="..."]` ব্যবহার করুন।

1. `name` হুবহু মিললে:

   ```xml
   <webctrl css-selector='[name="passwd"]' />
   ```

2. শুধু input-এর `name` হুবহু মিললে:

   ```xml
   <webctrl css-selector='input[name="passwd"]' />
   ```

3. `name`-এর মধ্যে `pass` থাকলে (`*=` মানে মানের যেকোনো অংশে আছে):

   ```xml
   <webctrl css-selector='input[name*="pass"]' />
   ```

4. `name` যদি `pass` দিয়ে শুরু হয় (`^=`):

   ```xml
   <webctrl css-selector='input[name^="pass"]' />
   ```

5. `name` যদি `wd` দিয়ে শেষ হয় (`$=`):

   ```xml
   <webctrl css-selector='input[name$="wd"]' />
   ```

## ৩. `aria-label` দিয়ে খোঁজা

`aria-label`-এর পুরো মান না লিখে তার একটি অংশ দিয়েও খুঁজতে পারেন।

1. `aria-label` হুবহু মিললে:

   ```xml
   <webctrl css-selector='input[aria-label="Enter the password"]' />
   ```

2. `aria-label`-এর মধ্যে phrase থাকলে:

   ```xml
   <webctrl css-selector='input[aria-label*="Enter the password" i]' />
   ```

3. `aria-label` যদি phrase দিয়ে শুরু হয় (`^=`):

   ```xml
   <webctrl css-selector='input[aria-label^="Enter the password" i]' />
   ```

4. `aria-label` যদি `password` দিয়ে শেষ হয় (`$=`):

   ```xml
   <webctrl css-selector='input[aria-label$="password" i]' />
   ```

5. `aria-label` হুবহু মিলবে, তবে বড়-ছোট হাতের পার্থক্য উপেক্ষা করে:

   ```xml
   <webctrl css-selector='input[aria-label="ENTER THE PASSWORD" i]' />
   ```

## ৪. `i` কী এবং কোথায় বসে?

`i` ওই attribute condition-এ ইংরেজি অক্ষরের বড়-ছোট হাতের পার্থক্য উপেক্ষা করে। এটি উদ্ধৃত মানের পরে এবং `]`-এর আগে বসে। এটি global নয়—যে condition-এ case উপেক্ষা করতে চান, তার ভেতরেই `i` দিন।

1. `name` হুবহু, case উপেক্ষা করে:

   ```xml
   <webctrl css-selector='input[name="PASSWD" i]' />
   ```

2. `name`-এর অংশ, case উপেক্ষা করে:

   ```xml
   <webctrl css-selector='input[name*="PASS" i]' />
   ```

3. ID attribute, case উপেক্ষা করে:

   ```xml
   <webctrl css-selector='input[id="I0118" i]' />
   ```

4. `aria-label`-এর অংশ, case উপেক্ষা করে:

   ```xml
   <webctrl css-selector='input[aria-label*="ENTER THE PASSWORD" i]' />
   ```

5. `placeholder` হুবহু, case উপেক্ষা করে:

   ```xml
   <webctrl css-selector='input[placeholder="PASSWORD" i]' />
   ```

`i` না দিলে সাধারণত value match case-sensitive হয়। একাধিক condition-এ case উপেক্ষা করতে চাইলে প্রতিটিতে আলাদা করে `i` দিন:

```xml
<webctrl css-selector='input[id="i0118" i][name="passwd" i][aria-label*="Enter the password" i]' />
```

শেষে একবার `i` লিখে পুরো selector-এ প্রয়োগ করা যায় না।

## ৫. OR: যেকোনো একটি শর্ত মিললেই

কমা `,` হলো OR। যে কোনো একটি selector মিললেই element match হবে।

1. ID অথবা name:

   ```xml
   <webctrl css-selector='#i0118, [name="passwd"]' />
   ```

2. ID অথবা aria-label:

   ```xml
   <webctrl css-selector='#i0118, [aria-label*="Enter the password" i]' />
   ```

3. name অথবা aria-label:

   ```xml
   <webctrl css-selector='[name="passwd"], [aria-label*="Enter the password" i]' />
   ```

4. ID, name অথবা aria-label:

   ```xml
   <webctrl css-selector='input#i0118, input[name="passwd"], input[aria-label*="Enter the password" i]' />
   ```

5. তিনটি বিকল্প, `input` tag ছাড়া:

   ```xml
   <webctrl css-selector='#i0118, [name="passwd"], [aria-label*="Enter the password" i]' />
   ```

## ৬. AND: একই element-এ সব শর্ত মিলতে হবে

AND করতে condition-গুলো পাশাপাশি লিখুন; মাঝখানে কমা দেবেন না।

1. ID এবং name:

   ```xml
   <webctrl css-selector='input[id="i0118"][name="passwd"]' />
   ```

2. ID এবং aria-label:

   ```xml
   <webctrl css-selector='input[id="i0118"][aria-label*="Enter the password" i]' />
   ```

3. name এবং aria-label:

   ```xml
   <webctrl css-selector='input[name="passwd"][aria-label*="Enter the password" i]' />
   ```

4. type এবং name:

   ```xml
   <webctrl css-selector='input[type="password"][name="passwd"]' />
   ```

5. ID, name এবং aria-label—তিনটিই:

   ```xml
   <webctrl css-selector='input[id="i0118"][name="passwd"][aria-label*="Enter the password" i]' />
   ```

## ৭. Class দিয়ে খোঁজা

`.` হলো class-এর সংক্ষিপ্ত চিহ্ন। ছবির ফর্মে `.username-form` দিলে form element match হবে; input নয়, কারণ class-টি form-এ আছে।

1. Class দিয়ে:

   ```xml
   <webctrl css-selector='.username-form' />
   ```

2. নির্দিষ্ট tag-এর class:

   ```xml
   <webctrl css-selector='form.username-form' />
   ```

3. Class-এর ভেতরে ID-যুক্ত input:

   ```xml
   <webctrl css-selector='.username-form #i0118' />
   ```

4. Class-এর ভেতরে name-যুক্ত input:

   ```xml
   <webctrl css-selector='.username-form input[name="passwd"]' />
   ```

5. Class-এর ভেতরে aria-label-যুক্ত input:

   ```xml
   <webctrl css-selector='.username-form input[aria-label*="Enter the password" i]' />
   ```

## দ্রুত মনে রাখুন

| CSS | অর্থ |
|---|---|
| `#i0118` | `id="i0118"` |
| `.username-form` | `class="username-form"` |
| `[name="passwd"]` | `name` হুবহু `passwd` |
| `[name*="pass"]` | `name`-এর যেকোনো অংশে `pass` আছে |
| `[name^="pass"]` | `name` `pass` দিয়ে শুরু |
| `[name$="wd"]` | `name` `wd` দিয়ে শেষ |
| `[aria-label*="Enter the password" i]` | phrase আছে; case উপেক্ষা করে |
| `A, B` | OR: A অথবা B |
| `A[B]` | AND: একই element-এ A এবং B |
