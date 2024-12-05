
# Convert a String to DateTime in UiPath

In UiPath, you can convert a string to a `DateTime` object using several methods. Below are the methods you can use along with examples.


## Explanation:
- **`Convert.ToDateTime`**: This method is simple but can be prone to errors if the format of the input string is not recognized by the system.
- **`DateTime.Parse`**: Automatically recognizes various date formats but requires the input string to be in a recognizable format.
- **`DateTime.ParseExact`**: The most reliable method when you know the exact format of the input string. It ensures that the string is parsed exactly as expected.


### 1. Convert using `Convert.ToDateTime` Method

This method can be used to convert a string to a `DateTime` object.

#### Example:
If the input string is:

```
Strinput = "05/12/2024"
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
Strinput = "05/12/2024"
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
Strinput = "23/12/2024 02:20:31 +5:30"
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

# Convert a String of Multiple Possible Date Formats to a DateTime Variable in UiPath

In some cases, you may have a string that represents a date in different formats. For example, the same date string might appear as `"dd/MM/yyyy"`, `"MM/dd/yyyy"`, or `"dd/yy"`, depending on the situation. You can handle such cases in UiPath by defining multiple possible formats in an array and then using the `DateTime.ParseExact` method to try each format.

**Steps to Convert a String with Multiple Possible Date Formats:**

## Define an Array with Possible Date Formats:
   
   You can store the possible formats in an array variable named `arr_formats`.

   ```
   arr_formats = {"dd/MM/yyyy", "MM/dd/yyyy", "dd/yy"}
```

### Convert the Date String Using DateTime.ParseExact:

Use the DateTime.ParseExact method to convert the input string to a DateTime object, specifying all possible formats from the arr_formats array.

```
var_datetime = DateTime.ParseExact(Strinput.ToString, arr_formats, System.Globalization.CultureInfo.InvariantCulture, DateTimeStyles.None)
```
### Example:
Suppose you have an input string Strinput that can be in multiple formats:

```
Strinput = "12/12/2024"  // Format: "dd/MM/yyyy"
```
Or

```
Strinput = "02/12/2024"  // Format: "MM/dd/yyyy"
```
Or

```
Strinput = "12/24"  // Format: "dd/yy"
```
Now, you can convert this string into a DateTime variable using the array of formats:

```
arr_formats = {"dd/MM/yyyy", "MM/dd/yyyy", "dd/yy"}
var_datetime = DateTime.ParseExact(Strinput.ToString, arr_formats, System.Globalization.CultureInfo.InvariantCulture, DateTimeStyles.None)
```
This approach ensures that the input string is parsed correctly even if the format changes.

### Explanation:
`arr_formats`: An array containing multiple possible date formats.

`DateTime.ParseExact`: This method attempts to parse the input string according to each format in the array until it succeeds.

`System.Globalization.CultureInfo.InvariantCulture`: Specifies that the parsing should not depend on the system's culture settings.

`DateTimeStyles.None`: Indicates that no additional formatting styles are applied.

### Notes:
Ensure that the format in the `arr_formats` array exactly matches the structure of the input string, as `DateTime.ParseExact` is strict about the format.
If you expect the input string to have different formats, this method will efficiently handle the conversion without errors.



# Convert a String to DateTime of Specific Culture Info in UiPath

In UiPath, you can convert a string to `DateTime` using a specific culture (e.g., German) by using `DateTime.ParseExact` along with the `CultureInfo` class. This allows you to handle date formatting according to different regional settings.

### Scenario:

Let’s assume you have a date string like `Strinput = "12-22-2024"`, which represents the date in the format `MM-dd-yyyy`. If you want to convert it to `DateTime` and display it using the German culture format, you can proceed as follows:

### Steps to Convert DateTime with Specific Culture Info:

1. **Use `DateTime.ParseExact` to Parse the String**:
   You will parse the date string using the correct format and the `CultureInfo.InvariantCulture`.

2. **Convert the `DateTime` to the Desired Culture**:
   After parsing the string, you can convert the `DateTime` to the desired culture format (e.g., German culture).

### Example:

Let’s consider the following input:

```
Strinput = "12-22-2024"
```

You want to convert this string into DateTime using the German format (dd/MM/yyyy). Here's how you can achieve this in UiPath:

```
str_datetime = DateTime.ParseExact(Strinput.ToString, "MM-dd-yyyy", System.Globalization.CultureInfo.InvariantCulture).ToString("dd/MM/yyyy", New System.Globalization.CultureInfo("de-DE"))
```

### Explanation:

`DateTime.ParseExact(Strinput.ToString, "MM-dd-yyyy", System.Globalization.CultureInfo.InvariantCulture)`:
This part of the expression converts the input string into a DateTime object based on the format MM-dd-yyyy.

The `CultureInfo.InvariantCulture` ensures that the parsing is done based on a culture-independent format.


`.ToString("dd/MM/yyyy", New System.Globalization.CultureInfo("de-DE"))`:
After parsing the date, we format it into the German date format dd/MM/yyyy.

`New System.Globalization.CultureInfo("de-DE")` specifies that the final date format should be based on the German culture.

### Example Output:

If the input `string Strinput = "12-22-2024"` is parsed and formatted, the output would be:
```
22/12/2024
```

This output follows the German date format `dd/MM/yyyy`.

### Notes:

`CultureInfo.InvariantCulture`: Ensures that the string is parsed in a culture-neutral manner, avoiding any ambiguity related to regional date formats.

`New System.Globalization.CultureInfo("de-DE")`: Specifies the German culture (Germany), which determines the date format to be used for the output.

You can replace `"de-DE"` with any other culture code (e.g., "en-US" for the United States, "fr-FR" for France) to get the output in the desired format for that culture.

### Additional Example with Timezone:

You can also include specific timezone details with `CultureInfo` as needed. For example:

```
str_datetime = DateTime.ParseExact(Strinput.ToString, "MM-dd-yyyy", System.Globalization.CultureInfo.InvariantCulture).ToString("dd/MM/yyyy", New System.Globalization.CultureInfo("de-DE")).ToString("yyyy-MM-dd HH:mm:ss zzz")
```
This would include the `timezone` information in the output.
This method is useful when you need to format the date according to different cultural settings, making your automation robust in dealing with international data formats.
