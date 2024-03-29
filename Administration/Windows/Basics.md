# Windows basics

## OS infos

Find informations about the system:<br>
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
| Win32\_Bios | I/O informations |

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

We can manage services via **services.msc** or with th **Get-Service** command:<br>

```
Get-Service | ? {$_.Status -eq "Running"} | select -First 2 | fl
```

**Sysinternal tool suite** is a set of tools for windows administration.<br>
We can use it directly from a share:<br>

```
\\live.sysinternals.com\tools\
```

**Task Manager** is for managing Windows systems.<br>

**Process Explorer** is a sysinternal tool to show wich processes are loaded when a program runs.<br>

**sc** command can also be used to manage services.<br>

```
sc qc service_name
sc //hostname service_name
sc stop service_name
```
The **Get-Acl** command show services permissions.<br>
