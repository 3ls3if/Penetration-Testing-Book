---
icon: hard-drive
---

# Hacking Vending Machines

## Introduction

When you think of hacking, the usual suspects probably come to mind — bank networks, corporate servers, social media accounts. But vending machines? Yes, those toys that dispense snacks and drinks can be part of the hacking adventure, thanks to the rise of the Internet of Things (IoT).

Today’s vending machines aren’t just mechanical snack dispensers. They’re IoT devices, connected to the internet, often relying on communication protocols like **MQTT** to send and receive data. When these machines aren’t properly secured, hackers can sneak in, as I did.

## How Vending Machines Work

Vending machines may look simple, but behind the snack selection lies some pretty cool technology. Here’s a quick breakdown:

* **Product Selection:** You pick your snack using buttons or a touch screen.
* **Payment:** You pay using cash, card, or a contactless payment method.
* **Product Delivery:** The machine checks your payment, and if everything is good, it dispenses your snack.
* **Data Communication:** Modern vending machines often communicate with a remote server, sending data about inventory levels, payment transactions, and system diagnostics. This is typically done using IoT protocols like MQTT or similar communication protocols.

So what happens if a vending machine’s communication system is exposed to the internet? Let’s find out.

## MQTT Protocol

[**MQTT (Message Queuing Telemetry Transport)**](https://www.geeksforgeeks.org/introduction-of-message-queue-telemetry-transport-protocol-mqtt/) is the go-to protocol for many IoT devices, including vending machines, because it’s lightweight and perfect for transmitting small amounts of data. Think of it as a messaging service where devices (like vending machines) send updates to a broker, and subscribers (like servers) receive those updates. To get deep into hacking MQTT, have a look at this p[blog](https://aravind07.medium.com/iot-pentesting-mqtt-101-with-lab-setup-and-exploitation-2003c9d3f09c) post.

It’s efficient for vending machines that need to report stock levels or transaction data to a central server without consuming much bandwidth. The only problem? Some machines expose these MQTT communications to the open internet. Without proper security, that’s where hackers like me come in.

## Using Censys to Find Exposed Vending Machines

To begin vending machine hacking journey, we turned to [**Censys**](http://search.censys.io/), an incredible search engine for internet-connected devices. It’s like Google, but for finding devices like webcams, industrial control systems, and in this case, vending machines.

With a simple query, we were able to pinpoint exposed vending machines that were using MQTT:

```
(vending machine) and services.service_name=`MQTT`
```

## Reconnaissance

Now that we had some potential targets, it was time to dive deeper into what these vending machines were up to. we used **Moxie**, a tool built for MQTT reconnaissance and pentesting, which makes it easy to scan, check, and even brute-force MQTT services. You can check out **Moxie** on [GitHub](https://github.com/aravind0x7/Moxie).





***

## REFERENCES

* [https://medium.com/@aravind07/the-art-of-hacking-vending-machines-2b65e34519ea](https://medium.com/@aravind07/the-art-of-hacking-vending-machines-2b65e34519ea)



