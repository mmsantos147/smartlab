# Instalação do Home Assistant

1. Pacotes essenciais para o sistema do HA

    ```bash
    apt install apt-transport-https ca-certificates curl gnupg2 software-properties-common apparmor-utils avahi-daemon dbus jq network-manager socat ffmpeg
    ```

2. Adicionando o repositório do docker

    ```bash
    curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
    apt-key fingerprint 0EBFCD88
    add-apt-repository "deb https://download.docker.com/linux/debian $(lsb_release -cs) stable"
    ```

3. Atualizando o repositório

    ```bash
    apt update
    ```

4. Instalando o docker

    ```bash
    apt install docker-ce
    ```

5. Instalando o Home Assistant 
    A versão do HA utilizada nesse projeto é Home Assistant Supervised para isso foi consultado o repositório oficial dessa versão:

    ```
    https://github.com/home-assistant/supervised-installer
    ```

6. Agora acesse seu endenreço ip na porta 8123 ex: “http://<seu ip>:8123”

***
***

# Home Assistant Installation

1. Essential packages for the HA system

   ```bash
   apt install apt-transport-https ca-certificates curl gnupg2 software-properties-common apparmor-utils avahi-daemon dbus jq network-manager socat ffmpeg
   ```

2. Adding the Docker repository

   ```bash
   curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
   apt-key fingerprint 0EBFCD88
   add-apt-repository "deb https://download.docker.com/linux/debian $(lsb_release -cs) stable"
   ```

3. Updating the repository

   ```bash
   apt update
   ```

4. Installing Docker

   ```bash
   apt install docker-ce
   ```

5. Installing Home Assistant

   The version of HA used in this project is Home Assistant Supervised.For this, the official repository of this version was consulted:

   ```
   https://github.com/home-assistant/supervised-installer
   ```
6. Now access your IP address on port 8123, for example:

   ```
   http://<your_ip>:8123
   ```