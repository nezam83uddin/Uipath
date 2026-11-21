# UiPath CSS Selector গাইড — `~` ও `~=`

CSS-এ `~` চিহ্নটি কোথায় বসছে, তার ওপর এর কাজ বদলায়।

| লেখার ধরন | সহজ অর্থ |
|---|---|
| `[class~="ext-input"]` | class-এর তালিকায় `ext-input` নামে পুরো একটি class খোঁজে |
| `label ~ input` | একই parent-এর ভেতরে `label`-এর পরে থাকা `input` খোঁজে |

## `~=` দিয়ে পুরো শব্দ খোঁজা

ধরো, একটা বাক্সে `big`, `red` আর `round` নামে তিনটা স্টিকার আছে। `~=` দিয়ে তুমি বলছ, “ঠিক `red` নামে একটা স্টিকার আছে কি?” `reddish` নামে স্টিকার থাকলে সেটা মিলবে না।

CSS-এ নিয়মটি হলো `[attribute~="একটি শব্দ"]`। একটি স্পেস, কয়েকটি স্পেস বা ট্যাব দিয়ে লেখা আলাদা করা থাকলে CSS সেগুলোকে আলাদা শব্দ ধরে।

**Class-এর তালিকায় একটি পুরো class খুঁজতে**

```xml
<webctrl css-selector='input[class~="ext-input"]' />
```

| HTML-এ যা আছে | মিলবে? | কেন |
|---|---|---|
| `class="ext-input"` | হ্যাঁ | পুরো class-এর নাম `ext-input` |
| `class="form-control ext-input"` | হ্যাঁ | `ext-input` আলাদা একটি class |
| `class="ext-input   form-control"` | হ্যাঁ | কয়েকটি স্পেস দিয়েও class আলাদা করা যায় |
| `class="ext-input-large"` | না | পুরো class-এর নাম `ext-input-large` |
| `class="EXT-INPUT"` | না | এই selector-এ বড় ও ছোট হাতের অক্ষর আলাদা ধরা হয় |

**একটি পুরো class খোঁজার ছোট রূপ**

```xml
<webctrl css-selector='input.ext-input' />
```

সাধারণ HTML পেজে এটি `input[class~="ext-input"]`-এর মতোই একটি পুরো class মেলায়। Class তালিকায় আগে বা পরে থাকলেও মিলবে।

**Class মেলাতে বড় ও ছোট হাতের পার্থক্য উপেক্ষা করতে**

```xml
<webctrl css-selector='input[class~="EXT-INPUT" i]' />
```

`class="form-control ext-input"` মিলবে। উদ্ধৃত মানের পরে `i` দেওয়ায় `EXT-INPUT` আর `ext-input` একই ধরা হবে। `ext-input-large` তবুও মিলবে না।

**`name`-এ আলাদা একটি শব্দ খুঁজতে**

```xml
<webctrl css-selector='input[name~="passwd"]' />
```

- `name="passwd"` → মিলবে।
- `name="login passwd"` → মিলবে, কারণ `passwd` আলাদা একটি শব্দ।
- `name="login-passwd"` → মিলবে না, কারণ হাইফেন এখানে শব্দ দুটোকে আলাদা করে না।

**পুরো `name` হুবহু মেলাতে**

```xml
<webctrl css-selector='input[name="passwd"]' />
```

এখানে শুধু `name="passwd"` মিলবে। `name="login passwd"` মিলবে না।

**ID-তে `~=` ব্যবহার করলে**

```xml
<webctrl css-selector='input[id~="i0118"]' />
```

`id="i0118"` মিলবে। `id="login-i0118"` মিলবে না। বৈধ HTML ID-তে স্পেস থাকে না, তাই ID হুবহু খুঁজতে নিচের ছোট রূপটিই যথেষ্ট।

**ID হুবহু মেলানোর ছোট রূপ**

```xml
<webctrl css-selector='input#i0118' />
```

**`aria-label`-এ একটি পুরো শব্দ খুঁজতে**

```xml
<webctrl css-selector='input[aria-label~="password" i]' />
```

- `aria-label="Enter the PASSWORD"` → মিলবে।
- `aria-label="Enter the password!"` → মিলবে না, কারণ `!` চিহ্নটি শব্দের সঙ্গে লেগে আছে।
- `aria-label="Enter the passwords"` → মিলবে না, কারণ `passwords` আলাদা শব্দ।

**`aria-label`-এ পুরো বাক্যাংশ খুঁজতে**

```xml
<webctrl css-selector='input[aria-label*="Enter the password" i]' />
```

`~=` দিয়ে একবারে একটি পুরো শব্দ খোঁজা যায়। `Enter the password`-এর মতো স্পেসসহ বাক্যাংশ খুঁজতে `*=` ব্যবহার করুন। এটি `aria-label="Enter the password for this account"`-এর সঙ্গে মিলবে।

**AND — একই input-এ দুইটি class থাকতে হবে**

```xml
<webctrl css-selector='input[class~="form-control"][class~="EXT-INPUT" i]' />
```

দুই শর্ত পাশাপাশি আছে, তাই একই input-এ `form-control` ও `ext-input` দুটোই থাকতে হবে। `i` শুধু দ্বিতীয় শর্তে কাজ করবে।

**OR — দুইটি class-এর যেকোনো একটি থাকলেই হবে**

```xml
<webctrl css-selector='input[class~="ext-input"], input[class~="form-control"]' />
```

কমা মানে OR। কোনো input-এ `ext-input` বা `form-control` থাকলেই সেটি মিলবে। দুইটি আলাদা input-ও মিলতে পারে।

## `~` একা দিয়ে পরে থাকা element খোঁজা

ধরো, একই ফর্মের ভেতরের element-গুলো লাইনে দাঁড়িয়ে আছে। `label ~ input` বলছে, “এই লাইনে `label`-এর পরে যে `input`-গুলো আছে, সেগুলো খোঁজো।”

এখানে **একই parent** মানে দুটো element একই HTML element-এর সরাসরি ভেতরে আছে। মাঝখানে অন্য element থাকতে পারে। কোনটি আগে বা পরে, সেটা HTML-এর ক্রম দিয়ে ঠিক হয়।

**উদাহরণের HTML**

```html
<form>
  <input id="before">
  <label for="i0118">Password</label>
  <span>নির্দেশনা</span>
  <input id="i0118" name="passwd" class="ext-input">
  <div>
    <input id="nested">
  </div>
  <input id="confirm" name="confirm">
</form>
```

**একই form-এ label-এর পরে থাকা input**

```xml
<webctrl css-selector='label ~ input' />
```

| Input-এর ID | মিলবে? | কেন |
|---|---|---|
| `before` | না | `label`-এর আগে আছে |
| `i0118` | হ্যাঁ | একই `form`-এর ভেতরে `label`-এর পরে আছে |
| `nested` | না | এর সরাসরি parent হলো `div` |
| `confirm` | হ্যাঁ | একই `form`-এর ভেতরে `label`-এর পরে আছে |

**পরে থাকা input-এর ID-ও মেলাতে**

```xml
<webctrl css-selector='label ~ input#i0118' />
```

শুধু `i0118` মিলবে। `~`-এর ডান পাশের `input#i0118` হলো যেটিকে খুঁজছেন।

**কোন label-এর পর থেকে খুঁজবে তা নির্দিষ্ট করতে**

```xml
<webctrl css-selector='label[for="i0118"] ~ input' />
```

`for="i0118"` থাকা label-এর পরে `i0118` ও `confirm` দুটোই আছে, তাই দুটোই মিলবে। `~` দিয়ে খোঁজার সময় label কোন input-এর সঙ্গে যুক্ত, সেটি দিয়ে মিল ঠিক হয় না। HTML-এ কোন input পরে আছে, সেটি দেখা হয়।

**পরে থাকা input-এর `name` মেলাতে এবং case উপেক্ষা করতে**

```xml
<webctrl css-selector='label ~ input[name="PASSWD" i]' />
```

শুধু `i0118` মিলবে, কারণ তার `name="passwd"`। `i` শুধু `name`-এর শর্তে কাজ করবে।

**একই selector-এ `~` আর `~=` ব্যবহার করতে**

```xml
<webctrl css-selector='label ~ input[class~="ext-input"]' />
```

- বাইরের `~` বলছে, input-টি একই parent-এর ভেতরে `label`-এর পরে থাকবে।
- ভেতরের `~=` বলছে, ওই input-এর class তালিকায় `ext-input` নামে পুরো একটি class থাকবে।

উপরের HTML-এ শুধু `i0118` দুইটি শর্তই মেলায়।

## `~` আর `+`-এর পার্থক্য

**`~` দিয়ে পরে থাকা সব মিল খোঁজা যায়**

```xml
<webctrl css-selector='label ~ input' />
```

`label` ও `input`-এর মাঝখানে `span` থাকলেও মিলবে।

**`+` দিয়ে ঠিক পরের element দেখা হয়**

```xml
<webctrl css-selector='label + input' />
```

উপরের HTML-এ `label`-এর ঠিক পরে `span` আছে। তাই এই selector কোনো input মেলাবে না।

## দ্রুত মনে রাখুন

| লেখার ধরন | কাজ |
|---|---|
| `[name="passwd"]` | পুরো `name`-এর মান হুবহু মেলায় |
| `[name~="passwd"]` | আলাদা পুরো শব্দ `passwd` খোঁজে |
| `[name*="pass"]` | মানের যেকোনো অংশে `pass` খোঁজে |
| `[class~="EXT-INPUT" i]` | পুরো class মেলায়, বড় ও ছোট হাতের পার্থক্য উপেক্ষা করে |
| `label ~ input` | একই parent-এর ভেতরে label-এর পরে থাকা input খোঁজে |
| `label + input` | একই parent-এর ভেতরে label-এর ঠিক পরের element input হলে মেলায় |

UiPath UI Explorer-এ একবারে একটি selector পেস্ট করে **Validate → Highlight** চাপুন। এতে কোন element ধরা পড়ছে দেখতে পাবেন।
