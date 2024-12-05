# Get Current DateTime with Timezone and AM/PM

## 1. Get Current DateTime as String with Timezone

To get the current DateTime with the timezone information, use the `K` format specifier. This will include the timezone offset.

### Example:
```
Datetime.Now.ToString("dd/MM/yyyy hh:mm:ss K")
```
### Example Output:
```
04/12/2024 02:30:45 +05:30
```
In this example, the `+05:30` represents the timezone offset (e.g., India Standard Time).

## 2. Get Current DateTime with AM/PM

To get the current DateTime with the AM/PM indicator, use the `tt` format specifier. This will append either `AM` or `PM` based on the time.

### Example:

```
Datetime.Now.ToString("dd/MM/yyyy hh:mm:ss tt")
```

### Example Output:

```
04/12/2024 02:30:45 PM
```

Here, `PM` denotes that the time is in the afternoon.
