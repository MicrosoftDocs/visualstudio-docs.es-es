---
title: Configuración del Servicio R remoto en Linux
description: Describe cómo configurar el servicio remoto de R en Ubuntu y el subsistema de Windows para Linux.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: c4d65388db0ef90f807ec85b8c9216d717c2b571
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "62809562"
---
# <a name="remote-r-service-for-linux"></a>Servicio R remoto para Linux

El servicio R remoto para Linux actualmente se empaqueta como rtvs-daemon. El demonio es compatible y se ha probado en Ubuntu 16.04, 16.10 LTS para escritorio, servidor y el subsistema de Windows para Linux con Ubuntu. En la mayor parte de este artículo se ofrecen instrucciones sobre cómo configurar el servicio remoto de R en estos distintos sistemas.

Una vez haya configurado el equipo remoto, los pasos siguientes conectan las herramientas de R para Visual Studio (RTVS) a ese servicio:

1. Seleccione **Herramientas de R** > **Ventanas** > **Áreas de trabajo** para abrir la ventana **Áreas de trabajo**.
1. Haga clic en **Agregar conexión**.
1. Asigne un nombre a la conexión y proporcione su dirección URL, como `https://localhost:5444` (Subsistema de Windows para Linux) o `https://public-ip:5444` (contenedor de Azure). Haga clic en **Guardar** cuando termine.
1. Haga clic en el icono de conexión o haga doble clic en el elemento de conexión.
1. Proporcione las credenciales de inicio de sesión. El nombre de usuario debe ir precedido de `<<unix>>\` como en `<<unix>>\ruser1` (según sea necesario para todas las conexiones a equipos remotos de Linux).
1. Si está usando un certificado autofirmado, es posible que vea una advertencia. En el mensaje se proporcionan instrucciones para corregir la advertencia.

## <a name="set-up-remote-r-service"></a>Configuración del Servicio R remoto

En esta sección se describen los conceptos siguientes:

- [Equipo físico de Ubuntu](#physical-ubuntu-computer)
- [Máquina virtual del servidor de Ubuntu o máquina virtual de ciencia de datos en Azure](#ubuntu-server-vm-or-data-science-vm-on-azure)
- [Contenedor de Docker local o remoto (compilación limpia)](#local-or-remote-docker-container-clean-build)
- [Contenedor que se ejecuta en Azure Container Instances](#container-running-on-azure-container-instances)

En cada caso, el equipo remoto debe tener instalado uno de los intérpretes de R siguientes:

- [Microsoft R Open](https://mran.microsoft.com/open/)
- [CRAN R para Windows](https://cran.r-project.org/bin/linux/ubuntu/)

### <a name="physical-ubuntu-computer"></a>Equipo físico de Ubuntu

1. Una vez que haya iniciado sesión en el equipo, descargue el paquete tarball rtvs-daemon:

    ```bash
    wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current
    tar -xvzf rtvs-daemon.tar.gz
    ```

1. Ejecute el script de instalación:

    ```bash
    sudo ./rtvs-install
    ```

    Para una automatización silenciosa, use `sudo ./rtvs-install -s`.

1. Habilite e inicie el servicio:

    ```bash
    sudo systemctl enable rtvsd
    sudo systemctl start rtvsd
    ```

1. Configure el certificado SSL (necesario para producción). De forma predeterminada, rtvs-daemon usa `ssl-cert-snakeoil.pem` y `ssl-cert-snakeoil.pem`, generados por el paquete `ssl-cert`. Durante la instalación, se combinan en `ssl-cert-snakeoil.pfx`. Para fines de producción, use el certificado SSL proporcionado por el administrador. El certificado SSL se puede configurar al proporcionar un archivo *.pfx* y una contraseña de importación opcional en: */etc/rtvs/rtvsd.config.json*.

1. (Opcional) Compruebe que el servicio se está ejecutando:

    ```bash
    ps -A -f | grep rtvsd
    ```

    Si no ve un proceso que se ejecuta bajo el nombre de usuario `rtvssvc`. Inícielo con el comando siguiente:

    ```bash
    sudo systemctl start rtvsd
    ```

1. Para configurar aún más el demonio de RTVS, vea `man rtvsd`.

### <a name="ubuntu-server-vm-or-data-science-vm-on-azure"></a>Máquina virtual del servidor de Ubuntu o máquina virtual de ciencia de datos en Azure

#### <a name="create-a-vm"></a>Crear una máquina virtual

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
1. Desplácese a Máquinas virtuales y, después, haga clic en **Agregar**.
1. En la lista de imágenes de máquina virtual disponibles, busque y seleccione una de las siguientes:
    - Servidor de Ubuntu: `Ubuntu Server 16.04 LTS`
    - Máquina virtual de ciencia de datos: `Linux Data Science` (vea [Máquinas virtuales de ciencia de datos](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) para obtener más información)
1. Establezca el modelo de implementación en `Resource manager` y haga clic en **Crear**.
1. Elija un nombre para la máquina virtual, proporcione un nombre de usuario y una contraseña (la contraseña es obligatoria, dado que no se admite el inicio de sesión de clave pública SSH).
1. Realice los cambios deseados en la configuración de la máquina virtual.
1. Elija un tamaño de máquina virtual, compruebe la configuración y haga clic en **Crear**. Una vez creada la máquina virtual, vaya a la sección siguiente.

#### <a name="configure-the-vm"></a>Configuración de la máquina virtual

1. En la sección **Red** de la máquina virtual, agregue 5444 como puerto de entrada permitido. Para usar otro puerto, cambie la configuración en el archivo de configuración del demonio de RTVS ( */etc/rtvs/rtvsd.config.json*).
1. (Opcional) Establezca un nombre DNS; también puede usar la dirección IP.
1. Conéctese a la máquina virtual mediante un cliente SSH como PuTTY para Windows.
1. Siga las instrucciones anteriores para una [equipo físico de Ubuntu](#physical-ubuntu-computer).

### <a name="windows-subsystem-for-linux-wsl"></a>Subsistema de Windows para Linux (WSL)

1. Siga las instrucciones de instalación de WSL para [Windows 10](/windows/wsl/install-win10#install-the-windows-subsystem-for-linux) o [Windows Server](/windows/wsl/install-on-server#enable-the-windows-subsystem-for-linux-wsl).
1. Inicie bash en Windows y siga las instrucciones anteriores de [equipo físico de Ubuntu](#physical-ubuntu-computer) con una excepción. En el paso 3, inicie el servicio con el comando `rtvsd` en su lugar, dado que actualmente WSL no admite las interfaces systemd/systemctl.

### <a name="local-or-remote-docker-container-clean-build"></a>Contenedor de Docker local o remoto (compilación limpia)

1. Cree un archivo de Docker con el contenido siguiente, que instala el demonio del servicio R remoto y la versión más reciente de R. **Nota**: Este script crea un usuario denominado "ruser1" con la contraseña "foobar", que se puede modificar según sea necesario en las dos últimas instrucciones `RUN`.

    ```docker
    FROM ubuntu:16.04

    ARG DEBIAN_FRONTEND=noninteractive

    RUN apt-get update \
     && apt-get install -y software-properties-common python-software-properties \
     && apt-get install -y apt-transport-https \
     && rm -rf /var/lib/apt/lists/*

    RUN sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list' \
     && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 417A0893 \
     && sh -c 'echo "deb https://cran.revolutionanalytics.com/bin/linux/ubuntu xenial/" > /etc/apt/sources.list.d/cran-r.list' \
     && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9 \
     && rm -rf /var/lib/apt/lists/* \
     && apt-get clean

    RUN apt-get update --fix-missing && apt-get update \
     && apt-get install -y dotnet-dev-1.0.4 libexplain51 libzip4 libc6 git lshw ssl-cert wget \
     && rm -rf /var/lib/apt/lists/*

    # install R
    RUN apt-get update && apt-get install -y r-base-dev
    RUN apt upgrade -y

    # install rtvs-daemon
    RUN wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current && tar -xvzf rtvs-daemon.tar.gz && ./rtvs-install -s

    RUN useradd --create-home ruser1
    RUN echo "ruser1:foobar" | chpasswd

    EXPOSE 5444
    ```

1. Compile y ejecute el archivo de Docker:

    ```bash
    docker build -t myrimage .
    docker run -p 5444:5444 myrimage rtvsd
    ```

1. Para conectarse al contenido de RTVS, use `https://localhost:5444` como la ruta de acceso, el nombre de usuario `<<unix>>\ruser1` y la contraseña `foobar`. Si el contenedor se ejecuta en un equipo remoto, use `https://remote-host-name:5444` como la ruta de acceso en su lugar. El puerto se puede cambiar al actualizar */etc/rtvs/rtvsd.config.json*.

### <a name="container-running-on-azure-container-instances"></a>Contenedor que se ejecuta en Azure Container Instances

1. Siga las instrucciones de [Contenedor de Docker local o remoto (compilación limpia)](#local-or-remote-docker-container-clean-build) para crear la imagen.
1. Inserte el contenedor en Docker Hub o en el repositorio de contenedores de Azure.
1. Inicie la CLI de Azure e inicie sesión con el comando `az login`.
1. Use el comando `az container create` para crear el contenedor, con `--command-line "rtvsd"` si el contenedor no se ha configurado para ejecutar `rtvsd` como un servicio `systemd`. En el comando siguiente, la imagen debe estar en Docker Hub. También puede usar el repositorio de contenedores de Azure mediante la adición de argumentos de credencial de repositorio de contenedores a la línea de comandos.

    ```bash
    az container create --image myimage:latest --name myaz-container --resource-group myaz-container-res --ip-address public --port 5444 --cpu 2 --memory 4 --command-line "rtvsd"
    ```

1. Use el comando `az container list` para comprobar el estado. Busque `provisioningState`: `Succeeded`.
1. Si el aprovisionamiento se realizó correctamente, ahora puede conectarse al contenedor. Busque la dirección IP pública, en el campo `ipAddress`, que se usa con las credenciales del archivo de Docker para conectarse al contenedor de RTVS.
