# Windows basics

## OS info

Find information about the system:<br>
```
Get-WmiObject
```

Version and build of the system:<br>
```
Get-WmiObject -Class win32_OperatingSystem | select Version,BuildNumber
```

Other useful classes:<br>

| Class | Use |
| ----- | --- |
| Win32\_Process | process listing |
| Win32\_Service | service listing |
| Win32\_Bios | I/O information |

## System structure

root directory: \<drive\_letter\>:\ (Commonly C drive)<br>

### Exploring directories

The **dir** command list files inside a directory.<br>

The **tree** command shows a graphical view of the directory structure.<br>

We can walk through directories using: <br>
```
tree c:\ /f | more
```

### Integrity Control Access List

We can list NTFS permissions using the **icacls** command.<br>
```
icacls C:\Users /grant joe:f
```
```
icacls C:\Users /remove joe
```

## Share

To connect to a share folder: <br>
```
smbclient -L IpadressOfTarget -U username
```

To mount share folder to our system: <br>
```
sudo mount -t cifs -o username=username,password=pwd //IpOfTarget/FolderName /home/user/
```

The **net share** command view all share folder on the system.<br>
We can also use the tool **Computer management**.<br>

**Event viewer** allows us to access the logs of every application.<br>

## Services

We can manage services via **services.msc** or with the **Get-Service** command:<br>
```
Get-Service | ? {$_.Status -eq "Running"} | select -First 2 | fl
```

**Sysinternal tool suite** is a set of tools for windows administration.<br>
We can use it directly from a share:<br>
```
\\live.sysinternals.com\tools\
```

Useful tools:<br>
- **Task Manager**
- **Process Explorer** (part of sysinternals suite)

**sc** command can also be used to manage services.<br>
```
sc qc service_name
```
```
sc //hostname service_name
```
```
sc stop service_name
```

The **Get-Acl** command show services permissions.<br>

## Interacting with the OS

### Command prompt and commands

**Windows command promtp** is used to type commands.<br>
**Powershell** is a windows shell to interact with the OS.<br>
It uses commands in the form: Verb-Noun like this:<br>
```
Get-ChildItem C:\
```

#### Aliases

There are many aliases in windows powershell:<br>
The alias for `Get-ChildItem` is `ls` <br>
The one for `Set-Location` is `cd` <br>
To see aliases:<br>
```
Get-Alias
```

To set Aliases
```
New-Alias -Name "Cmd_Name" alias_name
```

To get the online help of a command:<br>
```
Get-Help cmdlet_name -Online
```

To install locally help files:<br>
```
Update-Help
```

### Scripts

Windows powershell allow us to wright, import, download and execute scripts.<br>

To run a script remotly after loading it into memory:<br>
```
.\Module.ps1;Cmdlet
```

To import a module and all his commands:<br>
```
Import-Module .\Module.ps1
```

To List associated commands of modules:<br>
```
Get-Module | select Name,ExportedCommands | fl
```

#### Execution Policy

To see the execution policy:<br>
```
Get-ExecutionPolicy -List
```

To set execution policy:<br>
```
Set-ExecutionPolicy policy -Scope scope
```

### Windows Management Instrumentation (WMI)

We can use **wmic** to use wmi utilities by openning a interactive shell or directly run a command:<br>
```
wmic os list brief
```

We can use wmi in powershell with the `Get-WmiObject` module:<br>
```
Get-WmiObject -Class Win32OperatingSystem | select BuildNumber | ft
```

### Microsoft Management Console

This a tool we can use to create custum console for specific purposes.<br>

