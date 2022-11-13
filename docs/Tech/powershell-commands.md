## Commands/Scripts
#### list all computers in an OU
```powershell
Get-ADComputer -Filter * -SearchBase "OU=, DC=domain, DC=com" | Format-Table Name
```

#### list OUs by distinguished name
 ```powershell
Get-ADOrganizationalUnit -Filter 'Name -like "*"' | Format-Table Name, DistinguishedName -A
 ```

#### set unrestricted restriction policy for the current user
 ```powershell 
Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Scope CurrentUser
 ```

#### get domain info
```powershell
Get-ADDomain test.com
```

#### stop and disable a service from text file
```powershell
Get-Service -Name Spooler -ComputerName (Get-Content C:\Users\rt\notes\powershell\cylance_disable\servers.txt) | Stop-Service -PassThru | Set-Service -StartupType Disabled
```

#### launch powershell with different credentials
```powershell
Start Powershell -Credential ""
```

#### get disabled users by account name
```powershell
Get-ADUser -Filter {Enabled -eq $false} | FT samAccountName
```

#### get domain admins
```powershell
Get-ADGroupmember -Identity "Domain Admins" | FT name -A
```

#### get passwords set to never expire
```powershell
get-aduser -filter * -properties Name, PasswordNeverExpires | where { $_.passwordNeverExpires -eq "true" } | Select-Object Name,Enabled | Export-csv c:\working\pw_never_expires.csv -NoTypeInformation
```

#### get user account information
```powershell
get-aduser -filter * -Properties Enabled,samAccountName,LastLogonDate,PasswordLastSet | Export-csv c:\powershell\password-set.csv -NoTypeInformation
```

#### get stale users >90d
```powershell
$Days = 90
$Time = (Get-Date).Adddays(-($Days))

Get-ADUser -Filter {LastLogonTimeStamp -lt $Time} -Properties * | Select-Object samAccountName, Enabled, LastLogonDate | Export-csv c:\working\powershell\ad-testing\stale-users.csv -NoTypeInformation
```

#### get stale computers >90d
```powershell
$Days = 90
$Time = (Get-Date).Adddays(-($Days))

Get-ADComputer -server dc_hostname -Filter {LastLogonTimeStamp -lt $Time} -Properties * | Select-Object samAccountName, Enabled, LastLogonDate, DistinguishedName
```

#### get last logon date of a computer 
```powershell
Get-ADComputer -Filter * -Properties * | Sort LastLogonDate | FT Name, LastLogonDate -Autosize
```

#### get locked account info
```powershell
Get-WinEvent -ComputerName dc_hostname -FilterHashtable @{logname='security'; id=4740}
```

#### get enabled user count
```powershell
(Get-ADUser -server dc_hostname -Filter {Enabled -eq $true}).Count
``` 

#### test connection to service
```powershell
Test-Connection google.com
```

#### Test Connection to Server
```powershell
test-netconnection server.domain.com -port 14501
```

#### Get AD Users enabled status, company, and division
```powershell
 get-aduser -properties * -filter * | Select samaccountname,name,enabled,company,division | Export-Csv -path C:\working\users.csv
```