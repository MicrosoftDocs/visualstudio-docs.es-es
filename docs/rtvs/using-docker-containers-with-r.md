---
title: R y contenedores de Docker
description: Describe cómo configurar los contenedores de Docker para R y conectarse a ellos con Visual Studio.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 01048bc9b21287eb62693096b34a1ea8305e0ee9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851873"
---
# <a name="use-docker-containers-with-r-tools-for-visual-studio"></a>Usar contenedores de Docker con Herramientas de R para Visual Studio

Las herramientas de R para Visual Studio (RTVS) versión 1.3 y superiores, junto con una instalación de [Docker para Windows](https://www.docker.com/docker-windows), permiten trabajar con contenedores de Docker.

## <a name="create-a-container"></a>Crear un contenedor

1. Haga clic en el botón **Contenedores** en la esquina derecha de la ventana **Áreas de trabajo** (**Herramientas de R** > **Ventanas** > **Áreas de trabajo**). La ventana le informa si no tiene instalado Docker para Windows y proporciona un vínculo para la descarga. La instalación de Docker puede requerir el reinicio del equipo.

    ![Ventana Áreas de trabajo de Herramientas de R para Visual Studio (VS2017) con el comando Contenedores](media/container-workspaces-window.png)

1. En la ventana **Contenedores**, haga clic en **Crear**:

    ![Comando Crear en la ventana Contenedores](media/containers-window-create.png)

1. Rellene la información necesaria en el cuadro de diálogo y haga clic en **Crear**. Las credenciales que escriba también se usan para crear una cuenta en Linux, con la que más tarde iniciará sesión.

    ![Escritura de un nombre de contenedor y credenciales al crear un contenedor](media/containers-window-create-fill.png)

1. RTVS puede tardar algún tiempo en generar la imagen. En la ventana **Salida** de Visual Studio se muestra el progreso, pero es posible que parezca que no hace mucho durante la descarga de imágenes grandes; esté preparado para tener que esperar. Una vez que se crea la imagen, RTVS inicia el contenedor y se muestra en la ventana **Contenedor**. Con los controles de la parte derecha se detiene, quita o reinicia el contenedor.

    ![Ventana Contenedores en la que se muestra un contenedor completado](media/containers-window-created.png)

## <a name="connect-to-a-container"></a>Conectarse a un contenedor

1. En la sección **Contenedores locales en ejecución** de la ventana **Áreas de trabajo** se muestran los contenedores que ejecutan el demonio de RTVS en el puerto 5444. (Vea [R Server remoto para Linux](setting-up-remote-r-service-on-linux.md) para obtener más información sobre cómo se configura el demonio).

    ![Ventana Áreas de trabajo en la que se muestran los contenedores disponibles](media/workspaces-window-running-containers.png)

1. Para conectarse a un contenedor, haga doble clic en el nombre del contenedor o haga clic en el botón de flecha hacia delante a su derecha. Una vez conectado, verá una ventana de **R interactivo** (vea [Trabajar con la ventana interactiva de R](interactive-repl-for-r-in-visual-studio.md)):

    ![Ventana Áreas de trabajo y ventana REPL abiertas para un contenedor](media/workspaces-window-container-connected.png)

## <a name="use-custom-built-images"></a>Usar imágenes personalizadas

RTVS detecta y permite administrar contenedores creados con imágenes personalizadas, como la imagen de microsoft/rtvs que se describe en el archivo de Docker siguiente. La imagen base que se usa aquí tiene preinstalado el demonio de RTVS, R 3.4.2 y paquetes de R habituales. **Nota**: Cambie el nombre de usuario y la contraseña que se muestran aquí según sea necesario.

```docker
FROM microsoft/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

Use el comando siguiente para generar la imagen y cambie el nombre del contenedor (el argumento `--name`) como quiera:

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

El argumento `-p 6056:5444` asigna el puerto 6056 al puerto interno 5444, que RTVS usa para detectar rtvs-daemon. Cualquier contenedor que expone el puerto de contenedor 5444 aparece en la ventana **Áreas de trabajo**. Después, puede usar la ventana **Áreas de trabajo** para conectarse a un contenedor mediante `<<unix>>\ruser1` como nombre de usuario y "foobar" como contraseña, a menos que especifique credenciales diferentes en el archivo de Docker.
