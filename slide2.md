# Managing Services
## List all services

    Get-Service

## Start a service

    Start-Service -Name "Spooler"

## Stop a service

    Stop-Service -Name "Spooler"

## Restart a service

    Restart-Service -Name "Spooler"

## Check the status of a specific service

    Get-Service -Name "Spooler" | Select-Object Status
