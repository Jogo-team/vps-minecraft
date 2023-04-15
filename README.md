# My Personal Minecraft Server Setup

![Minecraft](https://img.shields.io/badge/Minecraft-1.19.2-green?logo=minecraft)
![docker badge](https://img.shields.io/badge/Docker-20.10.6-blue?logo=docker)

### Aim

- Able to automate the provisioning of a Fabric Minecraft Server with datapacks, mods, configuration, etc. This is achieved by using `ansible` and maybe several other IaC tools.
- Able to provision an efficient Vanilla+ server (retaining Vanilla mechanics without changing content too much)

### Features

- Using the [itzg/minecraft-server](https://github.com/itzg/docker-minecraft-server/) image.
- Easy to change configuration via `.env`.
- Able to use mods and datapacks easily by inserting them to respective folders.
- Backup of worlds in remote server.
- The ability to start and stop server remotely
- Able to run locally and do tunneling via [ngrok](https://ngrok.com/) using the [wernight/ngrok](https://github.com/wernight/ngrok) image.

### Mod List

Currently experimenting using Quilt Modloader, which is highly compatible with Fabric mods. Mods may change and depend on the Minecraft version used, but most of the mods are made sure to be available on a certain version.

- Carpet Mod (utility mod for technical stuff)
- Krypton (network optimization)
- LazyDFU (memory optimization)
- MemoryLeakFix (memory optimization)
- FerriteCore (memory optimization)
- Lithium (general optimization)
- Starlight (light-transport optimization)
- Fabric Chunk Pregenerator (to pregenerate chunks before exploring)

Extra mods and datapacks for world generation are listed in the directory. Feel free to remove if not wanted.

### Requirements

On local machine:

- `ansible` & `ansible-playbook`
- Zipping utility (`zip` or `tar`)

On remote machine:

- Zipping utility (`zip` or `tar`)
- Docker and docker-compose
- Python 3 & Python Docker API (`pip install docker`)

> **Note**
> Don't forget to setup your environment variables like in the one supplied on `.env.example` locally on `.env`.

### Running Manually

Use:

```bash
docker-compose up
```

### Provisioning Server

Make sure you have the hosts setup on `/etc/ansible/hosts`.
Example has been provided in `hosts.example`.

Commands:

```bash
./bootstrap.sh <private-key-location> (setup|start|stop|reset|backup)
# setup -- setting up server files, copying from local to remote
# start -- starting server (aka docker-compose up)
# stop -- stopping server (aka docker-compose down)
# reset -- resetting server files and configs in remote
# backup -- zipping world in remote and copy to local
```
