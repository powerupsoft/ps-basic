# Managing Services 

**List all services**

    Get-Service

**Start a service**

    Start-Service -Name "Spooler"

**Stop a service**

    Stop-Service -Name "Spooler"

**Restart a service**

    Restart-Service -Name "Spooler"

**Check the status of a specific service**

    Get-Service -Name "Spooler" | Select-Object Status
## Managing Processes

**List all running processes**

    Get-Process

**Stop a specific process by name**

    Stop-Process -Name "notepad" -Force

**Start a new instance of Notepad**

    Start-Process -FilePath "notepad.exe"

    ## Script Example
## Script Examples
**Print the OS you are logged in**
```powershell
if ($IsLinux) {
    Write-Host "Linux"
}
elseif ($IsMacOS) {
    Write-Host "macOS"
}
elseif ($IsWindows) {
    Write-Host "Windows"
}
```
**More complex example**
```powershell
if ($PSVersionTable.PSEdition -eq "Core") {
    # Cross-platform PowerShell Core
    $os = [System.Runtime.InteropServices.RuntimeInformation]::IsOSPlatform([System.Runtime.InteropServices.OSPlatform]::Linux)
    if ($os) {
        Write-Host "Linux"
    }
    elseif ([System.Runtime.InteropServices.RuntimeInformation]::IsOSPlatform([System.Runtime.InteropServices.OSPlatform]::OSX)) {
        Write-Host "macOS"
    }
    elseif ([System.Runtime.InteropServices.RuntimeInformation]::IsOSPlatform([System.Runtime.InteropServices.OSPlatform]::Windows)) {
        Write-Host "Windows"
    }
}
else {
    # PowerShell Desktop (Windows only)
    Write-Host "Windows"
}

```
