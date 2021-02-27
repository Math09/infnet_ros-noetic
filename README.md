# Configurando ROS-1 (Noetic) e Gazebo
A fim de instalar configurar e gerar exemplos de código para rodar o ROS-1 (Noetic) me fundamentei nos seguintes links:

* [ROS-1 (Noetic)](http://wiki.ros.org/noetic/Installation/Ubuntu)

## 1. Instalando ROS-1 (Noetic)
**Passo 1:** Configurar o sources.list para aceitar a instalação.
```bash
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

**Passo 2:** Configurando chave. <br/>
*Antes de realizar o comando para configurar a chave, é necessário verificar se o pacote **curl** está instalado no sistema.*

---
Verificando a versão do pacote curl:
```bash
curl --version
```
Caso apareça este retorno é necessário instalar o curl: <br/>
![Curl Not Found](/images/curl_not_found.png)

Porém caso apareça esse retorno no terminal pule a instalação do curl: <br/>
![Curl Version](/images/curl_version.png)

Instalando curl:
```bash
sudo apt-get install curl
```
---

```bash
curl -sSL 'http://keyserver.ubuntu.com/pks/lookup?op=get&search=0xC1CF6E31E6BADE8868B172B4F42ED6FBAB17C654' | sudo apt-key add -
```

**Passo 3:** Atualizando pacotes do sistema.
```bash
sudo apt update
```

**Passo 4:** Comando para instalar o ROS-1. <br/>
*Usar APENAS um dos comando a seguir.*

*Instalando ROS Desktop-Full (Instalação Completa).*
```bash
sudo apt install ros-noetic-desktop-full
```

*Instalando ROS-Desktop.*
```bash
sudo apt install ros-noetic-desktop
```

*Instalando ROS-Base.*
```bash
sudo apt install ros-noetic-ros-base
```

**Passo 5:** Configurando o caminho do ROS-1.

*Passo 5.1:* Abrindo o arquivo '.bashrc'.
```bash
sudo gedit .bashrc
```

*Passo 5.2:* Criando o alias initros1.
(Adicionar esse caminho ao '.bashrc' - normalmente pode ser adicionado no final do arquivo)
```bash
alias initros1="source /opt/ros/noetic/setup.bash";
```

*Passo 5.3:* Atualizando '.bashrc'.
```bash
source .bashrc
```

### Após a instalação execute os comandos a seguir para atribuir e verificar a versão do ROS. <br/>
1. Comando para atribuir a versão do ROS.
```bash
initros1
```
2. Comando para verificar a versão do ROS.
```bash
rosversion -d
```
3. Assim o terminar deverá ficar da seguinte forma: <br/>
![Version ROS](/images/ros_version.png)

---
## Verificando e Instalando o Gazebo
**Passo 1:** Verificando se o gazebo foi instalado. <br/>
Existem algumas maneiras de verificar se o Gazebo foi instalado na máquina.

1. O ícone deve estar no menu do sistema. <br/>
*Se o gazebo foi instalado junto com o ROS-1 possívelmente apareceram esses ícones, caso apareça apenas o ícone do Gazebo é oportuno realizar os outros testes.*
![gazebo icons]()

2. Verificar a versão do Gazebo, no terminal.
```bash
gazebo --version
```
Possíveis retornos:
```if( Se estiver instalado, esse será o retorno ):``` <br/>
![gazebo version]()

```else( Caso não esteja ):``` <br/>
![gazebo version not found]()

3. Verificar se as pastas '/gzserver' e '/gzclient' estão instaladas, no terminal. 
```bash
which gzserver && which gzclient
```
Possiveis retornos:
```if( Se estiver instalado, esse será o retorno ):``` <br/>
![gazebo folder]()

```else( Caso não esteja ):``` <br/>
![gazebo folder not found]()

4. Tentar executar o comando para abrir o gazebo, no terminal.
```bash
gazebo
```
Possíveis retornos:
```if( Se estiver instalado, esse será o retorno ):``` <br/>
![gazebo open]() <br/>
![gazebo terminal]()

```else( Caso não esteja ):``` <br/>
![gazebo not found]()

**Passo 2:** Instalando o Gazebo (gazebo_ros_pkg).

*Passo 2.1:* Instalando Debians pré construídos.
```bash
sudo apt-get install ros-noetic-gazebo-ros-pkgs ros-noetic-gazebo-ros-control
```
* Onde está a palavra noetic pode ser substituída por qualquer versão, tais como:
    * ROS - Lunar
    * ROS - Kinetic
    * ROS - Indigo

*Passo 2.2:* Instalando o Gazebo
```bash
sudo apt-get install -y libgazebo11-dev
```



```bash

```