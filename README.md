# My Personal Minecraft Server Setup

![Minecraft](https://img.shields.io/badge/Minecraft-1.19.4-green?logo=minecraft)
![docker badge](https://img.shields.io/badge/Docker-20.10.21-blue?logo=docker)

### Aim

- Able to automate the provisioning of a Fabric Minecraft Server with datapacks, mods, configuration, etc. This is achieved by using `ansible` and maybe several other IaC tools.
- Able to provision an efficient Vanilla+ server (retaining Vanilla mechanics without changing content too much)

### Features

- Using the [itzg/minecraft-server](https://github.com/itzg/docker-minecraft-server/) image.
- Easy to change configuration via `.env`.
- Able to use mods and datapacks easily by inserting them to respective folders.
- Backup of worlds in remote server.
- The ability to start and stop server remotely

### Requirements

On local machine:

- `ansible` & `ansible-playbook`
- Zipping utility (`zip` or `tar`)

On remote machine:

- Zipping utility (`zip` or `tar`)
- Docker and docker-compose
- Python 3 & Python Docker API (`pip install docker`)

### Running Manually

Use:

```bash
docker-compose up
```

### Provisioning Server

Make sure you have the hosts setup on `/etc/ansible/hosts`.

Commands:

```bash
./bootstrap.sh <private-key-location> (setup|start|stop|reset|backup)
# setup -- setting up server files, copying from local to remote
# start -- starting server (aka docker-compose up)
# stop -- stopping server (aka docker-compose down)
# reset -- resetting server world
# backup -- zipping world in remote and copy to local
```
