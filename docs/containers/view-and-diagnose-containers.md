---
title: Visualización y diagnóstico de contenedores e imágenes de Docker
description: Describe cómo mejorar la capacidad de depurar y diagnosticar las aplicaciones basadas en contenedores en Visual Studio mediante una ventana de herramientas para ver lo que está ocurriendo dentro de los contenedores que hospedan la aplicación.
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 01/20/2020
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: fd876e86cefcd0ce50aab02de8e7f4cf37d3ab51
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729228"
---
# <a name="how-to-view-and-diagnose-containers-and-images-in-visual-studio"></a>Visualización y diagnóstico de contenedores e imágenes en Visual Studio

Puede ver lo que está ocurriendo dentro de los contenedores que hospedan la aplicación mediante la ventana de **contenedores**. Si suele usar el símbolo del sistema para ejecutar los comandos de Docker con el fin de ver y diagnosticar lo que está ocurriendo con los contenedores, esta ventana proporciona una manera más cómoda de supervisar los contenedores sin tener que cerrar el IDE de Visual Studio.

## <a name="prerequisites"></a>Requisitos previos

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2019 versión 16.4 Preview 2](https://visualstudio.microsoft.com/downloads) o posterior, o bien, si usa una versión anterior de Visual Studio 2019, instale la [extensión de ventana de contenedores](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-containers-tools-extensions).

## <a name="view-information-about-your-containers"></a>Visualización de información acerca de los contenedores

La ventana de **contenedores** se abre automáticamente al iniciar un proyecto de .NET en contenedores. Para ver los contenedores en Visual Studio en cualquier momento, use **Ctrl**+**Q** para activar el cuadro de búsqueda de Visual Studio, escriba `Containers` y elija el primer elemento. También puede abrir la ventana de **contenedores** desde el menú principal. Use la ruta de acceso del menú **Ver** > **Otras ventanas** > **Contenedores**.  

![Captura de pantalla de la ventana Contenedores en Visual Studio con un contenedor seleccionado en el panel izquierdo y la pestaña Entorno seleccionada en el panel derecho.](media/view-and-diagnose-containers/container-window.png)

En el lado izquierdo, verá la lista de contenedores en el equipo local. Los contenedores asociados a la solución se muestran en **Contenedores de soluciones**. A la derecha, verá un panel con pestañas para **Entorno**, **Puertos**, **Registros** y **Archivos**.

> [!TIP]
> Puede personalizar fácilmente el lugar en el que la ventana de herramientas **Contenedores** está acoplada en Visual Studio. Consulte [Personalizar los diseños de ventana de Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). De forma predeterminada, la ventana de **contenedores** está acoplada con la ventana **Inspección** cuando el depurador está en ejecución.

## <a name="view-environment-variables"></a>Visualización de variables de entorno

En la pestaña **Entorno** se muestran las variables de entorno del contenedor. En el caso del contenedor de la aplicación, puede establecer estas variables de muchas maneras, por ejemplo, en el archivo Dockerfile, en un archivo .env o mediante la opción -e al iniciar un contenedor mediante un comando de Docker.

![Captura de pantalla de la ventana Contenedores en Visual Studio en la que se muestran las variables de entorno para el contenedor WebApplication11.](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> Los cambios en las variables de entorno no se reflejan en tiempo real. Además, las variables de entorno en esta pestaña son las variables de entorno del sistema en el contenedor y no reflejan las variables de entorno del usuario locales en la aplicación.

## <a name="view-port-mappings"></a>Visualización de asignaciones de puertos

En la pestaña **Puertos**, puede comprobar las asignaciones de puertos que están en vigor para su contenedor.

![Captura de pantalla de la pestaña Puertos en la ventana de contenedores](media/view-and-diagnose-containers/containers-ports.png)

Los puertos conocidos están vinculados, por lo que si hay contenido disponible en un puerto, puede hacer clic en el vínculo para abrir el explorador.

## <a name="view-logs"></a>Visualización de registros

En la pestaña **Registros** se muestran los resultados del comando `docker logs`. De forma predeterminada, la pestaña muestra las secuencias stdout y stderr en un contenedor, pero puede configurar la salida. Para obtener más información, vea [Registro de Docker](https://docs.docker.com/config/containers/logging/).  De forma predeterminada, la pestaña **Registros** transmite los registros, pero puede deshabilitarlo eligiendo el botón **Detener** en la pestaña.

![Captura de pantalla de la pestaña Registros en la ventana de contenedores](media/view-and-diagnose-containers/containers-logs.png)

Para borrar los registros, use el botón **Borrar** en la pestaña **Registros**.  Para obtener todos los registros, use el botón **Actualizar**.

> [!NOTE]
> Visual Studio redirige automáticamente stdout y stderr a la ventana **Salida** cuando realiza la ejecución sin depurar con contenedores de Windows, por lo que los contenedores de Windows iniciados desde Visual Studio mediante **Ctrl**+**F5** no mostrarán los registros en esta pestaña. En su lugar, use la ventana **Salida**.

## <a name="view-the-filesystem"></a>Visualización del sistema de archivos

En la pestaña **Archivos**, puede ver el sistema de archivos del contenedor, incluida la carpeta de la aplicación que contiene el proyecto.

![Captura de pantalla de la pestaña Archivos en la ventana de contenedores](media/view-and-diagnose-containers/container-filesystem.png)

Para abrir archivos en Visual Studio, busque el archivo y haga doble clic en él, o haga clic con el botón derecho y elija **Abrir**. Visual Studio abre los archivos en modo de solo lectura.

![Captura de pantalla del archivo abierto para verlo en Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

Con la pestaña **Archivos**, puede ver registros de aplicaciones como registros de IIS, archivos de configuración y otros archivos de contenido en el sistema de archivos del contenedor.

## <a name="start-stop-and-remove-containers"></a>Iniciar, detener y quitar contenedores

De forma predeterminada, la ventana de **contenedores** muestra todos los contenedores de la máquina que administra Docker. Puede usar los botones de la barra de herramientas para iniciar, detener o quitar (eliminar) un contenedor que ya no desee.  Esta lista se actualiza de forma dinámica a medida que se crean o se quitan contenedores.

## <a name="open-a-terminal-window-in-a-running-container"></a>Apertura de una ventana de terminal en un contenedor en ejecución

Puede abrir una ventana de terminal (símbolo del sistema o shell interactivo) en el contenedor mediante el botón **Abrir ventana de terminal**  de la ventana **Contenedor**.

![Captura de pantalla de Abrir ventana de terminal en la ventana Contenedores](media/view-and-diagnose-containers/containers-open-terminal-window.png)

En los contenedores de Windows, se abre el símbolo del sistema de Windows. En el caso de los contenedores de Linux, se abre una ventana con el shell de Bash.

![Captura de pantalla de la ventana de Bash](media/view-and-diagnose-containers/container-bash-window.png)

Normalmente, la ventana de terminal se abre fuera de Visual Studio como una ventana independiente. Si desea un entorno de línea de comandos integrado en el IDE de Visual Studio como una ventana de herramientas acoplable, puede instalar [Whack Whack Terminal](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal).

## <a name="attach-the-debugger-to-a-process"></a>Asociación del depurador a un proceso

Puede asociar el depurador a un proceso que se esté ejecutando en el contenedor mediante el botón **Asociar al proceso** de la barra de herramientas de la ventana Contenedores. Cuando se usa este botón, aparece el cuadro de diálogo **Asociar al proceso** y se muestran los procesos disponibles que se están ejecutando en el contenedor.  

![Captura de pantalla del cuadro de diálogo Asociar al proceso](media/view-and-diagnose-containers/containers-attach-to-process.jpg)

Puede realizar la asociación a procesos administrados en el contenedor. Para buscar un proceso en otro contenedor, use el botón **Buscar** y seleccione otro contenedor en el cuadro de diálogo **Seleccionar contenedor de Docker**.

## <a name="viewing-images"></a>Visualización de imágenes

También puede ver imágenes en el equipo local mediante la pestaña **Imágenes** de la ventana **Contenedores**. Las imágenes extraídas de repositorios externos se agrupan juntas en una vista de árbol. Seleccione una imagen para inspeccionar los detalles de la imagen.

Para quitar una imagen, haga clic con el botón derecho en la imagen en la vista de árbol y elija **Quitar**, o seleccione la imagen y use el botón **Quitar** de la barra de herramientas.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre las herramientas de contenedor disponibles en Visual Studio, lea la [información general sobre herramientas de contenedor](overview.md).

## <a name="see-also"></a>Vea también

[Desarrollo de contenedores en Visual Studio](./index.yml)

[Marketplace de extensiones para Visual Studio](https://marketplace.visualstudio.com/)