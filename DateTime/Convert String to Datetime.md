# Convert a String to DateTime in UiPath

In UiPath, you can convert a string to a `DateTime` object using several methods. Below are the methods you can use along with examples.

### 1. Convert using `Convert.ToDateTime` Method

This method can be used to convert a string to a `DateTime` object.

#### Example:
If the input string is:

```
Strinput = "12/02/2022"
```

You can convert it to `DateTime` using:
```
var_datetime = Convert.ToDateTime(Strinput.ToString)
```


## 2. Convert using `DateTime.Parse` Method
The `DateTime.Parse` method parses a string to a `DateTime` object. It automatically recognizes various date formats.

### Example:
```
var_datetime = DateTime.Parse(Strinput.ToString)
```

## 3. Convert using `DateTime.ParseExact` Method
If you know the exact format of the string, use `DateTime.ParseExact` to specify the format.

### Example:
If the input string is:

```
Strinput = "12/02/2022"
```
You can convert it to DateTime with:
```
var_datetime = DateTime.ParseExact(Strinput.ToString, "dd/MM/yyyy", System.Globalization.CultureInfo.InvariantCulture)
```
In this case, `"dd/MM/yyyy"` is the format that matches the input string. Ensure that the format matches the structure of the string.

## 4. Handle Full Format with Timezone Information
If the input string includes full date-time information, including time and timezone, you can use the `DateTime.ParseExact` method to specify the exact format with the timezone.

### Example:
If the input string is:

```
Strinput = "23/11/2022 02:20:31 +5:30"
```
You can convert it to `DateTime` using:

```
var_datetime = DateTime.ParseExact(Strinput.ToString, "dd/MM/yyyy hh:mm:ss K", System.Globalization.CultureInfo.InvariantCulture)
```
Here, `"dd/MM/yyyy hh:mm:ss K"` is the format that matches the string, including the timezone offset.

### Note:
If you want the result as a string after conversion, you can append `.ToString()` to the expression.

```
var_datetime = DateTime.ParseExact(Strinput.ToString, "dd/MM/yyyy hh:mm:ss K").ToString()
```

This will return the ```DateTime``` in the format specified or the default format based on your machine's culture settings.


### Explanation:
- **`Convert.ToDateTime`**: This method is simple but can be prone to errors if the format of the input string is not recognized by the system.
- **`DateTime.Parse`**: Automatically recognizes various date formats but requires the input string to be in a recognizable format.
- **`DateTime.ParseExact`**: The most reliable method when you know the exact format of the input string. It ensures that the string is parsed exactly as expected.

This markdown provides detailed examples and explanations for converting a string into `DateTime` in UiPath using different methods, depending on the format of the input string.
