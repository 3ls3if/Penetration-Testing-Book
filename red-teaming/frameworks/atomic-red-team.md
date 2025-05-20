---
icon: atom
---

# Atomic Red Team

## Introduction <a href="#id-0fa5" id="id-0fa5"></a>

[Atomic Red Team](https://github.com/redcanaryco/atomic-red-team) is an open-source project that provides a framework for performing security testing and threat emulation. The main goal of Atomic Red Team is to ease the threat emulation process. Atomic Red Team’s tests are mapped to the MITRE ATT\&CK framework.

Every Atomic Test is written for a specific MITRE Technique where the files are named as its mapped MITRE Technique ID. We can find the collection of available tests [here](https://atomicredteam.io/atomics/#collection).

### Set up <a href="#id-1f62" id="id-1f62"></a>

First we’ll need to open PowerShell as an administrator. Secondly, we’ll set the ExecutionPolicy to bypass in order to ignore the security warning prompts for the module.

```
powershell -ExecutionPolicy bypass
```

Third, we’ll import the module using the following command.

```
Import-Module "path/to/file/Invoke-AtomicRedteam.psd1" -Force
```

Next, we’ll need to update the PSDefaultParameterValues var

```
$PSDefaultParameterValues = @{"Invoke-AtomicTest:PathToAtomicsFolder"="C:\Tools\AtomicRedTeam\atomics"}
```

Once that is imported, we can then check to see if it’s working by using the help command.

```
help Invoke-AtomicTest
```

## Usage <a href="#bee7" id="bee7"></a>

We can list the available atomic techniques. For example if we wanted to see if [T1123 ](https://attack.mitre.org/techniques/T1123/)is available.

```
Invoke-AtomicTest T1123 -ShowDetails
```

<figure><img src="https://miro.medium.com/v2/resize:fit:875/1*mi4hU1w2v9M0jG660WV3FQ.png" alt="" height="474" width="700"><figcaption></figcaption></figure>

The output above gives us the attack commands that it’ll run as well as the clean up commands.

### Prerequisites <a href="#id-12f0" id="id-12f0"></a>

Some techniques will have a Dependencies section. In order to check with the pre-requisites are met, we can run the following command with the technique we want to use.

```
Invoke-AtomicTest T#### -CheckPrereqs
```

<figure><img src="https://miro.medium.com/v2/resize:fit:875/1*R1LyfJbIDZIvJSAmyG-9cw.png" alt="" height="286" width="700"><figcaption></figcaption></figure>

We can then try to pull the dependencies from an external source using the following command.

```
Invoke-AtomicTest T#### -GetPrereqs
```

### Execution <a href="#id-7c1d" id="id-7c1d"></a>

There are multiple ways of executing the Atomic tests.

<figure><img src="https://miro.medium.com/v2/resize:fit:684/1*Ijg3UEl2OKiizO2H6P42Bw.png" alt="" height="171" width="547"><figcaption></figcaption></figure>

If we look at the screenshot above, we can execute these tests in multiple ways. The first way would be with the TestNumbers which runs the tests by the numbers that we see to the right of T1053.005.

```
Invoke-AtomicTest T1053.005 -TestNumbers 1,2
```

The next way of executing tests is by the test name which is everything to the right of T1053.005–1.

```
Invoke-AtomicTest T1053.005 -TestNames "Scheduled Task Startup Script"
```

Alternatively, we can execute all tests or just a single test.

```
Invoke-AtomicTest T1053.005
```

```
Invoke-AtomicTest T1053.005-2
```

We can pass in custom arguments into each test through the command line by using the `-PromptForInputArgs` flag when we run the command.

```
Invoke-AtomicTest T1053.005-2 -PromptForInputArgs
```

### Cleanup <a href="#id-3f08" id="id-3f08"></a>

After executing any of the tests, it’s very important to clean up the results of those emulations. Atomic Red Team offers a Cleanup parameter that we can use to clean up the effects of the test.

```
Invoke-AtomicTest T1053.005 -Cleanup
```

### Adding New Atomic Tests <a href="#id-5683" id="id-5683"></a>

In some cases Atomic Red Team may not have the corresponding Atomic or test for the the MITRE techniques that you’re looking for.

We can create new tests using the Atomic Red Team GUI.

```
Start-AtomicGui
```

Once that’s started, we can then visit it at localhost:8487/home in the browser.

<figure><img src="https://miro.medium.com/v2/resize:fit:875/1*FRvKRXC8qLimWAUGM-Ynvg.png" alt="" height="382" width="700"><figcaption></figcaption></figure>

We can then fill out the form and generate the YAML file by clicking on the Generate Test Definition YAML button.

<figure><img src="https://miro.medium.com/v2/resize:fit:875/1*yCILYH2-S5milLG9dXApzQ.png" alt="" height="320" width="700"><figcaption></figcaption></figure>

[\
](https://medium.com/tag/cybersecurity?source=post_page-----7f07b8561b8---------------------------------------)

***

## REFERENCES

* [https://medium.com/@renbe/atomic-red-team-on-windows-7f07b8561b8](https://medium.com/@renbe/atomic-red-team-on-windows-7f07b8561b8)
* [https://github.com/redcanaryco/atomic-red-team/wiki/Getting-started](https://github.com/redcanaryco/atomic-red-team/wiki/Getting-started)

