# Exchange-Folders-Report
This Powershell script will allow you to retreive number of folders in all users' mailbox

//Configure Powershell Session to Exchange (do this even if running on Exchange server).  Use Server FQDN after ConnectionUri.  This can be found in My Computer > Properties. 

PS C:\Windows\system32> $Session = PS C:\Windows\system32> $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri http://GPS-EXCHANGE.gps.local/PowerShell/ -Authentication Kerberos -Credential $UserCredential

//Connect to Powershell session you created above

Import-PSSession $Session

//Verify you have connected to Exchanage Powershell Session

PS C:\Windows\system32> Get-PSSession

PS C:\Windows\system32> $mbx|select Displayname,@{n="FolderIdCount";e={(get-mailboxfoldersta
lect FolderId).count}} | Sort-Object -Property Displayname | export-csv c:\files\results.csv

Results will create a CSV in the format found below:

#TYPE Selected.System.Management.Automation.PSCustomObject
"DisplayName","FolderIdCount"
"Ashtin Odoy","15"
"Austin Williams","25"
"Cristian Lovin","15"
"Discovery Search Mailbox","15"
"Erik Geerdink","15"
"Jason Butler","15"
"Kelly","15"
"Kristina Turley","15"
"Mike Melkonian","15"
"ruben_grigoryan","15"
"Ryan Afdahl","15"
"Shane Donahue","15"
"Test Austin","15"
"Winnie Lam","15"
