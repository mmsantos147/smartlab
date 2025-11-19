# Instalação do Armbian na MX10 mini (processador RK3318 rev. 2.0)
## Alertas

- Esse passo a passo foi testado em várias unidades sem nenhuma ocorrência negativa.
- Há o risco de perda da sua TV Box caso haja algum problema mais severo. Use por seu próprio risco. Não me responsabilizo por nenhum dano.

## Procedimento

1. Baixe a imagem do **Multitool** disponível aqui.
2. Se você não instalou o **Balena Etcher**, faça o download e instale-o na sua máquina.
3. Rode o **Balena Etcher** e transfira a imagem para o seu cartão SD (não esqueça de descompactar o arquivo da imagem).
4. Após a transferência da imagem para o cartão SD, remova-o com segurança no Windows.
5. Insira o cartão SD na sua TV Box.
6. Ligue o cabo de energia. Utilizando um palitinho de madeira ou um clipes de papel aperte um botão escondido dentro da entrada AV da TVBox, caso seja de um modelo diferente pode ser necessário outro procedimento. Seu equipamento deverá iniciar automaticamente pelo **Multitool** e redimensionar as partições do cartão SD. 
7. Após a inicialização será exibido um menu, escolha **EXIT** e posteriormente, **Shutdown** e **OK**.
8. Reinsira o cartão SD no seu computador. Copie a imagem disponível aqui no cartão SD, na pasta images, sem desconpacta-la. Após a transferência da imagem para o cartão SD, remova-o com segurança no Windows.
9. Insira o cartão SD na sua TV Box.
10. Ligue o cabo de energia. Seu equipamento deverá iniciar automaticamente pelo **Multitool**. Será exibido um menu, escolha **EXIT**. 
11. No menu seguinte, escolha Burn image to flash, caso seu dispositivo tenha conteúdo dentro será necessário formatar pelo mesmo menu. Aparecerá a partição a ser gravada (`mmcblk2` ou algo semelhante). Ela deverá estar selecionada, escolha então **OK**. Aparecerá a imagem que copiou (`Armbian_22.08.0-trunk…`). Seleciona-a e escolha **OK** novamente. O Armbian será transferido para a sua TV Box. Aguarde.
12. Se tudo der certo, será exibida a mensagem **Image has been burned to device mmcblk2** (no nosso caso aqui). Selecione **OK**. Escolha então **Shutdown**.
13. Retire o cartão SD, desconecte o cabo de energia e conecte novamente. O Armbian deverá ser iniciado normalmente. Faça as configurações do Linux da forma que desejar.

## Observação 
- A imagem utilizada neste tutorial é a **Armbian 22.08 Bullseye Minimal**, mas futuramente será necessário atualiza-la para **Bookworm** então recomendo ja instalar essa imagem. Toda a instalação deverá ser feita posteriormente. Essa escolha se deu pelas características da TV Box, permitindo que você possa otimizar da forma que preferir. Qualquer dúvida, entre em contato.

- Para se conectar a tvbox remotamente basta conectar o cabo de rede, identificar o ip dela e conectar via ssh

## Atualização do Armbian 
1. Atualizar repositórios para Bookworm
    - Editar o arquivo sources.list   
        ```Shell
        sudo nano /etc/apt/sources.list
        ```
    - Troque todas as entradas contendo bullseye por bookworm:
        ```Shell
        
        # Original: deb-src http://deb.debian.org/debian bullseye main contrib non-free
        deb http://deb.debian.org/debian bookworm main contrib non-free

        # Original: deb-src http://deb.debian.org/debian bullseye-updates main contrib non-free
        deb http://deb.debian.org/debian bookworm-updates main contrib non-free
        
        # Original: deb-src http://deb.debian.org/debian bullseye-backports main contrib non-free
        deb http://deb.debian.org/debian bookworm-backports main contrib non-free

        # Original: deb-src http://security.debian.org/ bullseye-security main contrib non-free
        deb http://security.debian.org/ bookworm-security main contrib non-free
        
        # Original: deb-src https://download.docker.com/linux/debian bullseye stable
        deb https://download.docker.com/linux/debian bookworm stable

        ```
    - Editar o arquivo sources.list.d/armbian.list
        ```Shell
        sudo nano /etc/apt/sources.list.d/armbian.list
        ```
    - Troque as entradas contendo bullseye por bookworm:
        ```Shell
        deb http://apt.armbian.com bookworm main bookworm-utils bookworm-desktop
        ```
    - Atualizar o sistema:
        ```Shell
        sudo apt update
        ```
    - Utilizei os seguintes comandos por ser o inicio do sistema, caso atualize um sistema em andamento cuidado ao executar os seguintes comandos:
        ```Shell
        sudo apt full-upgrade -y
        sudo apt --purge autoremove -y
        sudo apt clean
        ```
    - Reinicialize o sistema:
        ```Shell
        sudo reboot
        ```
    - Teste se a versão esta correta:
        ```Shell
        lsb_release -a
        ```

***
***

# Armbian Installation on MX10 Mini (RK3318 rev. 2.0 Processor)
## Warnings

- This procedure has been tested on multiple units without any negative occurrences.
- There is a risk of damaging your TV Box if a severe issue occurs. Proceed at your own risk. I am not responsible for any damage.

## Procedure

1. Download the **Multitool** image available here.
2. If you haven’t installed **Balena Etcher**, download and install it on your computer.
3. Run **Balena Etcher** and flash the image to your SD card (don’t forget to extract the image file first).
4. After flashing the image, safely eject the SD card from Windows.
5. Insert the SD card into your TV Box.
6. Connect the power cable. Using a wooden stick or a paperclip, press the hidden button inside the AV port of the TV Box (for other models, the procedure might differ). Your device should automatically boot from **Multitool** and resize the SD card partitions.
7. Once the system boots, a menu will appear. Select **EXIT**, then **Shutdown**, and confirm with **OK**.
8. Reinsert the SD card into your computer. Copy the Armbian image available here into the **/images** folder on the SD card without extracting it. After copying, safely eject the SD card from Windows.
9. Insert the SD card back into your TV Box.
10. Connect the power cable again. The device should boot from **Multitool**. When the menu appears, choose **EXIT**.
11. In the next menu, select **Burn image to flash**. If your device already contains data, format it using the same menu. You’ll see a partition (e.g., `mmcblk2` or similar). Make sure it’s selected and choose **OK**. Then, select the image you copied earlier (e.g., `Armbian_22.08.0-trunk…`) and confirm with **OK**. The Armbian system will now be flashed to your TV Box. Wait for the process to complete.
12. If everything goes well, a message saying **Image has been burned to device mmcblk2** (or similar) will appear. Select **OK**, then choose **Shutdown**.
13. Remove the SD card, disconnect the power cable, and reconnect it. Armbian should now boot normally. Proceed with the Linux setup as you prefer.

## Notes

- The image used in this tutorial is **Armbian 22.08 Bullseye Minimal**, but it is recommended to update to **Bookworm** in the future—so you may install that version directly. All configurations should be performed afterward. This choice was made considering the TV Box’s characteristics, allowing you to optimize the system as desired. For any questions, feel free to get in touch.

- To connect to the TV Box remotely, simply plug in the network cable, identify its IP address, and connect via SSH

## Armbian Update

1. Update repositories to Bookworm

   - Edit the sources.list file

     ```Shell
     sudo nano /etc/apt/sources.list
     ```
   - Replace all entries containing bullseye with bookworm:

     ```Shell

     # Original: deb-src http://deb.debian.org/debian bullseye main contrib non-free
     deb http://deb.debian.org/debian bookworm main contrib non-free

     # Original: deb-src http://deb.debian.org/debian bullseye-updates main contrib non-free
     deb http://deb.debian.org/debian bookworm-updates main contrib non-free

     # Original: deb-src http://deb.debian.org/debian bullseye-backports main contrib non-free
     deb http://deb.debian.org/debian bookworm-backports main contrib non-free

     # Original: deb-src http://security.debian.org/ bullseye-security main contrib non-free
     deb http://security.debian.org/ bookworm-security main contrib non-free

     # Original: deb-src https://download.docker.com/linux/debian bullseye stable
     deb https://download.docker.com/linux/debian bookworm stable

     ```
   - Edit the sources.list.d/armbian.list file

     ```Shell
     sudo nano /etc/apt/sources.list.d/armbian.list
     ```
   - Replace the entries containing bullseye with bookworm:

     ```Shell
     deb http://apt.armbian.com bookworm main bookworm-utils bookworm-desktop
     ```
   - Update the system:

     ```Shell
     sudo apt update
     ```
   - I used the following commands because this was a fresh system. If you are updating an active system, be careful when executing the following commands:

     ```Shell
     sudo apt full-upgrade -y
     sudo apt --purge autoremove -y
     sudo apt clean
     ```
   - Reboot the system:

     ```Shell
     sudo reboot
     ```
   - Test if the version is correct:

     ```Shell
     lsb_release -a
     ```