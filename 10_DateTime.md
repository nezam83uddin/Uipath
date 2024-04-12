## 1. Adding Staring Date, Ending Date and total duration of each process

```java
dateTime_startTime = DateAndTime.Now
dateTime_endTime = System.DateTime.Now
str_TotalTimeInSec = math.Round((dateTime_endTime-dateTime_startTime).TotalSeconds,2).ToString
```

```java
CurrentWeek=GetTodayDate.AddDays((-1*GetTodayDate.DayOfWeek)+1)
LastWeek=CurrentWeek.AddDays(-7)
bool_IsToday=CInt(Date.Today.DayOfWeek)=1
```



## 1. Math (Getting 2 digit)

```scala
math.round(Credit_List.Sum,2)
```
## 1. DateTime

```java
CurrentWeek=GetTodayDate.AddDays((-1*GetTodayDate.DayOfWeek)+1)
LastWeek=CurrentWeek.AddDays(-7)
bool_IsToday=CInt(Date.Today.DayOfWeek)=1
```





### 2. Filter different formation of date

```scala
ImmunizationDT= (from row In immunizationdt Order By DateTime.ParseExact(row(0).ToString, "MM/dd/yyyy", System.Globalization.CultureInfo.InvariantCulture) Ascending Select row).CopyToDataTable
```

```scala
ImmunizationDT= (from row In immunizationdt Order By DateTime.ParseExact(row(0).ToString, "M/d/yyyy", System.Globalization.CultureInfo.InvariantCulture) Ascending Select row).CopyToDataTable
```

### 3. Taking 1st 7th row from DataTable
```scala
ImmunizationDT= dt_OutPutDataTable_Email.AsEnumerable().Take(7).CopyToDataTable
```
### 4. Get all Dates between “28.11.2019” and “03.01.2020” as String
You can read more ([Click this link...]([https://github.com/rpa92/uipath/blob/main/README.md](https://forum.uipath.com/t/get-all-dates-between-28-11-2019-and-03-01-2020-as-string/143774/4)))

```scala

in_str_date = “28.11.2019”
out-str_date = “03.01.2020”

there are totally four steps
–assign activity
–while loop
–assign activity
–writeline activity

the steps involved are
–in a assign activity like this

final_date = Datetime.ParseExact(in_date,“dd.MM.yyyy”,system.globalization.cultureinfo.invariantculture)

where final_date is a datetime variable

–now use a while loop and mention condition like this
final_date > Datetime.ParseExact(out_date,“dd.MM.yyyy”,system.globalization.cultureinfo.invariantculture)

–inside the loop use a assign activity like this
Final_date = Datetime.ParseExact(Final_date,“dd.MM.yyyy”,system.globalization.cultureinfo.invariantculture).AddDays(1)

–now use a write line activity and mention like this
Final_date.ToString(“dd.MM.yyyy”)
```
