---
title: Registros de contenedores, variables de entorno y acceso al sistema de archivos
description: Describe cómo mejorar la capacidad de depurar y diagnosticar las aplicaciones basadas en contenedores en Visual Studio mediante una ventana de herramientas para ver lo que está ocurriendo dentro de los contenedores que hospedan la aplicación.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 05/06/2019
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: 3fb9a52f990a2e492c63a6e71a7cc2063110c816
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "71126098"
---
# <a name="how-to-view-and-diagnose-containers-in-visual-studio"></a>Cómo ver y diagnosticar contenedores en Visual Studio

Puede ver lo que está ocurriendo dentro de los contenedores que hospedan la aplicación mediante la ventana de **contenedores**. Si suele usar el símbolo del sistema para ejecutar los comandos de Docker con el fin de ver y diagnosticar lo que está ocurriendo con los contenedores, esta ventana proporciona una manera más cómoda de supervisar los contenedores sin tener que cerrar el IDE de Visual Studio.

> [!NOTE]
> La ventana de contenedores está disponible actualmente como una extensión de versión preliminar que puede [descargar](https://aka.ms/vscontainerspreview) para Visual Studio 2019.

## <a name="prerequisites"></a>Requisitos previos

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- Instalación de [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
- Instalación de la [extensión de la ventana de contenedores](https://aka.ms/vscontainerspreview)

## <a name="view-information-about-your-containers"></a>Visualización de información acerca de los contenedores

La ventana de **contenedores** se abre automáticamente al iniciar un proyecto de .NET en contenedores. Para ver los contenedores en Visual Studio en cualquier momento, use **Ctrl**+**Q** para activar el cuadro de búsqueda de Visual Studio, escriba `Containers` y elija el primer elemento. También puede abrir la ventana de **contenedores** desde el menú principal. Use la ruta de acceso del menú **Ver** > **Otras ventanas** > **Contenedores**.  

![Captura de pantalla de la pestaña Entorno en la ventana de contenedores](media/view-and-diagnose-containers/container-window.png)

En el lado izquierdo, verá la lista de contenedores en el equipo local. Los contenedores asociados a la solución se muestran en **Contenedores de soluciones**. A la derecha, verá un panel con pestañas para **Entorno**, **Puertos**, **Registros** y **Archivos**.

> [!TIP]
> Puede personalizar fácilmente el lugar en el que la ventana de herramientas **Contenedores** está acoplada en Visual Studio. Consulte [Personalizar los diseños de ventana de Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio). De forma predeterminada, la ventana de **contenedores** está acoplada con la ventana **Inspección** cuando el depurador está en ejecución.

## <a name="view-environment-variables"></a>Visualización de variables de entorno

En la pestaña **Entorno** se muestran las variables de entorno del contenedor. En el caso del contenedor de la aplicación, puede establecer estas variables de muchas maneras, por ejemplo, en el archivo Dockerfile, en un archivo .env o mediante la opción -e al iniciar un contenedor mediante un comando de Docker.

![Captura de pantalla de la pestaña Entorno en la ventana de contenedores](media/view-and-diagnose-containers/container-environment-vars.png)

> [!NOTE]
> Los cambios en las variables de entorno no se reflejan en tiempo real. Además, las variables de entorno en esta pestaña son las variables de entorno del sistema en el contenedor y no reflejan las variables de entorno del usuario locales en la aplicación.

## <a name="view-port-mappings"></a>Visualización de asignaciones de puertos

En la pestaña **Puertos**, puede comprobar las asignaciones de puertos que están en vigor para su contenedor.

![Captura de pantalla de la pestaña Puertos en la ventana de contenedores](media/view-and-diagnose-containers/container-ports.png)

Los puertos conocidos están vinculados, por lo que si hay contenido disponible en un puerto, puede hacer clic en el vínculo para abrir el explorador.

## <a name="view-logs"></a>Visualización de registros

En la pestaña **Registros** se muestran los resultados del comando `docker logs`. De forma predeterminada, la pestaña muestra las secuencias stdout y stderr en un contenedor, pero puede configurar la salida. Para obtener más información, vea [Registro de Docker](https://docs.docker.com/config/containers/logging/).  De forma predeterminada, la pestaña **Registros** transmite los registros, pero puede deshabilitarlo eligiendo el botón **Detener** en la pestaña.

![Captura de pantalla de la pestaña Registros en la ventana de contenedores](media/view-and-diagnose-containers/containers-logs.jpg)

Para borrar los registros, use el botón **Borrar** en la pestaña **Registros**.  Para obtener todos los registros, use el botón **Actualizar**.

> [!NOTE]
> Visual Studio redirige automáticamente stdout y stderr a la ventana **Salida**, de modo que los contenedores se inician desde Visual Studio (es decir, los contenedores de la sección **Contenedores de soluciones**) no mostrarán los registros en esta pestaña. En su lugar, use la ventana **Salida**.

## <a name="view-the-filesystem"></a>Visualización del sistema de archivos

En la pestaña **Archivos**, puede ver el sistema de archivos del contenedor, incluida la carpeta de la aplicación que contiene el proyecto.

![Captura de pantalla de la pestaña Archivos en la ventana de contenedores](media/view-and-diagnose-containers/container-filesystem.png)

Para abrir archivos en Visual Studio, busque el archivo y haga doble clic en él, o haga clic con el botón derecho y elija **Abrir**. Visual Studio abre los archivos en modo de solo lectura.

![Captura de pantalla del archivo abierto para verlo en Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

Con la pestaña **Archivos**, puede ver registros de aplicaciones como registros de IIS, archivos de configuración y otros archivos de contenido en el sistema de archivos del contenedor.

## <a name="start-stop-and-remove-containers"></a>Iniciar, detener y quitar contenedores

De forma predeterminada, la ventana de **contenedores** muestra todos los contenedores de la máquina que administra Docker. Puede usar los botones de la barra de herramientas para iniciar, detener o quitar (eliminar) un contenedor que ya no desee.  Esta lista se actualiza de forma dinámica a medida que se crean o se quitan contenedores.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre las herramientas de contenedor disponibles en Visual Studio, lea la [información general sobre herramientas de contenedor](overview.md).

## <a name="see-also"></a>Vea también

[Desarrollo de contenedores en Visual Studio](/visualstudio/containers)

[Marketplace de extensiones para Visual Studio](https://marketplace.visualstudio.com/)
