# 🐲 intro to ghidra

## Intro To Ghidra

### Installation and QuickStart

```
sudo apt-get update && sudo apt-get install -y openjdk-11-jdk
```

[Download Ghidra](https://ghidra-sre.org)

```
unzip <ghidra.zip> -d ~

cd ~/ghidra

./ghidraRun
```

### Create a Project

* Click on File | New or Ctrl+N
* Click File | Import to import the executables
* Click on Ok
* Double Click the Target file to launch the code browser and start the analysis

### Analysis

* Function Analyzer Assigns addresses and names to functions based on their symbol reference or by detecting function prologues and epilogues in the code disassembly.
* Stack Analyzer Infers stack variable sizes and references based on stack base and pointer operations at the beginning of the function.
* Operand Analyzer Assigns and resolves address and symbol references based on scalar operands.
* Data Reference Analyzer Resolves addresses and references to data values and obvious data types based on their memory section location and operands in the code.

### Code Browser

* Main menu: All the main options are available from this menu.
* Toolbar: Here you will ﬁnd a group of icon buttons you can use as shortcuts for common functionality.
* Program Trees: This provides tree lists of all the memory segments deﬁned by the binary and will vary depending on the binary format and loader.
* Symbol Tree: Here you can quickly navigate through all the symbols deﬁned by the debugging information or resolved by the initial analysis. These symbols are separated by type: imports, exports, functions, labels, classes, and namespaces.
* Data Type: Manager Built-in, generic, binary- provided, and user-deﬁned data types will be available here. You can easily navigate to operations on values and references by their data type.
* Listing: The program’s code disassembly and data references are listed here. You can easily explore program logic, references, and address oﬀsets. Special comments and named values generated by the Ghidra loader and analyzer are displayed here as well. -Decompile: This window displays a C language representation of the function selected on the Listing window. This decompilation eases the process of analyzing large and complex assembly code blocks.
* Console – Scripting: Results and outputs from scripts and plug-ins are shown here.

### Lab 4-2: Binary Diﬃng and Patch Analysis

#### Install BinDiffHelper Extension

**Install Gradle build automation tool**

```
wget https://services.gradle.org/distributions/gradle-6.5-milestone-2-bin.zip && sudo unzip gradle-6.5-milestone-2-bin.zip -d /opt
```

**Clone and compile the BinExport2 plug-in**

```
git clone --single --depth=1 --branch=master  https://github.com/google/binexport ~/binexport && cd ~/binexport/java/BinExport && /opt/gradle-6.5-milestone-2/bin/gradle -PGHIDRA_INSTALL_DIR=~/ghidra_9.3.2_PUBLIC
```

**Download and Install BinDiff**

```
wget https://storage.googleapis.com/bindiff-releases/bindiff_6_amd64.deb

sudo dpkg -i bindiff_6_amd64.deb || sudo apt-get install -f
```

**Clone and Compile BinDiffHelper plug-in**

```
cd ~/ && git clone --single --depth=1 --branch=master https://github.com/ubfx/BinDiffHelper && cd ~/BinDiffHelper && /opt/gradle-6.5-milestone-2/bin/gradle -PGHIDRA_INSTALL_DIR=~/ghidra_9.3.2_PUBLIC
```

## References

* [Ghidra Cheatsheet](https://ghidra-sre.org/CheatSheet.html)
