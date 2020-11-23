---
title: Asociación a procesos que se ejecutan en contenedores de Docker
description: Aprenda a depurar una aplicación que ejecuta un contenedor de Docker mediante Visual Studio
ms.date: 11/11/2020
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux Docker container
- debugging, Docker container
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 5b32b402e2bbf85cf5c028ec2dc94821ec463644
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94674795"
---
# <a name="attach-to-a-process-running-on-a-docker-container"></a>Asociación a procesos que se ejecutan en contenedores de Docker 

Con Visual Studio, puede depurar aplicaciones que se ejecutan en un contenedor de Docker en Windows o en un contenedor de Docker de .NET Core en Linux.

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a> Asociación a un proceso que se ejecuta en un contenedor de Docker de Linux

Puede asociar el depurador de Visual Studio a un proceso que se ejecuta en un contenedor de Docker de .NET Core de Linux en el equipo local o remoto mediante el cuadro de diálogo **Asociar al proceso**.

> [!IMPORTANT]
> Para usar esta característica, debe instalar la carga de trabajo de desarrollo multiplataforma de .NET Core y tener acceso local al código fuente.

**Para asociar a un proceso en ejecución en un contenedor de Docker de Linux:**

1. En Visual Studio, seleccione **Depurar > Asociar al proceso (CTRL + ALT + P)** para abrir el cuadro de diálogo **Asociar al proceso**.

![Menú Asociar al proceso](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Establezca **Tipo de conexión** en **Docker (contenedor de Linux)** .
3. Seleccione **Buscar...** para establecer el **Destino de conexión** mediante el cuadro de diálogo **Seleccionar contenedor de Docker**.

    Puede depurar un proceso de contenedor de Docker de forma local o remota.

    **Para depurar un proceso de contenedor de Docker localmente:**
    1. Establezca **Docker CLI host** (Host de CLI de Docker) en **Máquina local**.
    1. Seleccione un contenedor en ejecución con el que establecer la conexión de la lista y presione **Aceptar**.

    ![Menú para seleccionar contenedor de Docker](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")

    **B. Para depurar un proceso de contenedor de Docker de forma remota:**

    > [!NOTE]
    > Hay dos opciones para establecer una conexión remota con un proceso en ejecución en un contenedor de Docker. La primera opción, usar SSH, es idónea si no tiene herramientas de Docker instaladas en la máquina local.  Si tiene herramientas de Docker instaladas localmente y tiene un demonio de Docker que está configurado para aceptar solicitudes remotas, pruebe la segunda opción: usar un demonio de Docker.

    1. **_Para conectarse a una máquina remota a través de SSH:_*
        1. Seleccione *Agregar...* para conectarse a un sistema remoto.<br/>
        ![Conectar con el sistema remoto](../debugger/media/connect-remote-system.png "Conexión con el sistema remoto")
        1. Seleccione un contenedor en ejecución al que asociarse después de conectarse correctamente al SSH o el demonio y haga clic en **Aceptar**.

    1. **_Para establecer el destino en un contenedor remoto que ejecuta un proceso a través de un [demonio de Docker:](https://docs.docker.com/engine/reference/commandline/dockerd/)_*
        1. Especifique la dirección del demonio (es decir, a través de TCP, IP, etc.) en *Docker host (Optional)* (Host de Docker [opcional]) y haga clic en el vínculo para actualizar.
        1. Seleccione un contenedor en ejecución al que asociarse después de conectarse al demonio correctamente y haga clic en **Aceptar**.

4. Elija el proceso de contenedor correspondiente en la lista **Procesos disponibles** y seleccione **Asociar** para empezar a depurar el proceso de contenedor de C# en Visual Studio.

    ![Menú para asociar Docker completado](../debugger/media/docker-attach-complete.png "Menú de conexión de Docker de Linux completado")

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a> Asociación a un proceso que se ejecuta en un contenedor de Docker de Windows

Puede asociar el depurador de Visual Studio a un proceso que se ejecuta en un contenedor de Docker de Windows en el equipo local mediante el cuadro de diálogo **Asociar al proceso**.

> [!IMPORTANT]
> Para usar esta característica con un proceso de .NET Core, debe instalar la carga de trabajo de desarrollo multiplataforma de .NET Core y tener acceso local al código fuente.

**Para asociar a un proceso en ejecución en un contenedor de Docker de Windows:**

1. En Visual Studio, seleccione **Depurar > Asociar al proceso** (o **CTRL + ALT + P**) para abrir el cuadro de diálogo **Asociar al proceso**.

   ![Menú Asociar al proceso](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Establezca **Tipo de conexión** en **Docker (contenedor de Windows)** .
3. Seleccione **Buscar...** para establecer el **Destino de conexión** mediante el cuadro de diálogo **Seleccionar contenedor de Docker**.

    > [!IMPORTANT]
    > El proceso de destino debe tener la misma arquitectura de procesador que el contenedor de Windows de Docker en el que se está ejecutando.

   El establecimiento del destino en un contenedor remoto a través de SSH no está disponible actualmente y solo puede realizarse mediante un demonio de Docker.

    **_Para establecer el destino en un contenedor remoto que ejecuta un proceso a través de un [demonio de Docker:](https://docs.docker.com/engine/reference/commandline/dockerd/)_*
    1. Especifique la dirección del demonio (es decir, a través de TCP, IP, etc.) en *Docker host (Optional)* (Host de Docker [opcional]) y haga clic en el vínculo para actualizar.

    1. Seleccione un contenedor en ejecución al que asociarse después de conectarse al demonio correctamente y seleccione Aceptar.

4. Elija el proceso de contenedor correspondiente en la lista **Procesos disponibles** y seleccione **Asociar** para empezar a depurar el proceso de contenedor de C#.

    ![Menú para asociar Docker completado](../debugger/media/docker-attach-complete-windows.png "Menú de conexión de Docker de Windows completado")

5.  Elija el proceso de contenedor correspondiente en la lista de procesos disponibles y seleccione **Asociar** para empezar a depurar el proceso de contenedor de C#.