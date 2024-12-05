# Get Current Date and Time in UiPath

In UiPath, you can use the following activities and expressions to get the current date and time as a string and a `DateTime` variable.

## 1. Get Current Date and Time as String

To get the current date and time in the format `"dd/MM/yyyy hh:mm:ss"`, use the `Assign` activity.

### Assign Activity:
- **To**: `currentDateString`
- **Value**: `Now.ToString("dd/MM/yyyy hh:mm:ss")`

### Example:
```plaintext
currentDateString = Now.ToString("dd/MM/yyyy hh:mm:ss")