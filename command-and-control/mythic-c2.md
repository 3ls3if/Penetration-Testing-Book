# 🦄 Mythic C2

## Mythic

A cross-platform, post-exploit, red teaming framework built with GoLang, docker, docker-compose, and a web browser UI. It's designed to provide a collaborative and user friendly interface for operators, managers, and reporting throughout red teaming.

### Starting Mythic

Mythic is controlled via the `mythic-cli` binary. To generate the binary, run `sudo make` from the main Mythic directory. From there, you can run `sudo ./mythic-cli start` to bring up all default Mythic containers.

More specific setup instructions, configurations, examples, screenshots, and more can be found on the [Mythic Documentation](https://docs.mythic-c2.net/) website.

### Installing Agents and C2 Profiles

The Mythic repository itself does not host any Payload Types or any C2 Profiles. Instead, Mythic provides a command, `./mythic-cli install github <url> [branch name] [-f]`, that can be used to install agents into a current Mythic instance.

Payload Types and C2 Profiles can be found on the [overview](https://mythicmeta.github.io/overview) page.

To install an agent, simply run the script and provide an argument of the path to the agent on GitHub:

```
sudo ./mythic-cli install github https://github.com/MythicAgents/apfell
```

The same is true for installing C2 Profiles:

```
sudo ./mythic-cli install github https://github.com/MythicC2Profiles/http
```

This allows the agents and c2 profiles to be updated at a much more regular pace and separates out the Mythic Core components from the rest of Mythic.



***

## REFERENCES

* [https://github.com/its-a-feature/Mythic](https://github.com/its-a-feature/Mythic)
* [https://medium.com/@haq.prg/mythic-server-setup-tutorial-7981c87a8d01](https://medium.com/@haq.prg/mythic-server-setup-tutorial-7981c87a8d01)
* [https://docs.mythic-c2.net/installation](https://docs.mythic-c2.net/installation)
* [https://medium.com/r3d-buck3t/red-teaming-in-the-cloud-installing-mythic-c2-on-azure-vm-35ef762e61b6](https://medium.com/r3d-buck3t/red-teaming-in-the-cloud-installing-mythic-c2-on-azure-vm-35ef762e61b6)
