# PEN-300 Toolkit

A collection of scripts, executables, and utilities used during the OffSec PEN-300 (OSEP) course labs.

> **Disclaimer:** These tools are intended for authorized penetration testing and educational use only. Unauthorized use against systems you do not own or have permission to test is illegal.

## Structure

```
pen-300/
├── AppLocker-CLM-Bypass/   # Tools for bypassing AppLocker and Constrained Language Mode
├── CSharp/                 # C# payloads and helper utilities
│   ├── ConsoleAppChallenge/  - Shellcode injection payload
│   ├── Helper/               - Shellcode encoder (C# format)
│   ├── HelperVBA/            - Shellcode encoder (VBA format)
│   ├── LatInject/            - Process injection payload
│   ├── POSHBypass/           - PowerShell execution via .NET
│   └── lat2/                 - Service-based AV evasion and execution
└── PowerShell/             # PowerShell reconnaissance and post-exploitation scripts
```

## PowerShell Tools

| Script | Purpose |
|---|---|
| `AMSIBypass.ps1` | AMSI evasion |
| `HostRecon.ps1` | Host enumeration |
| `Invoke-Mimikatz.ps1` | Credential extraction |
| `Invoke-ReflectivePEInjection.ps1` | Reflective PE injection |
| `Invoke-Rubeus.ps1` | Kerberos tooling |
| `Invoke-Seatbelt.ps1` | Security configuration checks |
| `Invoke-WinEnum.ps1` | Windows enumeration |
| `Invoke-winPEAS.ps1` | Privilege escalation checks |
| `PowerView_dev.ps1` | Active Directory enumeration |
| `powermad.ps1` | AD exploitation utilities |
| `pwshShellcodeRunnerX64.txt` | x64 shellcode runner |

## C# Tools

| Project | Purpose |
|---|---|
| `ConsoleAppChallenge` | Encrypted shellcode injection with sandbox evasion |
| `Helper` / `HelperVBA` | Caesar cipher encoder for shellcode payloads |
| `LatInject` | Process injection into target service |
| `lat2` | Remote service modification for AV evasion |
| `POSHBypass` | PowerShell download-and-execute via .NET Installer class |

## Usage

- **PowerShell scripts** can be loaded with `. .\ScriptName.ps1` or downloaded in-memory via `IEX`.
- **C# projects** should be compiled with Visual Studio or `dotnet build`. Some are designed to run via `MSBuild` or `InstallUtil`.
- **AppLocker bypass** executables are pre-compiled and ready to use.

## Requirements

- Windows target environment
- Visual Studio or .NET SDK (for compiling C# projects)
- PowerShell 5.1+ (for PowerShell scripts)
- Msfvenom (for generating fresh shellcode payloads)
