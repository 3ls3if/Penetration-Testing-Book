# ⚔️ Weaponization

## What is Weaponization?

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption><p>Cyber Kill Chain</p></figcaption></figure>

**Weaponization** is the second stage of the Cyber Kill Chain model. In this stage, the attacker generates and develops their own malicious code using deliverable payloads such as word documents, PDFs, etc. \[[1](https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html)]. The weaponization stage aims to use the malicious weapon to exploit the target machine and gain initial access.

**Red Team Toolkit:** [https://github.com/infosecn1nja/Red-Teaming-Toolkit#Payload%20Development](https://github.com/infosecn1nja/Red-Teaming-Toolkit#Payload%20Development)



***



## Windows Scripting Host (WSH)

Windows scripting host is a built-in Windows administration tool that runs batch files to automate and manage tasks within the operating system.

It is a Windows native engine, cscript.exe (for command-line scripts) and wscript.exe (for UI scripts), which are responsible for executing various Microsoft Visual Basic Scripts (VBScript), including vbs and vbe. For more information about VBScript, please visit [here](https://en.wikipedia.org/wiki/VBScript). It is important to note that the VBScript engine on a Windows operating system runs and executes applications with the same level of access and permission as a regular user; therefore, it is useful for the red teamers.

#### Hello.vbs

```
Dim message 
message = "Welcome!"
MsgBox message
```

Run the script using the below command:

```
wscript Hello.vbs
```

**VBScript to run executable files**

The following vbs code is to invoke the Windows calculator, proof that we can execute .exe files using the Windows native engine (WSH).

```
Set shell = WScript.CreateObject("Wscript.Shell")
shell.Run("C:\Windows\System32\calc.exe " & WScript.ScriptFullName),0,True
```

We create an object of the WScript library using CreateObject to call the execution payload. Then, we utilize the Run method to execute the payload. For this task, we will run the Windows calculator calc.exe.&#x20;

To execute the vbs file, we can run it using the wscript as follows,&#x20;

```
wscript payload.vbs
```

We can also run it via cscript as follows,

```
cscript.exe payload.vbs
```

As a result, the Windows calculator will appear on the Desktop.

Another trick. If the VBS files are blacklisted, then we can rename the file to .txt file and run it using wscript as follows,\


```
wscript /e:VBScript payload.txt
```

The result will be as exact as executing the vbs files, which run the calc.exe binary.\


\


***

