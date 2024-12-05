# Get Current Date and Time in UiPath

In UiPath, you can use the following activities and expressions to get the current date and time as a string and a `DateTime` variable.

## 1. Get Current Date and Time as String

To get the current date and time in the format `"dd/MM/yyyy hh:mm:ss"`, use the `Assign` activity.

### Assign Activity:
- **To**: `currentDateString`
- **Value**: `Now.ToString("dd/MM/yyyy hh:mm:ss")`

### Example:
```currentDateString = Now.ToString("dd/MM/yyyy hh:mm:ss")

If the `current date` and time are `4th December 2024, 02:30:45`, the `currentDateString` will have the value:
`04/12/2024 02:30:45`


###Get Current Date and Time as DateTime Variable
To store the current date and time as a `DateTime` variable, simply use:

###Assign Activity:
To: `currentDateTime`
Value: `Now`
###Example:
```
currentDateTime = Now

If the current date and time are `4th December 2024, 02:30:45 PM`, the `currentDateTime` will hold the DateTime value:
`12/4/2024 2:30:45 PM`

###Complete Steps:
###Assign Activity for String Format:
- **To**: `currentDateString`
- **Value**: `Now.ToString("dd/MM/yyyy hh:mm:ss")`

###Assign Activity for DateTime Format:
- **To**: `currentDateTime`
- **Value**: `Now`
###Example Workflow:

Assign (to get DateTime as a string):
```
currentDateString = Now.ToString("dd/MM/yyyy hh:mm:ss")

Assign (to get DateTime as a DateTime type):

```
currentDateTime = Now

###Result:
`currentDateString`: "04/12/2024 02:30:45" (as a string)
`currentDateTime`: 12/4/2024 2:30:45 PM (as a `DateTime` variable)

Now you have `currentDateString` as a `string` and `currentDateTime` as a `DateTime` variable.
