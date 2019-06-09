# Docker

Here are a couple of commands to install Docker Community Edition (CE) on Centos 7.

## Install Docker CE

### 1. Repository update

2 commands to use to update the repository first.

>  sudo yum install -y yum-utils device-mapper-persistent-data lvm2

```
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


```
[root@centos7 ~]# yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
Modules complémentaires chargés : fastestmirror, langpacks
adding repo from: https://download.docker.com/linux/centos/docker-ce.repo
grabbing file https://download.docker.com/linux/centos/docker-ce.repo to /etc/yum.repos.d/docker-ce.repo
repo saved to /etc/yum.repos.d/docker-ce.repo
[root@centos7 ~]#
```

### 2. Now program installation

Here is the installation command to have Docer working on the Linux host.

> sudo yum install docker-ce docker-ce-cli containerd.io

```
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

## Uninstall docker CE

> yum remove docker-ce

```
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
