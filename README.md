# LSP-LINUX-SERVER-PROJECT


## 🧊 MINECRAFT JAVA 

### 🛠️ Guía de Instalación Paso a Paso

Sigue estos comandos en orden dentro de la terminal de tu servidor


### 1. Dependencias del Sistema

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y curl wget file tar bzip2 gzip unzip bsdmainutils python3 util-linux ca-certificates binutils bc jq tmux netcat-openbsd lib32gcc-s1 lib32stdc++6 libsdl2-2.0-0
```

### 2. Java

- Java 8 version antiguas < 1.16.5

```bash
sudo apt install -y openjdk-8-jdk
```

### Configurar variable de entorno

```bash
echo 'export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64' >> ~/.bashrc
echo 'export PATH=$PATH:$JAVA_HOME/bin' >> ~/.bashrc
source ~/.bashrc
```

- Java 17 para versiones 1.17 a 1.20.4
  
```bash
sudo apt install -y openjdk-17-jdk
```

### Configurar variable de entorno

```bash
echo 'export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64' >> ~/.bashrc
echo 'export PATH=$PATH:$JAVA_HOME/bin' >> ~/.bashrc
source ~/.bashrc
```
  
- Java 21 para versiones 1.20.5 y superiores

```bash
sudo apt install -y openjdk-21-jdk
```
### Configurar variable de entorno

```bash
echo 'export JAVA_HOME=/usr/lib/jvm/java-21-openjdk-amd64' >> ~/.bashrc
echo 'export PATH=$PATH:$JAVA_HOME/bin' >> ~/.bashrc
source ~/.bashrc
```

### Verificar

```bash
java -version
```
### 3. Instalación de LinuxGSM y Minecraft Server

```bash
wget -O linuxgsm.sh https://linuxgsm.sh && chmod +x linuxgsm.sh && bash linuxgsm.sh mcserver
./mcserver install
```

### 4. Permitir el puerto a Playit

```bash
sudo ufw allow 25565/tcp
```

### 5. Gestion del Servidor

### Iniciar el Servidor
```bash
./mcserver start
```
### Ver consola del Servidor
```bash
./mcserver console
```
### Reinicio del Servidor
```bash
./mcserver restart
```
### Detalles del Servidor
```bash
./mcserver details
```

### Actualizar el Servidor 
```bash
./mcserver update
```

### 6. Playit

```bash
curl -SsL https://playit-cloud.github.io/ppa/key.gpg | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/playit.gpg
echo "deb [signed-by=/etc/apt/trusted.gpg.d/playit.gpg] https://playit-cloud.github.io/ppa/data ./" | sudo tee /etc/apt/sources.list.d/playit-cloud.list
sudo apt update
sudo apt install playit -y
```

```bash
playit
```

- Ver el estado del túnel:

```bash
sudo systemctl status playit
```

- Reiniciar Playit (si se cae la conexión):

```bash
sudo systemctl restart playit
```
- Habilitar para que inicie solo al prender la PC:
  
```bash
sudo systemctl enable playit
```

- Iniciar playit
  
```bash
sudo systemctl start playit
```

```bash
sudo systemctl daemon-reload
```

```bash
sudo systemctl edit playit.service
```
```bash
[Service]
Restart=always
RestartSec=5
StartLimitIntervalSec=0
```

```bash
screen -S playit_tunnel
```
```bash
playit
```

```bash
sudo systemctl is-enabled playit
```
## Otra versiones

- Regresar al paso antes de instalar

```bash
wget -O linuxgsm.sh https://linuxgsm.sh && chmod +x linuxgsm.sh && bash linuxgsm.sh mcserver
./mcserver install
```

- Instalar y cambiar el archivo minecraft_server.jar

```bash
chmod +x serverfiles/minecraft_server.jar
```

Verifica que tu version de Forge, Fabric, Arclight, Mohist, Paper Purpur o Otros sea estable antes ingresarla al servidor

```bash
./mcserver start 
```

### Si es forge directo tienes que hacer esto

```bash
java -jar minecraft_server.jar --installServer
```

### En la ruta: (config-lgsm/mcserver/mcserver.cfg)

# Si es Forge antiguo (<1.17)
```bash
executable="./minecraft_server.jar"
```
```bash
chmod +x forge-*.jar
```
# Si es Forge moderno (1.17+)

```bash
executable="./run.sh"
```

```bash
chmod +x run.sh
```
## Iniciar el servidor
```bash
./mcserver start
./mcserver console
```
## Verificar la version de Forge
- Forge 1.20.1+ -> Java 17 o 21.

- Forge 1.12.2 -> Java 8.

## Asignar mas Ram al servidor 

En la ruta: (config-lgsm/mcserver/mcserver.cfg)
```bash
javaram="x"
```

x= Dos gigas menos de la ram que tienes en mb 1gb ram = 1000mb 
### Ejemplo
```bash
javaram = "6000"
```

Si tienes 8gb de ram

### ------------------
### AUTIO INICIO DEL SERVIDOR
```bash
sudo bash -c 'cat <<EOF > /etc/systemd/system/minecraft-watchdog.service
[Unit]
Description=Watchdog para Minecraft LinuxGSM (LSP)
After=network.target

[Service]
# Asegúrate de que el User coincida con el que creaste (ej. lsp-admin)
User=lsp-admin
Group=lsp-admin
WorkingDirectory=/home/lsp-admin
Type=forking

# Comandos específicos de LinuxGSM
ExecStart=/home/lsp-admin/mcserver start
ExecStop=/home/lsp-admin/mcserver stop
Restart=always
RestartSec=15

[Install]
WantedBy=multi-user.target
EOF'
```
### Recargar los servicios de sistema
```bash
sudo systemctl daemon-reload
```
### Permitir el sistema
```bash
sudo systemctl enable minecraft-watchdog.service
```
### Iniciarlo
```bash
sudo systemctl start minecraft-watchdog.service
```
### Detenerlo
```bash
sudo systemctl stop minecraft-watchdog.service
```
### Verificarlo
```bash
sudo systemctl status minecraft-watchdog.service
```


By lucast1574
