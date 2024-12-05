# Convert an OADate in Excel to DateTime or String DateTime in UiPath

In Excel, dates are often represented as OADates (which is the number of days since January 1, 1900). You can convert these OADates to `DateTime` objects in UiPath and format them as strings in the desired date format (e.g., "dd-MMM-yyyy").

### Scenario:

Suppose you have an OADate value, such as `43800`, which represents the date in Excel, and you need to convert it to the string `"1-Dev-2022"` in the format `"dd-MMM-yyyy"`.

### Steps to Convert OADate to DateTime or String DateTime:

1. **Convert the OADate to `DateTime`**:
   Use the `DateTime.FromOADate` method to convert the OADate value to a `DateTime` object.
   
2. **Format the DateTime into the Required Format**:
   After converting to `DateTime`, you can use `.ToString("dd-MMM-yyyy")` to get the desired format.

### Example:

Suppose the input value (OADate) is stored in `Strinput`:

```
Strinput = "43800"   // OADate value
```

Now, you can convert this OADate to a `DateTime` in the required format using the following UiPath expression:

```
str_datetime = DateTime.FromOADate(Convert.ToDouble(Strinput.ToString)).ToString("dd-MMM-yyyy")
```

### Explanation:

- **Convert.ToDouble(Strinput.ToString)**:

This converts the string value of Strinput (which contains the OADate) to a double, which is required by DateTime.FromOADate.

- **DateTime.FromOADate(Convert.ToDouble(Strinput.ToString))**:

This converts the OADate (a numeric value) to a DateTime object.

- **.ToString("dd-MMM-yyyy")**:

This formats the DateTime into the desired string format "dd-MMM-yyyy", which will display the date in the form of 01-Dec-2022.