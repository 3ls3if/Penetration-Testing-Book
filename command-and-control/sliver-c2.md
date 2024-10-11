# ⛎ Sliver C2

## Introduction

Sliver is a powerful command and control (C2) framework designed to provide advanced capabilities for covertly managing and controlling remote systems. With Sliver, security professionals, red teams, and penetration testers can easily establish a secure and reliable communication channel over Mutual TLS, HTTP(S), DNS, or Wireguard with target machines. Enabling them to execute commands, gather information, and perform various post-exploitation activities. The framework offers a user-friendly console interface, extensive functionality, and support for multiple operating systems as well as multiple CPU architectures, making it an indispensable tool for conducting comprehensive offensive security operations.

## Features

* Dynamic code generation
* Compile-time obfuscation
* Multiplayer-mode
* Staged and Stageless payloads
* [Procedurally generated C2](https://sliver.sh/docs?name=HTTPS+C2) over HTTP(S)
* [DNS canary](https://sliver.sh/docs?name=DNS+C2) blue team detection
* [Secure C2](https://sliver.sh/docs?name=Transport+Encryption) over mTLS, WireGuard, HTTP(S), and DNS
* Fully scriptable using [JavaScript/TypeScript](https://github.com/moloch--/sliver-script) or [Python](https://github.com/moloch--/sliver-py)
* Windows process migration, process injection, user token manipulation, etc.
* Let's Encrypt integration
* In-memory .NET assembly execution
* COFF/BOF in-memory loader
* TCP and named pipe pivots
* Much more!

## Installation

```
curl https://sliver.sh/install|sudo bash

# Run sliver
sliver
```





***

## REFERENCES

* [https://dominicbreuker.com/post/learning\_sliver\_c2\_01\_installation/](https://dominicbreuker.com/post/learning\_sliver\_c2\_01\_installation/)
* [https://sliver.sh/docs?name=Getting+Started](https://sliver.sh/docs?name=Getting+Started)

