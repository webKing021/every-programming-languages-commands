# Windows Commands Reference

## File System Navigation

```powershell
# Display current directory
pwd
Get-Location

# List directory contents
dir
Get-ChildItem
ls
dir /a       # Show hidden files
dir /s       # Recursive listing
dir /b       # Bare format (names only)
dir /o:n     # Sort by name
dir /o:s     # Sort by size
dir /o:d     # Sort by date
dir /o:-d    # Sort by date (newest first)

# Change directory
cd path\to\directory
Set-Location path\to\directory
cd ..        # Parent directory
cd \         # Drive root
cd %USERPROFILE%  # Home directory
pushd path   # Change directory and save previous
popd         # Return to previous directory

# Create directory
mkdir directory_name
md directory_name
New-Item -ItemType Directory -Path directory_name

# Remove directory
rmdir directory_name
rd directory_name
rmdir /s /q directory_name  # Remove with contents, no confirmation
Remove-Item directory_name -Recurse -Force

# Copy files/directories
copy source destination
copy /y source destination  # No confirmation
xcopy source destination /s /e /h /i  # Recursive with hidden files
robocopy source destination /e  # Enhanced recursive copy
Copy-Item source destination
Copy-Item -Recurse source destination  # Copy directories recursively

# Move/rename files/directories
move source destination
ren file_name new_name
Move-Item source destination
Rename-Item file_name new_name

# Find files/directories
dir /s /b filename
where filename
Get-ChildItem -Path C:\ -Recurse -Filter filename
Get-ChildItem -Path C:\ -Recurse -Include *pattern*

# Show disk usage
dir /s directory  # Size of directory contents
Get-ChildItem -Recurse | Measure-Object -Property Length -Sum

# Show disk space
wmic logicaldisk get deviceid, size, freespace
Get-Volume
Get-PSDrive -PSProvider FileSystem
```

## File Operations

```powershell
# Create empty file
type nul > filename
echo $null > filename
New-Item -ItemType File -Path filename

# View file contents
type filename
more filename  # Paginated view
Get-Content filename
cat filename

# View beginning/end of file
more +n filename  # First n lines
Get-Content filename -Head 10  # First 10 lines
Get-Content filename -Tail 10  # Last 10 lines

# Compare files
fc file1 file2
comp file1 file2
Compare-Object (Get-Content file1) (Get-Content file2)

# Sort file contents
sort filename
Get-Content filename | Sort-Object
Get-Content filename | Sort-Object -Descending

# Remove duplicates
Get-Content filename | Sort-Object -Unique

# Combine files
type file1 file2 > combined_file
copy /b file1+file2 combined_file
Get-Content file1, file2 | Set-Content combined_file

# Create file with content
echo content > filename
Set-Content -Path filename -Value "content"

# File attributes
attrib filename
attrib +r filename  # Set read-only
attrib -r filename  # Remove read-only
attrib +h filename  # Set hidden
attrib -h filename  # Remove hidden
Get-ItemProperty filename
Set-ItemProperty filename -Name Attributes -Value "ReadOnly"

# File ownership and permissions
icacls filename
icacls filename /grant username:(R,W)  # Grant read/write
icacls filename /deny username:(W)      # Deny write
icacls filename /remove username        # Remove permissions
Get-Acl filename
Set-Acl filename
```

## Text Processing

```powershell
# Search file contents
findstr "pattern" filename
findstr /i "pattern" filename  # Case-insensitive
findstr /s "pattern" directory  # Recursive search
findstr /v "pattern" filename  # Invert match
findstr /n "pattern" filename  # Show line numbers
Select-String -Pattern "pattern" -Path filename
Select-String -Pattern "pattern" -Path directory\*.txt -Recurse

# Regular expression search
findstr /r "regex" filename
Select-String -Pattern "regex" -Path filename

# Search and replace
(Get-Content filename) -replace "pattern", "replacement" | Set-Content filename

# Advanced text processing
Get-Content filename | ForEach-Object { $_ -replace "pattern", "replacement" } | Set-Content newfile

# Cut columns
for /f "tokens=1,3 delims=," %i in (filename) do @echo %i %j
Get-Content filename | ForEach-Object { $_.Split(',')[0,2] -join ' ' }

# Count pattern occurrences
findstr /i /c:"pattern" filename | find /c /v ""
Select-String -Pattern "pattern" -Path filename | Measure-Object | Select-Object -ExpandProperty Count
```

## Process Management

```powershell
# List processes
tasklist
Get-Process
ps

# Find specific process
tasklist | findstr "process_name"
Get-Process -Name process_name
Get-Process | Where-Object { $_.ProcessName -like "*process*" }

# Process details
tasklist /v
Get-Process | Format-List *
Get-Process -Id PID | Format-List *

# Kill processes
taskkill /im process_name.exe
taskkill /pid PID
taskkill /f /im process_name.exe  # Force kill
Stop-Process -Name process_name
Stop-Process -Id PID
Stop-Process -Name process_name -Force

# Start process
start program_name
Start-Process program_name
Start-Process program_name -ArgumentList "arg1 arg2"

# Run as administrator
runas /user:administrator program_name
Start-Process program_name -Verb RunAs

# Services
sc query                      # List all services
sc query service_name         # Query specific service
sc start service_name         # Start service
sc stop service_name          # Stop service
sc config service_name start= auto  # Set to automatic start
Get-Service
Get-Service -Name service_name
Start-Service -Name service_name
Stop-Service -Name service_name
Set-Service -Name service_name -StartupType Automatic

# System resource usage
wmic cpu get loadpercentage   # CPU usage
Get-Counter '\Processor(_Total)\% Processor Time'
Get-Counter '\Memory\Available MBytes'
```

## User Management

```powershell
# Current user info
whoami
$env:USERNAME
[System.Security.Principal.WindowsIdentity]::GetCurrent().Name

# User information
net user                      # List all users
net user username             # Specific user info
Get-LocalUser
Get-LocalUser -Name username

# Create/modify/delete users
net user username password /add  # Create user
net user username /delete        # Delete user
net user username newpassword    # Change password
New-LocalUser -Name username -Password (ConvertTo-SecureString "password" -AsPlainText -Force)
Remove-LocalUser -Name username

# Group information
net localgroup                # List all groups
net localgroup groupname      # List group members
Get-LocalGroup
Get-LocalGroupMember -Group groupname

# Group management
net localgroup groupname username /add    # Add user to group
net localgroup groupname username /delete # Remove user from group
Add-LocalGroupMember -Group groupname -Member username
Remove-LocalGroupMember -Group groupname -Member username

# Create/delete groups
net localgroup groupname /add     # Create group
net localgroup groupname /delete  # Delete group
New-LocalGroup -Name groupname
Remove-LocalGroup -Name groupname
```

## System Information

```powershell
# System info
systeminfo
Get-ComputerInfo

# Operating system info
wmic os get Caption,Version,OSArchitecture
Get-CimInstance Win32_OperatingSystem | Select-Object Caption,Version,OSArchitecture

# Computer name
hostname
$env:COMPUTERNAME

# Hardware info
wmic cpu get Name,NumberOfCores,NumberOfLogicalProcessors
wmic memorychip get Capacity,Speed
wmic diskdrive get Model,Size,Status
Get-CimInstance Win32_Processor
Get-CimInstance Win32_PhysicalMemory
Get-CimInstance Win32_DiskDrive

# Network info
ipconfig
ipconfig /all                  # Detailed network info
Get-NetIPAddress
Get-NetAdapter

# System logs
eventlog                       # List event logs
eventlog /L:System             # View System log
Get-EventLog -LogName System -Newest 50
Get-WinEvent -LogName System -MaxEvents 50

# System uptime
wmic os get lastbootuptime
(Get-CimInstance Win32_OperatingSystem).LastBootUpTime
(Get-Date) - (Get-CimInstance Win32_OperatingSystem).LastBootUpTime
```

## Networking

```powershell
# Network interfaces
ipconfig
ipconfig /all                  # Detailed network info
Get-NetIPAddress
Get-NetAdapter

# Network connectivity
ping host                      # ICMP echo
ping -t host                   # Continuous ping
ping -n 10 host                # 10 pings
Test-Connection host
Test-Connection host -Count 10

# Trace route
tracert host
Test-NetConnection host -TraceRoute

# DNS lookup
nslookup domain
Resolve-DnsName domain

# Network connections
netstat -ano                   # All connections with PID
netstat -ab                    # Connections with process names
Get-NetTCPConnection
Get-NetTCPConnection -State Listen

# Remote connections
ssh user@host                  # SSH (Windows 10+)
New-PSSession -ComputerName host -Credential username

# File transfer
scp file user@host:/path       # Secure copy (Windows 10+)
robocopy source destination /e # Enhanced copy

# Network configuration
ipconfig /release              # Release DHCP lease
ipconfig /renew                # Renew DHCP lease
ipconfig /flushdns             # Flush DNS cache
Clear-DnsClientCache

# Firewall
netsh advfirewall show allprofiles                    # Show firewall status
netsh advfirewall firewall show rule name=all         # Show all rules
netsh advfirewall firewall add rule name="Allow Port" dir=in action=allow protocol=TCP localport=80
Get-NetFirewallRule
New-NetFirewallRule -DisplayName "Allow Port 80" -Direction Inbound -Action Allow -Protocol TCP -LocalPort 80

# Network shares
net share                      # List shares
net share sharename=C:\path    # Create share
net share sharename /delete    # Delete share
Get-SmbShare
New-SmbShare -Name sharename -Path C:\path
Remove-SmbShare -Name sharename
```

## Package Management

```powershell
# Windows Package Manager (winget) - Windows 10+
winget search app_name         # Search for application
winget install app_name        # Install application
winget uninstall app_name      # Uninstall application
winget list                    # List installed applications
winget upgrade                 # List available upgrades
winget upgrade --all           # Upgrade all applications

# Chocolatey (requires installation)
choco search package_name      # Search for package
choco install package_name     # Install package
choco uninstall package_name   # Uninstall package
choco list --local-only        # List installed packages
choco upgrade package_name     # Upgrade package
choco upgrade all              # Upgrade all packages

# PowerShell modules
Find-Module module_name        # Search for module
Install-Module module_name     # Install module
Uninstall-Module module_name   # Uninstall module
Get-InstalledModule            # List installed modules
Update-Module module_name      # Update module
Update-Module                  # Update all modules

# Windows features
DISM /Online /Get-Features                    # List all features
DISM /Online /Enable-Feature /FeatureName:name  # Enable feature
DISM /Online /Disable-Feature /FeatureName:name # Disable feature
Get-WindowsOptionalFeature -Online
Enable-WindowsOptionalFeature -Online -FeatureName name
Disable-WindowsOptionalFeature -Online -FeatureName name
```

## Compression & Archives

```powershell
# Built-in ZIP support
Compact /C /S:folder           # Compress folder with NTFS compression
Compact /U /S:folder           # Uncompress folder

# PowerShell compression
Compress-Archive -Path source -DestinationPath archive.zip
Expand-Archive -Path archive.zip -DestinationPath destination

# Extract specific files
Expand-Archive -Path archive.zip -DestinationPath destination -Force

# Update existing archive
Compress-Archive -Path source -DestinationPath archive.zip -Update

# 7-Zip (if installed)
7z a archive.7z folder         # Create archive
7z x archive.7z -odestination  # Extract archive
7z l archive.7z                # List contents
```

## PowerShell Scripting

```powershell
# Variables
$var = "value"
$var = 123
$var = @("item1", "item2")      # Array
$var = @{key1="value1"; key2="value2"}  # Hashtable

# Conditionals
if ($condition) {
    # commands
} elseif ($condition2) {
    # commands
} else {
    # commands
}

# Loops
foreach ($item in $collection) {
    # commands
}

for ($i=0; $i -lt 10; $i++) {
    # commands
}

while ($condition) {
    # commands
}

do {
    # commands
} while ($condition)

do {
    # commands
} until ($condition)

# Functions
function Function-Name {
    param(
        [Parameter(Mandatory=$true)]
        [string]$Parameter1,
        
        [int]$Parameter2 = 0
    )
    
    # commands
    return $value
}

# Error handling
try {
    # commands
} catch {
    # error handling
} finally {
    # always executed
}

# Pipeline
Get-Process | Where-Object { $_.CPU -gt 10 } | Sort-Object CPU -Descending

# Output
Write-Host "Message"            # Display message
Write-Output $var               # Output to pipeline
Write-Error "Error message"     # Write error
Write-Warning "Warning message" # Write warning
Write-Verbose "Verbose message" # Write verbose message
Write-Debug "Debug message"     # Write debug message
```

## Scheduled Tasks

```powershell
# List tasks
schtasks /query
Get-ScheduledTask

# Create task
schtasks /create /tn "TaskName" /tr "command" /sc daily /st 10:00
New-ScheduledTask -Action (New-ScheduledTaskAction -Execute "command") -Trigger (New-ScheduledTaskTrigger -Daily -At 10am)

# Run task
schtasks /run /tn "TaskName"
Start-ScheduledTask -TaskName "TaskName"

# Delete task
schtasks /delete /tn "TaskName" /f
Unregister-ScheduledTask -TaskName "TaskName" -Confirm:$false

# Modify task
schtasks /change /tn "TaskName" /st 12:00
Set-ScheduledTask -TaskName "TaskName" -Trigger (New-ScheduledTaskTrigger -Daily -At 12pm)
```

## Registry

```powershell
# Navigate registry
cd HKLM:\SOFTWARE
Set-Location HKCU:\Software\Microsoft\Windows

# List keys/values
dir
Get-ChildItem
Get-ItemProperty .

# Create key
New-Item -Path HKCU:\Software\MyApp

# Create/modify value
New-ItemProperty -Path HKCU:\Software\MyApp -Name "Setting" -Value "Value" -PropertyType String
Set-ItemProperty -Path HKCU:\Software\MyApp -Name "Setting" -Value "NewValue"

# Delete value
Remove-ItemProperty -Path HKCU:\Software\MyApp -Name "Setting"

# Delete key
Remove-Item -Path HKCU:\Software\MyApp -Recurse

# Registry commands
reg query "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion"
reg add "HKCU\Software\MyApp" /v "Setting" /t REG_SZ /d "Value"
reg delete "HKCU\Software\MyApp" /f
```

## System Administration

```powershell
# System shutdown/restart
shutdown /s /t 0               # Shutdown immediately
shutdown /r /t 0               # Restart immediately
shutdown /s /t 60 /c "Message" # Shutdown in 60 seconds with message
shutdown /a                    # Abort shutdown
Restart-Computer
Stop-Computer

# Disk management
diskpart                       # Interactive disk management
defrag C: /O                   # Optimize drive
chkdsk C: /f                   # Check disk and fix errors
chkdsk C: /r                   # Check disk, fix errors, recover data
Optimize-Volume -DriveLetter C -Defrag
Repair-Volume -DriveLetter C -Scan

# Windows updates
wuauclt /detectnow             # Check for updates
wuauclt /updatenow             # Install updates
Get-WindowsUpdate
Install-WindowsUpdate

# System file checker
sfc /scannow                   # Scan and repair system files
DISM /Online /Cleanup-Image /RestoreHealth  # Repair Windows image

# Task Manager from command line
taskmgr
Get-Process | Sort-Object -Property CPU -Descending | Select-Object -First 10

# System restore
rstrui.exe                     # System restore UI
Checkpoint-Computer -Description "Restore Point Description"
Restore-Computer -RestorePoint pointNumber
```

## Security & Permissions

```powershell
# File permissions
icacls filename
icacls filename /grant username:(R,W)  # Grant read/write
icacls filename /deny username:(W)      # Deny write
icacls filename /remove username        # Remove permissions
Get-Acl filename
Set-Acl filename

# Take ownership
takeown /f filename
takeown /r /d y /f directory           # Recursive for directory

# User Account Control
msconfig                       # System Configuration utility

# Windows Defender
MpCmdRun -Scan -ScanType 2    # Full scan
MpCmdRun -Scan -ScanType 1    # Quick scan
Start-MpScan -ScanType FullScan

# Firewall
netsh advfirewall show allprofiles                    # Show firewall status
netsh advfirewall firewall show rule name=all         # Show all rules
netsh advfirewall firewall add rule name="Allow Port" dir=in action=allow protocol=TCP localport=80
Get-NetFirewallRule
New-NetFirewallRule -DisplayName "Allow Port 80" -Direction Inbound -Action Allow -Protocol TCP -LocalPort 80

# Encryption
cipher /e directory            # Encrypt directory
cipher /d directory            # Decrypt directory
```

## Miscellaneous

```powershell
# Environment variables
set                            # Display all variables
echo %VARIABLE%                # Display variable
set VARIABLE=value             # Set variable (session only)
setx VARIABLE value            # Set variable (permanent)
$env:VARIABLE                  # Display variable in PowerShell
$env:VARIABLE = "value"        # Set variable in PowerShell
[Environment]::SetEnvironmentVariable("VARIABLE", "value", "Machine")  # System-wide

# Command history
doskey /history                # CMD history
Get-History                    # PowerShell history
Invoke-History 10              # Execute history item 10

# Help and documentation
help command                   # PowerShell help
Get-Help command               # PowerShell help
Get-Help command -Examples     # PowerShell help with examples
command /?                     # CMD help

# Clipboard
clip < filename                # Copy file content to clipboard
echo text | clip               # Copy text to clipboard
Get-Content filename | Set-Clipboard
Set-Clipboard -Value "text"

# Date and time
date /t                        # Display date
time /t                        # Display time
Get-Date                       # Display date and time
Get-Date -Format "yyyy-MM-dd" # Formatted date

# File associations
assoc                          # List all associations
assoc .txt                     # Show association for .txt
assoc .txt=txtfile             # Set association for .txt
ftype txtfile="C:\Program Files\Notepad++\notepad++.exe" "%1"
Get-ItemProperty HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.txt

# Path management
path                           # Display PATH
path %PATH%;C:\new\path       # Add to PATH (session only)
setx PATH "%PATH%;C:\new\path" # Add to PATH (permanent)
$env:Path += ";C:\new\path"   # Add to PATH in PowerShell
```