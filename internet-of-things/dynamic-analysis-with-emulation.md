# 🎮 Dynamic Analysis with Emulation

## FirmAE

The FirmAE3 tool extends the capability of FIRMADYNE4 to allow for the emulation of more ﬁrmware by using various arbitrations for services and the QEMU hypervisor. The focus of the arbitrations is to allow the running of web services, as that is a common attack vector. The beauty of this approach is that you do not have to buy the hardware to test the ﬁrmware. This powerful approach allows for scaled testing in parallel. The authors of FirmAE had a success rate of 79.36 percent on 1,124 devices and found 12 new 0-days, 5 which is not bad at all.&#x20;

## Setting Up FirmAE

### Install Packages

```
sudo apt install build-essential git telnet
```

### Install FirmAE

```
git clone https://github.com/pr0v3rbs/FirmAE.git

cd FirmAE

./download.sh

./install.sh

./init.sh
```

## Emulating Firmware

First, using the run.sh script, check any ﬁrmware . This step will extract the image, get the architecture, infer the network conﬁg, and associate an ID in the database for the analysis (this may take a while, so be patient):

```
sudo -E ./run.sh -c <netgear> <firmware.zip>
```

### Run the Emulator with Debugging Enabled

```
sudo -E ./run.sh -d <netgear> <firmware.zip>

# Access the shell
2
```

### Reset the Database and Environment

```
psql -d postgres -U firmdyne -h 127.0.0.1 -q -c 'DROP DATABASE "firmware"'

sudo -u postgres createdb -O firmdyne firmware

sudo -u postgres psql -d firmware < ./database/schema

sudo rm -rf ./images/*.tar.gz

sudorm -rf scratch/
```



At this point, the ﬁrmware should be running on the preceding IP as a tap device. You should also be able to connect to this virtual interface from the machine on which you are running QEMU. From within the VM, open a web browser and try to connect to the inferred IP, as shown next. You may need to wait a minute for the web service to fully start after the emulator launches the ﬁrmware.

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption><p>Screenshot</p></figcaption></figure>



***

## REFERENCES

* [https://github.com/pr0v3rbs/FirmAE](https://github.com/pr0v3rbs/FirmAE)
* [www.acsac.org/2020/ﬁles/web/6a-4\_ﬁrmae-slides.pdf](https://www.acsac.org/2020/%EF%AC%81les/web/6a-4\_%EF%AC%81rmae-slides.pdf)
* [https://github.com/ﬁrmadyne/ﬁrmadyne](https://github.com/%EF%AC%81rmadyne/%EF%AC%81rmadyne)
* [https://www.schneier.com/blog/archives/2014/01/securit\
  y\_risks\_9.html](https://www.schneier.com/blog/archives/2014/01/security\_risks\_9.html)
* [https://github.com/ﬁrmadyne/ﬁrmadyne](https://github.com/%EF%AC%81rmadyne/%EF%AC%81rmadyne)
* [https://packetstormsecurity.com/ﬁles/135956/D-Link-\
  Netgear-FIRMADYNE-Command-Injection-Buﬀer-\
  Overﬂow.html](https://packetstormsecurity.com/%EF%AC%81les/135956/D-Link-Netgear-FIRMADYNE-Command-Injection-Bu%EF%AC%80er-Over%EF%AC%82ow.html)

