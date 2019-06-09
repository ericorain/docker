# Docker

Here are a couple of commands to install Docker Community Edition (CE) on Centos 7.

## 1. Install Docker CE

### 1.1 Repository update

2 commands to use to update the repository first.

>  sudo yum install -y yum-utils device-mapper-persistent-data lvm2

``` shell
[root@centos7 ~]# yum install -y yum-utils device-mapper-persistent-data lvm2
Modules complémentaires chargés : fastestmirror, langpacks
Loading mirror speeds from cached hostfile
 * base: mirrors.ircam.fr
 * extras: mirrors.ircam.fr
 * updates: mirrors.ircam.fr
Le paquet yum-utils-1.1.31-50.el7.noarch est déjà installé dans sa dernière version
Le paquet device-mapper-persistent-data-0.7.3-3.el7.x86_64 est déjà installé dans sa dernière version
Le paquet 7:lvm2-2.02.180-10.el7_6.7.x86_64 est déjà installé dans sa dernière version
Rien à faire
[root@centos7 ~]#
```

> sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo


``` shell
[root@centos7 ~]# yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
Modules complémentaires chargés : fastestmirror, langpacks
adding repo from: https://download.docker.com/linux/centos/docker-ce.repo
grabbing file https://download.docker.com/linux/centos/docker-ce.repo to /etc/yum.repos.d/docker-ce.repo
repo saved to /etc/yum.repos.d/docker-ce.repo
[root@centos7 ~]#
```

### 1.2 Docker installation command

Here is the installation command to have Docer working on the Linux host.

> sudo yum install docker-ce docker-ce-cli containerd.io

``` shell
[root@centos7 ~]# sudo yum install docker-ce docker-ce-cli containerd.io
Modules complémentaires chargés : fastestmirror, langpacks
Loading mirror speeds from cached hostfile
 * base: mirrors.ircam.fr
 * extras: mirrors.ircam.fr
 * updates: mirrors.ircam.fr
Le paquet 1:docker-ce-cli-18.09.6-3.el7.x86_64 est déjà installé dans sa dernière version
Le paquet containerd.io-1.2.5-3.1.el7.x86_64 est déjà installé dans sa dernière version
Résolution des dépendances
--> Lancement de la transaction de test
---> Le paquet docker-ce.x86_64 3:18.09.6-3.el7 sera installé
--> Résolution des dépendances terminée

Dépendances résolues

========================================================================================================================
 Package                  Architecture          Version                           Dépôt                           Taille
========================================================================================================================
Installation :
 docker-ce                x86_64                3:18.09.6-3.el7                   docker-ce-stable                 19 M

Résumé de la transaction
========================================================================================================================
Installation   1 Paquet

Taille totale des téléchargements : 19 M
Taille d'installation : 81 M
Is this ok [y/d/N]: y
Downloading packages:
docker-ce-18.09.6-3.el7.x86_64.rpm                                                               |  19 MB  00:00:02
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installation : 3:docker-ce-18.09.6-3.el7.x86_64                                                                   1/1
  Vérification : 3:docker-ce-18.09.6-3.el7.x86_64                                                                   1/1

Installé :
  docker-ce.x86_64 3:18.09.6-3.el7

Terminé !
[root@centos7 ~]#
```

## 2. Uninstall docker CE

If needed Docker can be uninstalled. Removing forgotten images/containers might be done alos (not described here).

> yum remove docker-ce

``` shell
[root@centos7 ~]# yum remove docker-ce
Modules complémentaires chargés : fastestmirror, langpacks
Résolution des dépendances
--> Lancement de la transaction de test
---> Le paquet docker-ce.x86_64 3:18.09.6-3.el7 sera effacé
--> Résolution des dépendances terminée
base/7/x86_64                                                                                    | 3.6 kB  00:00:00
docker-ce-stable/x86_64                                                                          | 3.5 kB  00:00:00
extras/7/x86_64                                                                                  | 3.4 kB  00:00:00
updates/7/x86_64                                                                                 | 3.4 kB  00:00:00

Dépendances résolues

========================================================================================================================
 Package                  Architecture          Version                          Dépôt                            Taille
========================================================================================================================
Suppression :
 docker-ce                x86_64                3:18.09.6-3.el7                  @docker-ce-stable                 81 M

Résumé de la transaction
========================================================================================================================
Supprimer  1 Paquet

Taille d'installation : 81 M
Est-ce correct [o/N] : o
Downloading packages:
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
/usr/bin/dockerd n'a pas encore été configuré en tant qu'alternative à dockerd
  Suppression  : 3:docker-ce-18.09.6-3.el7.x86_64                                                                   1/1
  Vérification : 3:docker-ce-18.09.6-3.el7.x86_64                                                                   1/1

Supprimé :
  docker-ce.x86_64 3:18.09.6-3.el7

Terminé !
[root@centos7 ~]#
```

## 3. Testing Docker is running

Let's check if the service is running.

> systemctl status docker

``` shell
[root@centos7 ~]# systemctl status docker
? docker.service - Docker Application Container Engine
   Loaded: loaded (/usr/lib/systemd/system/docker.service; disabled; vendor preset: disabled)
   Active: inactive (dead)
     Docs: https://docs.docker.com

juin 09 07:02:48 centos7 dockerd[3315]: time="2019-06-09T07:02:48.554055018+02:00" level=info msg="Loading conta...art."
juin 09 07:03:05 centos7 dockerd[3315]: time="2019-06-09T07:03:05.767508668+02:00" level=info msg="Default bridg...ress"
juin 09 07:03:07 centos7 dockerd[3315]: time="2019-06-09T07:03:07.658506716+02:00" level=info msg="Loading conta...one."
juin 09 07:03:08 centos7 dockerd[3315]: time="2019-06-09T07:03:08.572303542+02:00" level=info msg="Docker daemon....09.6
juin 09 07:03:08 centos7 dockerd[3315]: time="2019-06-09T07:03:08.572588513+02:00" level=info msg="Daemon has co...tion"
juin 09 07:03:08 centos7 systemd[1]: Started Docker Application Container Engine.
juin 09 07:03:08 centos7 dockerd[3315]: time="2019-06-09T07:03:08.928673786+02:00" level=info msg="API listen on...sock"
juin 09 11:00:42 centos7 systemd[1]: Stopping Docker Application Container Engine...
juin 09 11:00:42 centos7 dockerd[3315]: time="2019-06-09T11:00:42.909296195+02:00" level=info msg="Processing si...ted'"
juin 09 11:00:42 centos7 systemd[1]: Stopped Docker Application Container Engine.
Hint: Some lines were ellipsized, use -l to show in full.
[root@centos7 ~]#
```

-> By default Docker deamon is not running.

Let's make it run.

> systemctl start docker

``` shell
[root@centos7 ~]# systemctl start docker
[root@centos7 ~]# systemctl status docker
? docker.service - Docker Application Container Engine
   Loaded: loaded (/usr/lib/systemd/system/docker.service; disabled; vendor preset: disabled)
   Active: active (running) since dim. 2019-06-09 11:16:59 CEST; 4s ago
     Docs: https://docs.docker.com
 Main PID: 14421 (dockerd)
    Tasks: 12
   Memory: 33.1M
   CGroup: /system.slice/docker.service
           mq14421 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock

juin 09 11:16:57 centos7 dockerd[14421]: time="2019-06-09T11:16:57.614024431+02:00" level=info msg="pickfirstBal...=grpc
juin 09 11:16:57 centos7 dockerd[14421]: time="2019-06-09T11:16:57.661662965+02:00" level=info msg="[graphdriver...lay2"
juin 09 11:16:57 centos7 dockerd[14421]: time="2019-06-09T11:16:57.673014729+02:00" level=info msg="Graph migrat...onds"
juin 09 11:16:57 centos7 dockerd[14421]: time="2019-06-09T11:16:57.674449115+02:00" level=info msg="Loading cont...art."
juin 09 11:16:58 centos7 dockerd[14421]: time="2019-06-09T11:16:58.666087357+02:00" level=info msg="Default brid...ress"
juin 09 11:16:58 centos7 dockerd[14421]: time="2019-06-09T11:16:58.960505346+02:00" level=info msg="Loading cont...one."
juin 09 11:16:58 centos7 dockerd[14421]: time="2019-06-09T11:16:58.995057112+02:00" level=info msg="Docker daemo....09.6
juin 09 11:16:58 centos7 dockerd[14421]: time="2019-06-09T11:16:58.995247867+02:00" level=info msg="Daemon has c...tion"
juin 09 11:16:59 centos7 dockerd[14421]: time="2019-06-09T11:16:59.023290431+02:00" level=info msg="API listen o...sock"
juin 09 11:16:59 centos7 systemd[1]: Started Docker Application Container Engine.
Hint: Some lines were ellipsized, use -l to show in full.
[root@centos7 ~]#
```

A way to check that Docker is working is to run the "hello world" test. This test consists of downloading a simple Docker image then running Docker with this image.

> sudo docker run hello-world

``` shell
[root@centos7 ~]# sudo docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
1b930d010525: Pull complete
Digest: sha256:0e11c388b664df8a27a901dce21eb89f11d8292f7fca1b3e3c4321bf7897bffe
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

[root@centos7 ~]#
```

Since the container did not exists the image of the container  has been downloaded. We can see it in the image list of Docker.

``` shell
[root@centos7 ~]# docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
hello-world         latest              fce289e99eb9        5 months ago        1.84kB
[root@centos7 ~]#
```

## 4. Usefull commands

### 4.1 Get Docker currently installed version

> docker --version

``` shell
[root@centos7 ~]# docker --version
Docker version 18.09.6, build 481bc77156
[root@centos7 ~]#
```

### 4.2 Get Docker information (number of images, containers, etc.)

> docker info

``` shell
[root@centos7 ~]# docker info
Containers: 1
 Running: 0
 Paused: 0
 Stopped: 1
Images: 1
Server Version: 18.09.6
Storage Driver: overlay2
 Backing Filesystem: xfs
 Supports d_type: true
 Native Overlay Diff: true
Logging Driver: json-file
Cgroup Driver: cgroupfs
Plugins:
 Volume: local
 Network: bridge host macvlan null overlay
 Log: awslogs fluentd gcplogs gelf journald json-file local logentries splunk syslog
Swarm: inactive
Runtimes: runc
Default Runtime: runc
Init Binary: docker-init
containerd version: bb71b10fd8f58240ca47fbb579b9d1028eea7c84
runc version: 2b18fe1d885ee5083ef9f0838fee39b62d653e30
init version: fec3683
Security Options:
 seccomp
  Profile: default
Kernel Version: 3.10.0-957.12.2.el7.x86_64
Operating System: CentOS Linux 7 (Core)
OSType: linux
Architecture: x86_64
CPUs: 1
Total Memory: 3.701GiB
Name: centos7
ID: VKLJ:6VVK:YXH5:5RUP:PTDJ:C4FB:T7MJ:6YEX:JDC4:2QUL:LDI3:2PXD
Docker Root Dir: /var/lib/docker
Debug Mode (client): false
Debug Mode (server): false
Registry: https://index.docker.io/v1/
Labels:
Experimental: false
Insecure Registries:
 127.0.0.0/8
Live Restore Enabled: false
Product License: Community Engine

[root@centos7 ~]#
```

### 4.23 List images

> docker images

or

> docker image ls


``` shell
[root@centos7 ~]# docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
hello-world         latest              fce289e99eb9        5 months ago        1.84kB
[root@centos7 ~]#
```

