# Breakdown of the Process
Write this code in Outlook VBA

### Starting the Process:
The code first sends a request to the UiPath Orchestrator to start a job. This job is associated with the process you are working with (e.g., automating some task in UiPath). The `StartJobs` API is called to initiate the process, and the process ID (`ProcId`) is extracted from the response.

### Checking the Status:
After starting the process, the code enters a loop that is designed to check the status of the job periodically to see if it is finished.

### Sleep Between Checks:
Inside the loop, the `Sleep` function is called to pause the execution for 5 seconds (5000 milliseconds) before checking the status again. This is done to avoid making too many requests in a short amount of time.

### Job State Check:
Each time the loop runs, it sends a GET request to the UiPath Orchestrator to check the state of the job using the job’s `ProcId`. The response contains the current state of the job, which can be one of the following:

- **"Successful"**: The job finished successfully.
- **Other states like "Running", "Failed", or "Pending"**: The job is still in progress or encountered an issue.

### Exit Condition:
The loop checks if the job's state is "successful". If it is, the loop will exit early (using `Exit Do`). If the job is still running or hasn't finished, the loop continues checking the status up to 12 iterations (in this case, roughly 1 minute of total wait time).

## Key Part of the Code (Status Check and Loop):

```vba
' Loop to see if the process is done
Dim i As Integer
i = 1
Do While i < 12
    Sleep 5000 ' Wait for 5 seconds

    ' Send a GET request to check the job status
    req.Open "GET", myUrl, False
    req.SetRequestHeader "Content-Type", "application/json"
    req.SetRequestHeader "X-UIPATH-TenantName", "YOUR TENANT NAME"
    req.SetRequestHeader "Authorization", Auth
    req.Send Body
    Resp = req.ResponseText

    ' Parse the response to check the job status
    Tmp = Mid(Resp, InStr(Resp, "State") + 8, InStr(Resp, "JobPriority") - InStr(Resp, "State") - 11)
    Tmp = LCase(Tmp) ' Convert to lowercase for easy comparison

    If (Tmp = "successful") Then
        Exit Do ' Exit the loop if the job is successful
    End If

    i = i + 1
Loop
