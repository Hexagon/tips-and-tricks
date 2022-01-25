# Hexagon's tips & tricks

This is mostly for my own use, but feel free to get inspired.

*   [Windows 10 SSH key management](#windows-10-ssh-key-management)

(more to come)

## Windows 10 SSH key management

Good to know: ssh-agent is used by PowerShell, VS Code and (believe it or not) cmd.

Use PowerShell for running the commands below.

### Enable extra Windows features (Requires admin-shell)

*OpenSSH-client*

`Add-WindowsCapability -Online -Name OpenSSH.Client`

ssh-agent

`Get-Service -Name ssh-agent | Set-Service -StartupType Automatic`

### Start ssh-agent

`Start-Service ssh-agent`

### Genererate new key

`ssh-keygen`

### Add key to ssh-agent

`ssh-add $env:USERPROFILE\.ssh\id_rsa`

### Upload key to server

`type $env:USERPROFILE\.ssh\id_rsa.pub | ssh user@host "cat >> .ssh/authorized_keys"`
