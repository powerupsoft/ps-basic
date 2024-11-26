$\Huge\color{#9900FF}{\textsf{Managing Services}}$

$\normalsize\color{#2ecc71}{\textsf{List all services}}$

    Get-Service

**Start a service**

    Start-Service -Name "Spooler"

**Stop a service**

    Stop-Service -Name "Spooler"

**Restart a service**

    Restart-Service -Name "Spooler"

**Check the status of a specific service**

    Get-Service -Name "Spooler" | Select-Object Status
$\Huge\color{#9900FF}{\textsf{Managing Proceses}}$

**List all running processes**

    Get-Process

**Stop a specific process by name**

    Stop-Process -Name "notepad" -Force

**Start a new instance of Notepad**

    Start-Process -FilePath "notepad.exe"

    ## Script Example
$\Huge\color{#9900FF}{\textsf{Script Examples}}$

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
$\Large\color{Lime}{\textsf{Explanation:}}$

1.  **`$PSVersionTable.PSEdition`**
    
    -   Checks if the current PowerShell session is running **Core** (cross-platform) or **Desktop** (Windows only).
2.  **`[System.Runtime.InteropServices.RuntimeInformation]`**
    
    -   A .NET class used to determine the operating system type.
    -   `IsOSPlatform()` checks for specific platforms like Linux, macOS (OSX), or Windows.
3.  **Platform Detection Logic:**
    
    -   If PowerShell Core is running, it evaluates the OS and prints the appropriate message.
    -   If it's PowerShell Desktop, it assumes **Windows** (since Desktop runs only on Windows).
  
    **Reference:** [RuntimeInformation Class (System.Runtime.InteropServices) | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/api/system.runtime.interopservices.runtimeinformation?view=net-9.0)

