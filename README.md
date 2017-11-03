# Nutdeep
Nutdeep - A light memory manager library made by C# lovers


### ProcessHandler

By string
```csharp
using (var handler = new ProcessHandler("ProcessName")) { ... }
```
By process id (System.Int32)
```csharp
using (var handler = new ProcessHandler(ProcessId)) { ... }
```
By process (System.Diagnostics.Process)
```csharp
using (var handler = new ProcessHandler(Process)) { ... }
```

If you are looking for Chrome Showckwave Flash process
```csharp
using (var handler = new ProcessHandler("chrome&flash")) { ... }
```

You can find easily process that runs **FlashPlayer** this way
```csharp
//using System.Linq
var flashPlayerProcesses = Process.GetProcesses()
  .Where(p => p.RunsFlashPlayer()).ToArray();
```



### MemoryScanner
```csharp
using (var handler = new ProcessHandler(//))
{
  //MemoryScanner needs for ProcessAccess (ProcessHandler : ProcessAccess)
  MemoryScanner scanner = handler;
  scanner.SetSettings(new ScanSettings()
  {
    Writable = ScanType.ONLY
  });
}
```
Click [here](https://github.com/Adversities/Nutdeep/blob/master/Nutdeep/Tools/ScanSettings.cs) to check how ScanSettings is setup by default *(that will be the setup if you dont specific it)*

Where T might be:

* Char
* Single 
* Byte[]
* String
* Boolean
* Decimal
* Int16/UInt16
* Int32/UInt32
* Int64/UInt64
* Signature : String

To perfom a scan
```csharp
var addresses = scanner.SearchFor<T>(T obj);
```

Scan by signature
```csharp
var addresses = scanner.SearchFor<Signature>("0I ?? LO ?? VE ?? CO ?? ?? DE");
```

To perform a next scan
```csharp
var nextAddresses = scanner.NextSearchFor<T>(IntPtr[] addresses, T obj);
```
Next scan by signature
```csharp
var nextAddresses = scanner.NextSearchFor<Signature>(addresses, "0I ?? LO ?? VE ?? CO ?? ?? DE");
```

# THIS IS INCOMPLETE, GONNA DONE THIS AFTER THE TRAVEL


TODO List:
* Multithreading scan
