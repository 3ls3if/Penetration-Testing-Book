# ⚔️ Weaponization

## What is Weaponization?

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>Cyber Kill Chain</p></figcaption></figure>

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

