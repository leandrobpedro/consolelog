# Elipse E3/Power Console Log

Library for managing logs in Elipse E3/Power. Allows displaying messages in a console window, storing them internally, and exporting to a text file.

---

## How to Use

### 1. Setup

1. Add the `consolelog.lib` library to your domain.
2. Instantiate the `Console Log Engine` xObject in a `DataServer` within any project (`.prj`) in the domain.
3. Instantiate the `Immediate window` xControl on a screen and link its `.Console` property to the previously created xObject, for example:
   ```
   Data.consolelog_Engine1
   ```

### 2. Usage

To write a message to the console, use the `.WriteLine` property of the `ConsoleLog` xObject:

```vbs
Sub ExampleMessage()
    Dim consoleLog
    Set consoleLog = Application.GetObject("Data.consolelog_Engine1")
    consoleLog.WriteLine = "Starting verification process..."
End Sub
```

Or create a helper function for simpler usage:

```vbs
Sub WriteLog(ByVal message)
    Dim consoleLog
    Set consoleLog = Application.GetObject("Data.ConsoleLog1")
    consoleLog.WriteLine = message
End Sub

Sub ProcessData()
    WriteLog "Processing started"
    ' processing code...
    WriteLog "Processing completed successfully"
End Sub
```