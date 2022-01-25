# Windows SSH key management

ssh-agent is used by PowerShell, VS Code and even cmd.

Use PowerShell

## Enable extra Windows features (Requires admin-shell)

*OpenSSH-klient*

`Add-WindowsCapability -Online -Name OpenSSH.Client`

ssh-agent

`Get-Service -Name ssh-agent | Set-Service -StartupType Automatic`

## Start ssh-agent

`Start-Service ssh-agent`

## Genererate new key

`ssh-keygen`

## Add key to ssh-agent

`ssh-add $env:USERPROFILE\.ssh\id_rsa`

## Upload key to server

`type $env:USERPROFILE\.ssh\id_rsa.pub | ssh user@host "cat >> .ssh/authorized_keys"`
