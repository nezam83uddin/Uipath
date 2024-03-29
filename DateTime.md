# DateTime

<p align="center">
  <a href="https://www.youtube.com/watch?v=VV89AhYODOE&list=PLl1rPImyc34cqVn6_o4CAV9jVFHR1Rk2e&index=3">
    <img src="https://img.youtube.com/vi/VV89AhYODOE/0.jpg" alt="JavaScript Tutorial For Beginners" />
  </a>
</p>

# DateTime Systax

ডাটা টেবিল থেকে বিভিন্ন ফরমেটের তারিখ ফিল্টার :

```scala
ImmunizationDT= (from row In immunizationdt Order By DateTime.ParseExact(row(0).ToString, "MM/dd/yyyy", System.Globalization.CultureInfo.InvariantCulture) Ascending Select row).CopyToDataTable
```

```scala
ImmunizationDT= (from row In immunizationdt Order By DateTime.ParseExact(row(0).ToString, "M/d/yyyy", System.Globalization.CultureInfo.InvariantCulture) Ascending Select row).CopyToDataTable
```
