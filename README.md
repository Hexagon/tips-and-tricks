# SSH nyckelhantering windows

Använd PS när nedan kommandon körs, adminläge. Nyckeln kan sedan användas från lite var som helst, inkl VS Code.

## Installera extra paket i windows

*OpenSSH-klient*

`Add-WindowsCapability -Online -Name OpenSSH.Client`

ssh-agent

`Get-Service -Name ssh-agent | Set-Service -StartupType Automatic`

## Starta ssh-agent

`Start-Service ssh-agent`

## Generera ny nyckel

`ssh-keygen`

## Lägg till nyckel i ssh-agent

`ssh-add $env:USERPROFILE\.ssh\id_rsa`

## Ladda upp nyckel till server

`type $env:USERPROFILE\.ssh\id_rsa.pub | ssh robin@core.huset.nu "cat >> .ssh/authorized_keys"`
