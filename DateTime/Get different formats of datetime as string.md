# Different Formats of DateTime as String in UiPath

In UiPath, you can use the `ToString` method on the `DateTime` object to convert it into various formats. Below are the different formats you can use to get the current date and time in various forms.


### Summary of DateTime Formats:

| Format       | Example Output   | Description                           |
|--------------|------------------|---------------------------------------|
| `dd`         | `04`             | Current day in numerical terms       |
| `dddd`       | `Monday`         | Full name of the day                 |
| `MMMM`       | `December`       | Full name of the month               |
| `MMM`        | `Dec`            | First three letters of the month     |
| `MM`         | `12`             | Month as a number                    |
| `yyyy`       | `2024`           | Full year                            |
| `yy`         | `24`             | Last two characters of the year      |
| `hh:mm:ss`   | `02:30:45`       | 12-hour format time                  |
| `HH:mm:ss`   | `14:30:45`       | 24-hour format time                  |
| `hh`         | `02`             | Hour in 12-hour format               |
| `HH`         | `14`             | Hour in 24-hour format               |
| `mm`         | `30`             | Current minutes                      |
| `ss`         | `45`             | Current seconds                      |


## 1. Get Current Day (Numerical Terms)
To get the current day as a number (e.g., `04` for 4th):

```
Datetime.Now.ToString("dd")
```

## 2. Get Current Day (Full Text)
To get the full name of the current day (e.g., Monday):
```
Datetime.Now.ToString("dddd")
```

## 3. Get Current Month (Full Name)
To get the full name of the current month (e.g., December):

```
Datetime.Now.ToString("MMMM")
```

## 4. Get Current Month (First Three Characters)
To get the first three characters of the current month (e.g., Dec):

```
Datetime.Now.ToString("MMM")
```

## 5. Get Current Month (Numerical Value)
To get the current month as a number (e.g., 12 for December):

```
Datetime.Now.ToString("MM")
```

## 6. Get Current Year (Full Year)
To get the current year in full (e.g., 2024):

```
Datetime.Now.ToString("yyyy")
```

## 7. Get Current Year (Last Two Characters)
To get the last two characters of the current year (e.g., 24 for the year 2024):

```
Datetime.Now.ToString("yy")
```

## 8. Get Current Time (12-Hour Format)
To get the current time in a 12-hour format with seconds (e.g., 02:30:45):

```
Datetime.Now.ToString("hh:mm:ss")
```

## 9. Get Current Time (24-Hour Format)
To get the current time in a 24-hour format with seconds (e.g., 14:30:45):

```
Datetime.Now.ToString("HH:mm:ss")
```

## 10. Get Current Hour (12-Hour Format)
To get the current hour in a 12-hour format (e.g., 02):

```
Datetime.Now.ToString("hh")
```

## 11. Get Current Hour (24-Hour Format)
To get the current hour in a 24-hour format (e.g., 14):

```
Datetime.Now.ToString("HH")
```

## 12. Get Current Minutes
To get the current minutes (e.g., 30):

```
Datetime.Now.ToString("mm")
```

## 13. Get Current Seconds
To get the current seconds (e.g., 45):

```
Datetime.Now.ToString("ss")
```
