---
icon: mountain
---

# MITRE Caldera

## Mitre Caldera

Caldera™ is an adversary emulation platform designed to easily run autonomous breach-and-attack simulation exercises. Caldera is built on the MITRE ATT\&CK™ framework and is an active research project

[![Logo](https://wiki.pentest.training/~gitbook/image?url=https%3A%2F%2Fcaldera.readthedocs.io%2Ffavicon.ico\&width=20\&dpr=4\&quality=100\&sign=59007ff1\&sv=2)Installing MITRE Caldera — caldera documentation](https://caldera.readthedocs.io/en/latest/Installing-Caldera.html)

#### Docker Deployment[](https://caldera.readthedocs.io/en/latest/Installing-Caldera.html#docker-deployment) <a href="#docker-deployment" id="docker-deployment"></a>

Caldera can be installed and run in a Docker container.

Start by cloning the Caldera repository recursively, passing the desired version/release in x.x.x format:

```
git clone https://github.com/mitre/caldera.git --recursive --branch 5.0.0
```

Next, build the docker image, changing the image tag as desired.

```
cd caldera
docker build --build-arg WIN_BUILD=true . -t caldera:server
```

Alternatively, you can use the `docker-compose.yml` file by running:

```
docker-compose build
```

Finally, run the docker Caldera server, changing port forwarding as required. More information on Caldera’s configuration is [available here](https://caldera.readthedocs.io/en/latest/Server-Configuration.html#configuration-file).

```
docker run -p 7010:7010 -p 7011:7011/udp -p 7012:7012 -p 8888:8888 caldera:server
```

To gracefully terminate your docker container, do the following:

```
# Find the container ID for your docker container running Caldera
docker ps

# Send interrupt signal, e.g. "docker kill --signal=SIGINT 5b9220dd9c0f"
docker kill --signal=SIGINT [container ID]
```



***

## REFERENCES

* [https://wiki.pentest.training/cyberwolf-security/labs-resources/mitre-caldera](https://wiki.pentest.training/cyberwolf-security/labs-resources/mitre-caldera)
* [https://medium.com/@joaohenriquepatakibernardes/how-to-install-caldera-adversary-simulator-98500f114808](https://medium.com/@joaohenriquepatakibernardes/how-to-install-caldera-adversary-simulator-98500f114808)
* [https://caldera.readthedocs.io/en/4.1.0/Installing-CALDERA.html](https://caldera.readthedocs.io/en/4.1.0/Installing-CALDERA.html)
* [https://github.com/mitre/caldera](https://github.com/mitre/caldera)
