# Docker in VirtualBox(Vagrant + Ansible)

Ubuntu 22.04.03 (jammy LTS) で Docker-ce 24.0.7

## 必要なもの

あらかじめ以下のツールを導入先ホストにインストールして下さい。

* Vagrant (2.4.0で確認)
* Ansible (core 2.15.8で動作確認)

## 動作確認環境

* Vagrant (2.4.0)
* Ansible (core 2.15.8)

## 物理マシン要件

dockerが動ける範囲で、Vagrantfileのmvspecを適宜変えてください。

* CPU: 4コア
* メモリ:4GB
* ディスク: 50GB

## インストール

* Vagrantfileがあるディレクトリで、

```bash
$ vagrant up
```

* SSHでホストに入るには

```bash
$ vagrant ssh
```

## 共有ディレクトリ

* ホスト: `./` (vagrant実行時のディレクトリ)
* ゲスト(Ubuntu): `/var/synced`

## 動作確認

```bash
vagrant@docker-ce:~$ docker -v
Docker version 24.0.7, build afdd53b
vagrant@docker-ce:~$ docker run hello-world

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
```

