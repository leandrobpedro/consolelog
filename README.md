# Elipse E3/Power Console Log
Message output window for Elipse E3/Power.

## How to use

### Setup
- Add the `consolelog.lib` library to your domain.
- Instantiate the `Console` xobject in a `DataServer` from any `.prj` file in the domain.
- Instantiate the `Output` xcontrol on a screen and bind the `.Console` property in the xcontrol properties window to the xobject added in the previous step, for example, `Dados.Console1`.

### Usage
To write a log entry to the output window, assign the desired message to the `.WriteLine` property of the `Console` xobject, for example:

```vbs
Sub Foo()
  Dim xo
  Set xo = Application.GetObject("Dados.Console1")
  xo.WriteLine = "My message"
End Sub
```

Or create a helper `Sub`:

```vbs
Sub Foo()
  WriteLine "Foo..."
End Sub

Sub Bar()
  WriteLine "Bar..."
End Sub

Sub WriteLine(ByVal s)
  Dim xo
  Set xo = Application.GetObject("Dados.Console1")
  xo.WriteLine = s
End Sub
```

## Properties

| Property | Description | Default |
| --- | --- | --- |
| `WriteLine` | Writes a message to the console buffer. When a value is assigned, a new entry is added to the buffer with the current timestamp as a prefix. The property is automatically cleared after each write. | N/A |
| `MaxLines` | Maximum number of entries retained in the console buffer. When the limit is reached, the oldest entries are discarded to make room for new ones. | `200` |
| `DateTimeFormat` | Date and time format used as the prefix for each log entry. If an invalid format is provided, the default value is applied. See the `E3Format` documentation for the available formats. | `dd/MM/yyyy HH:mm:ss` |
| `TraceEnabled` | When `True`, each log entry is also written to a text file through the `Trace` method, creating a persistent record in addition to the in-memory buffer. The file is saved in the same path as the Domain file with a `.txt` extension. | `False` |
