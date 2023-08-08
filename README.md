# Simple install on VPS (requires docker or docker-compose)

```
$ cd simple-install
$ docker run -d --name v2ray -v /path/to/config.json:/etc/v2fly/config.json -p 10086:10086 v2fly/v2fly-core run -c /etc/v2fly/config.json
```

## or

```
$ cd simple-install
$ docker-compose up -d
```

# Ansible install

### Create your config

```
$ cd ansible-install/inventory
$ mkdir -p <any name>/group_vars
$ touch <any name>/hosts.ini
$ touch <any name>/group_vars/all.yml
```
### Change `group_vars/all.yml` with your parameters

## Run ansible-playbook

### Install docker first (optional)

```
$ cd ansible-install
$ ansible-playbook -i inventory/<any name>/hosts.ini docker-install.yml -k -K
```

### Install and run v2ray server

```
$ cd ansible-install
$ ansible-playbook -i inventory/<any name>/hosts.ini v2ray-install.yml -k -K
```

#### Your client config will be fetched to `ansible-install/fetched/<server ip>/client-config.json`