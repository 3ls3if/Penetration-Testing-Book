# 🌩️ C2 In The Cloud

## Deploy Covenant C2 in the Cloud

### Setup EC2 Instance

#### Step 1: Launch an Instance

```
Click on Services

Select EC2

Click on Launch Instance

Enter a Name under Name and tags

Select an OS type under Application and OS Images

Click on Create new key pair under Key pair

Leave the other options as default

Click on Launch instance button

```

#### Step 2: Connect to your instance

**For Windows**

* https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/connecting\_to\_windows\_instance.html

```
Click on Instance ID under Instances dashboard

Click on Connect

Select RDP Client

Click on Get password

Upload the private key file

Click on Decrypt password

Copy the password and public dns name

Now, open Remmina or any other rdp client

Enter the copied public dns

Enter the username as Administrator

Enter the decrypted password

Click on Ok

```

### Setup Covenant

#### Install dotnet

```
https://dotnet.microsoft.com/download/dotnet/3.1

```

#### Install Git

```
https://git-scm.com/download/win
```

#### Install Covenant

```
mkdir c:\c2

Cd c:\c2

git clone --recurse-submodules https://github.com/cobbr/Covenant

cd

cd Covenant\Covenant

dotnet run

```

#### Register Account

```
Visit : https://127.0.0.1:7443/

Enter a username

Enter password

Confirm the password
```

***

## REFERENCES

* https://youtu.be/IR2ibXwwt8I
* https://medium.com/@harellevy159/setting-up-c2-redirectors-with-havoc-132bf53033d1
* https://youtu.be/1uh5-OzBEqM
* https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2\_GetStarted.html
* https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/connecting\_to\_windows\_instance.html
* https://www.pwndefend.com/2021/03/20/installing-covenant-c2-on-windows/

