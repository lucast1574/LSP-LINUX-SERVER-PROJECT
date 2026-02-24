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

## Otra versiones

- Regresar al paso antes de instalar

```bash
wget -O linuxgsm.sh https://linuxgsm.sh && chmod +x linuxgsm.sh && bash linuxgsm.sh mcserver
./mcserver install
```

- Instalar y cambiar el archivo minecraft_server.jar

```bash
chmod +x /minecraft/serverfiles/minecraft_server.jar
```

Verifica que tu version de Forge, Fabric, Arclight, Mohist, Paper Purpur o Otros sea estable antes ingresarla al servidor

```bash
./mcserver start 
```

### Si es forge directo tienes que hacer esto

```bash
java -jar forge-1.20.1-47.3.0-installer.jar --installServer
```

En la ruta: (config-lgsm/mcserver/mcserver.cfg)

# Si es Forge antiguo (<1.17)
```bash
executable="./forge-1.12.2-14.23.5.2859-universal.jar"
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
