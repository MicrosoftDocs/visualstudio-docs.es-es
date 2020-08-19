---
title: Asociación a los procesos en ejecución con el depurador | Microsoft Docs
ms.custom: seodec18
ms.date: 06/12/2020
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4b4a90cc06396f9fb6afb8a356385e966ed1b3d
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2020
ms.locfileid: "88249211"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Asociar con procesos en ejecución con el depurador de Visual Studio

Puede asociar el depurador de Visual Studio a un proceso en ejecución en un equipo local o remoto. Una vez que el proceso se esté ejecutando, seleccione **Depurar** > **Asociar al proceso** o presione **Ctrl**+**Alt**+**P** en Visual Studio y use el cuadro de diálogo **Asociar al proceso** para asociar el depurador al proceso.

Puede usar **Asociar al proceso** para depurar aplicaciones en ejecución en equipos locales o remotos, depurar varios procesos simultáneamente, depurar aplicaciones que no se crearon en Visual Studio o depurar cualquier aplicación que no se haya iniciado desde Visual Studio con el depurador asociado. Por ejemplo, si está ejecutando una aplicación sin el depurador y alcanza una excepción, puede asociar el depurador al proceso que ejecuta la aplicación y comenzar la depuración.

> [!TIP]
> ¿No está seguro de si usar **Asociar al proceso** para su escenario de depuración? Vea [Escenarios comunes de depuración](#BKMK_Scenarios).

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Asociación con un proceso en ejecución en el equipo local

Para volver a asociar rápidamente a un proceso que ha asociado previamente, consulte [Reasociar a un proceso](#BKMK_reattach).

**Para asociar a un proceso en el equipo local:**

1. En Visual Studio, seleccione **Depurar** > **Asociar al proceso** (o presione **Ctrl**+**Alt**+**P**) para abrir el cuadro de diálogo **Asociar al proceso**.

1. Compruebe el **tipo de conexión**.

   En la mayoría de los escenarios, puede usar el **valor predeterminado**. Algunos escenarios pueden requerir un tipo de conexión diferente. Para obtener más información, consulte otras secciones de este artículo o [escenarios comunes de depuración](#BKMK_Scenarios).

1. Establezca el **destino de la conexión** en el nombre de la máquina local.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

1. En la lista **Procesos disponibles**, busque y seleccione el proceso o los procesos con los que quiere establecer la asociación.

   - Para seleccionar rápidamente un proceso, escriba su nombre o su primera letra en el cuadro **Filtrar procesos**.

   - Si no conoce el nombre del proceso, desplácese por la lista o consulte [Escenarios comunes de depuración](#BKMK_Scenarios) para ver algunos nombres de proceso comunes.

   >[!TIP]
   >Los procesos se pueden iniciar y detener en segundo plano mientras el cuadro de diálogo **Asociar al proceso** está abierto, por lo que la lista de procesos en ejecución puede no estar siempre actualizada. Puede seleccionar **Actualizar** en cualquier momento para ver la lista actual.

1. En el campo **Asociar a**, asegúrese de que aparece el tipo de código que va a depurar. El parámetro **Automático** predeterminado funciona en la mayoría de los tipos de aplicaciones.

   Si usa el tipo de conexión **predeterminado**, puede seleccionar manualmente el tipo de código al que desee establecer una asociación. De lo contrario, la opción **Seleccionar** puede deshabilitarse.

   Para seleccionar tipos de código manualmente:
   1. Haga clic en **Seleccionar**.
   1. En el cuadro de diálogo **Seleccionar tipo de código**, seleccione **Depurar estos tipos de código**.
      Si se produce un error al intentar establecer una asociación a un proceso de la lista, puede usar el cuadro de diálogo [Seleccionar tipo de código](../debugger/select-code-type-dialog-box.md) para ayudar a [solucionar](#BKMK_Troubleshoot_attach_errors) la incidencia.
   1. Seleccione los tipos de código que desea depurar.
   1. Seleccione **Aceptar**.

1. Seleccione **Adjuntar**.

>[!NOTE]
>Puede tener asociaciones con varias aplicaciones para la depuración, pero solo una aplicación está activa en el depurador a la vez. Puede establecer la aplicación activa en la barra de herramientas **Ubicación de depuración** o la ventana **Procesos** de Visual Studio.

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Asociar a un proceso en un equipo remoto

También puede seleccionar un equipo remoto en el cuadro de diálogo **Asociar al proceso**, consultar una lista con los procesos disponibles que se están ejecutando en dicho equipo y establecer una asociación con uno o varios procesos para llevar a cabo la depuración. El depurador remoto (*msvsmon. exe*) debe ejecutarse en el equipo remoto. Para obtener más información, vea [Depuración remota](../debugger/remote-debugging.md).

Para obtener instrucciones más completas sobre cómo depurar aplicaciones ASP.NET que se han implementado en IIS, vea [Depuración remota de ASP.NET en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Para establecer una asociación con un proceso en ejecución en un equipo remoto:**

1. En Visual Studio, seleccione **Depurar** > **Asociar al proceso** (o presione **Ctrl**+**Alt**+**P**) para abrir el cuadro de diálogo **Asociar al proceso**.

1. Compruebe el **tipo de conexión**.

   En la mayoría de los escenarios, puede usar el **valor predeterminado**. Algunos escenarios, como la depuración de Linux o una aplicación en contenedores, requieren un tipo de conexión diferente. Para obtener más información, consulte otras secciones de este artículo o [escenarios comunes de depuración](#BKMK_Scenarios).

1. En el cuadro **Destino de conexión**, seleccione el equipo remoto mediante uno de los métodos siguientes:

   - Seleccione la flecha desplegable situada junto a **Destino de conexión** y seleccione el nombre del equipo en la lista desplegable.
   - Escriba el nombre del equipo en el cuadro **Destino de conexión** y presione **Entrar**.

     Compruebe que Visual Studio agrega el puerto necesario al nombre del equipo, que aparece en el formato **\<remote computer name>:puerto**.

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Si no puede conectarse con el nombre del equipo remoto, pruebe a usar la dirección IP y el puerto (por ejemplo, `123.45.678.9:4022`). 4024 es el puerto predeterminado para el depurador remoto de Visual Studio 2019 x64. Para otras asignaciones de puerto del depurador remoto, vea [Asignaciones de puerto del depurador remoto](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Si no puede conectarse con el nombre del equipo remoto, pruebe a usar la dirección IP y el puerto (por ejemplo, `123.45.678.9:4022`). 4022 es el puerto predeterminado para el depurador remoto de Visual Studio 2017 x64. Para otras asignaciones de puerto del depurador remoto, vea [Asignaciones de puerto del depurador remoto](remote-debugger-port-assignments.md).

     ::: moniker-end

   - Seleccione el botón **Buscar** situado junto al cuadro **Destino de conexión** para abrir el cuadro de diálogo **Conexiones remotas**. En el cuadro de diálogo **Conexiones remotas** se muestran todos los dispositivos que están en la subred local o conectados directamente al equipo. Es posible que necesite [abrir el puerto UDP 3702](../debugger/remote-debugger-port-assignments.md) en el servidor para detectar dispositivos remotos. Seleccione el equipo o el dispositivo que desee y, a continuación, haga clic en **Seleccionar**.

   > [!NOTE]
   > El parámetro **Tipo de conexión** se conserva entre las sesiones de depuración. El parámetro **Destino de la conexión** solo se conserva entre las sesiones de depuración si se produce una conexión de depuración correcta con ese destino.

3. Haga clic en **Actualizar** para rellenar la lista **Procesos disponibles**.

    >[!TIP]
    >Los procesos se pueden iniciar y detener en segundo plano mientras el cuadro de diálogo **Asociar al proceso** está abierto, por lo que la lista de procesos en ejecución puede no estar siempre actualizada. Puede seleccionar **Actualizar** en cualquier momento para ver la lista actual.

4. En la lista **Procesos disponibles**, busque y seleccione el proceso o los procesos con los que quiere establecer la asociación.

   - Para seleccionar rápidamente un proceso, escriba su nombre o su primera letra en el cuadro **Filtrar procesos**.

   - Si no conoce el nombre del proceso, desplácese por la lista o consulte [Escenarios comunes de depuración](#BKMK_Scenarios) para ver algunos nombres de proceso comunes.

   - Para buscar procesos que se ejecutan en todas las cuentas de usuario, active la casilla **Mostrar los procesos de todos los usuarios**.

     >[!NOTE]
     >Si intenta asociar a un proceso que pertenece a una cuenta de usuario que no es de confianza, aparecerá un cuadro de diálogo de confirmación con una advertencia de seguridad. Para obtener más información, vea [Advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario que no sea de confianza puede ser peligroso. Si la información siguiente le resulta sospechosa o no está seguro de su procedencia, no la adjunte a este proceso](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. En el campo **Asociar a**, asegúrese de que aparece el tipo de código que va a depurar. El parámetro **Automático** predeterminado funciona en la mayoría de los tipos de aplicaciones.

   Si usa el tipo de conexión **predeterminado**, puede seleccionar manualmente el tipo de código al que desee establecer una asociación. De lo contrario, la opción **Seleccionar** puede deshabilitarse.

   Para seleccionar tipos de código manualmente:
   1. Haga clic en **Seleccionar**.
   1. En el cuadro de diálogo **Seleccionar tipo de código**, seleccione **Depurar estos tipos de código**.
      Si se produce un error al intentar establecer una asociación a un proceso de la lista, puede usar el cuadro de diálogo [Seleccionar tipo de código](../debugger/select-code-type-dialog-box.md) para ayudar a [solucionar](#BKMK_Troubleshoot_attach_errors) la incidencia.
   1. Seleccione **Aceptar**.

6. Seleccione **Adjuntar**.

>[!NOTE]
>Puede tener asociaciones con varias aplicaciones para la depuración, pero solo una aplicación está activa en el depurador a la vez. Puede establecer la aplicación activa en la barra de herramientas **Ubicación de depuración** o la ventana **Procesos** de Visual Studio.

En algunos casos, al depurar en una sesión de Escritorio remoto (Terminal Services), en la lista **Procesos disponibles** no aparecerán todos los procesos disponibles. Si se ejecuta Visual Studio como usuario que tiene una cuenta de usuario limitada, la lista **Procesos disponibles** no mostrará los procesos que se estén ejecutando en la sesión 0. La sesión 0 se usa para los servicios y otros procesos de servidor, incluido *w3wp.exe*. Para resolver el problema, ejecute [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] con una cuenta de administrador o ejecute [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde la consola de servidor en lugar de una sesión de Terminal Services.

Si ninguna de estas dos soluciones es posible, existe una tercera opción que consiste en asociar al proceso mediante la ejecución de `vsjitdebugger.exe -p <ProcessId>` en la línea de comandos de Windows. Puede determinar el identificador de proceso mediante *tlist.exe*. Para obtener el archivo *tlist.exe*, descargue e instale las Herramientas de depuración para Windows, disponibles en  [Descargas de WDK y WinDbg](/windows-hardware/drivers/download-the-wdk).

::: moniker range=">= vs-2019"

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>Asociación a un proceso de .NET Core que se ejecuta en Linux mediante SSH

Para obtener más información, vea [Depuración remota de .NET Core en Linux con SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a> Asociación a un proceso que se ejecuta en un contenedor de Docker de Linux

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

    1. ***Para conectarse a un equipo remoto a través de SSH:***
        1. Seleccione **Agregar...** para conectarse a un sistema remoto.<br/>
        ![Conectar con el sistema remoto](../debugger/media/connect-remote-system.png "Conexión con el sistema remoto")
        1. Seleccione un contenedor en ejecución al que asociarse después de conectarse correctamente al SSH o el demonio y haga clic en **Aceptar**.

    1. ***Para establecer el destino en un contenedor remoto que ejecuta un proceso a través de un [demonio de Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)***
        1. Especifique la dirección del demonio (es decir, a través de TCP, IP, etc.) en **Docker host (Optional)** (Host de Docker [opcional]) y haga clic en el vínculo para actualizar.
        1. Seleccione un contenedor en ejecución al que asociarse después de conectarse al demonio correctamente y haga clic en **Aceptar**.

4. Elija el proceso de contenedor correspondiente en la lista **Procesos disponibles** y seleccione **Asociar** para empezar a depurar el proceso de contenedor de C# en Visual Studio.

    ![Menú para asociar Docker completado](../debugger/media/docker-attach-complete.png "Menú de conexión de Docker de Linux completado")    

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a><a name="BKMK_Windows_Docker_Attach"></a> Asociación a un proceso que se ejecuta en un contenedor de Docker de Windows

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
    
    ***Para establecer el destino en un contenedor remoto que ejecuta un proceso a través de un [demonio de Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)***
    1. Especifique la dirección del demonio (es decir, a través de TCP, IP, etc.) en **Docker host (Optional)** (Host de Docker [opcional]) y haga clic en el vínculo para actualizar. 

    1. Seleccione un contenedor en ejecución al que asociarse después de conectarse al demonio correctamente y seleccione Aceptar.
    
4. Elija el proceso de contenedor correspondiente en la lista **Procesos disponibles** y seleccione **Asociar** para empezar a depurar el proceso de contenedor de C#.

    ![Menú para asociar Docker completado](../debugger/media/docker-attach-complete-windows.png "Menú de conexión de Docker de Windows completado")

5.  Elija el proceso de contenedor correspondiente en la lista de procesos disponibles y seleccione **Asociar** para empezar a depurar el proceso de contenedor de C#.

::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a> Reasociar a un proceso

Puede volver a asociarse rápidamente a los procesos a los que se asoció con anterioridad eligiendo **Depurar** > **Reasociar al proceso** (**Mayús**+**Alt**+**P**). Cuando se elige este comando, el depurador intentará asociarse de inmediato a los últimos procesos a los que se haya asociado intentando buscar una coincidencia con el identificador de proceso anterior y, si no obtiene resultados, con el nombre del proceso anterior. Si no se encuentran coincidencias, o si hay varios procesos con el mismo nombre, se abrirá el cuadro de diálogo **Asociar al proceso** para que pueda seleccionar el proceso correcto.

> [!NOTE]
> El comando **Reasociar al proceso** está disponible a partir de Visual Studio 2017.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> Escenarios comunes de depuración

Para ayudarle a determinar si debe usar **Asociar al proceso** y a qué proceso se debe asociar, en la tabla siguiente se muestran algunos escenarios comunes de depuración, con vínculos que llevan a más instrucciones si están disponibles. (Esta lista no es exhaustiva).

En el caso de algunos tipos de aplicaciones, como una Aplicación Windows universal (UWP), no se asocia directamente a un nombre de proceso, sino que se usa en su lugar la opción de menú **Depurar paquete de aplicaciones instalado** de Visual Studio (vea la tabla).

Para que el depurador se asocie al código escrito en C++, el código debe emitir `DebuggableAttribute`. Puede agregar este atributo automáticamente al código vinculando con la opción [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) del vinculador.

Para la depuración de scripts del lado cliente, la depuración de scripts debe estar habilitada en el explorador. Para depurar el script de cliente en Chrome, elija **JavaScript (Chrome)** o **JavaScript (Microsoft Edge - Chromium)** como tipo de código y, en función del tipo de aplicación, es posible que necesite cerrar todas las instancias de Chrome e iniciar el explorador en modo de depuración (escriba `chrome.exe --remote-debugging-port=9222` desde una línea de comandos). En versiones anteriores de Visual Studio, el depurador de scripts para Chrome era **Web kit**.

Para seleccionar rápidamente un proceso en ejecución al que asociarse, en Visual Studio, escriba **Ctrl**+**Alt**+**P**y, a continuación, escriba la primera letra del nombre del proceso.

|Escenario|Método de depuración|Nombre del proceso|Notas y vínculos|
|-|-|-|-|
|Depuración remota de ASP.NET 4 o 4.5 en un servidor IIS|Uso de herramientas remotas y **Asociar al proceso**|*w3wp.exe*|Vea [Depuración remota de ASP.NET en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).|
|Depuración remota de ASP.NET Core en un servidor de IIS|Uso de herramientas remotas y **Asociar al proceso**|*w3wp.exe* o *dotnet.exe*|A partir de .NET Core 3, el proceso *w3wp.exe* se usa para el [modelo de hospedaje en la aplicación](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models) predeterminado. Para la implementación de aplicaciones, vea [Publicación en IIS](/aspnet/core/host-and-deploy/iis/). Para obtener información más detallada, vea [Depuración remota de ASP.NET Core en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach)|
|Depuración del script del lado cliente en un servidor IIS local, para los tipos de aplicaciones compatibles |Uso de **Asociar al proceso**|*chrome.exe*, *MicrosoftEdgeCP.exe* o *iexplore.exe*|La depuración de scripts debe estar habilitada. Para Chrome, también debe ejecutar Chrome en modo de depuración (escriba `chrome.exe --remote-debugging-port=9222` desde una línea de comandos) y seleccionar **JavaScript (Chrome)** en el campo **Asociar a**.|
|Depuración de una aplicación de C#, Visual Basic o C++ en la máquina local|Uso de la depuración estándar (**F5**) o **Asociar al proceso**|*\<appname>.exe*|En la mayoría de los escenarios, use la depuración estándar y no **Asociar al proceso**.|
|Depuración remota de una aplicación de escritorio de Windows|Herramientas remotas|N/D| Consulte [Depuración de una aplicación de C# o Visual Basic](../debugger/remote-debugging-csharp.md) o [Depuración remota de un proyecto C++](../debugger/remote-debugging-cpp.md).|
|Depuración de .NET Core en Linux|Uso de **Asociar al proceso**|*dotnet.exe*|Para usar SSH, consulte [Depuración remota de .NET Core en Linux con SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md). En el caso de las aplicaciones en contenedores, consulte las secciones anteriores de este artículo.|
|Depuración remota de Python en Linux|Uso de **Asociar al proceso**|*debugpy*|Consulte [Asociar desde Herramientas de Python de forma remota](../python/debugging-python-code-on-remote-linux-machines.md#attach-remotely-from-python-tools)|
|Depuración de una aplicación de ASP.NET en el equipo local después de iniciar la aplicación sin el depurador|Uso de **Asociar al proceso**|*iiexpress.exe*|Puede resultar útil para agilizar la carga de la aplicación, como (por ejemplo,) al generar perfiles. |
|Depuración de otros tipos de aplicaciones compatibles en un proceso de servidor|Si el servidor es remoto, use herramientas remotas y **Asociar al proceso**.|*chrome.exe*, *iexplore.exe* u otros procesos|Si es necesario, utilice Monitor de recursos para identificar mejor el proceso. Vea [Depuración remota](../debugger/remote-debugging.md).|
|Depuración remota de una Aplicación Windows universal (UWP), OneCore, HoloLens o IoT|Depurar paquete de aplicaciones instalado|N/D|Consulte [Depurar un paquete de aplicación instalado](debug-installed-app-package.md) en lugar de usar **Asociar al proceso**.|
|Depuración de una Aplicación Windows universal (UWP), OneCore, HoloLens o IoT que no se inició desde Visual Studio|Depurar paquete de aplicaciones instalado|N/D|Consulte [Depurar un paquete de aplicación instalado](debug-installed-app-package.md) en lugar de usar **Asociar al proceso**.|

## <a name="use-debugger-features"></a>Uso de las características del depurador

Para usar todas las características del depurador de Visual Studio (como las llegadas a un punto de interrupción) al asociarse a un proceso, la aplicación debe coincidir exactamente con el código fuente y los símbolos locales. Es decir, el depurador debe ser capaz de cargar los [archivos de símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) correctos. De forma predeterminada, esto requiere una compilación de depuración.

En escenarios de depuración remota, debe tener el código fuente (o una copia del código fuente) ya abierto en Visual Studio. Los archivos binarios de la aplicación compilada en el equipo remoto deben provenir de la misma compilación que en el equipo local.

En algunos escenarios de depuración local, puede depurar en Visual Studio sin acceso al origen si los archivos de símbolos correctos están presentes en la aplicación. De forma predeterminada, esto requiere una compilación de depuración. Para obtener más información, vea [Especificar archivos de código fuente y símbolos en el depurador de Visual Studio (C#, C++, Visual Basic, F#)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Solucionar problemas de errores de asociación

En algunos escenarios, es posible que el depurador necesite ayuda para identificar correctamente el tipo de código que se va a depurar. Si los valores de conexión se establecen correctamente (puede ver el proceso correcto en la lista **Procesos disponibles**), pero el depurador no se asocia, intente seleccionar el tipo de conexión más adecuado en la lista **Tipo de conexión**, que puede requerirse, por ejemplo, si depura una aplicación de Linux o Python. Si usa el tipo de conexión predeterminado, también puede seleccionar el tipo específico de código al que conectarse, como se describe más adelante en esta sección.

Cuando el depurador se asocia a un proceso en ejecución, el proceso puede contener uno o varios tipos de código. Los tipos de código a los que se puede asociar el depurador se muestran y seleccionan en el cuadro de diálogo [Seleccionar tipo de código](../debugger/select-code-type-dialog-box.md) .

A veces, el depurador puede asociarse correctamente a un tipo de código, pero no a otro. Normalmente, esto ocurre cuando:

- Intenta establecer una asociación a un proceso que se ejecuta en un equipo remoto. Puede que el equipo remoto tenga instalados los componentes de depuración remota para algunos tipos de código, pero no para otros.
- Intenta establecer una asociación a dos o varios procesos para realizar una depuración directa de la base de datos. La depuración de SQL sólo admite la asociación a un único proceso.

Si el depurador logra asociarse a algunos tipos de código, pero no a todos, aparece un mensaje en el que se identifican los tipos sin asociar.

Si el depurador se asocia correctamente a un tipo de código por lo menos, podrá reanudar la depuración del proceso. Sólo podrá depurar los tipos de código que se hayan asociado correctamente. El código sin asociar del proceso seguirá ejecutándose, pero no se podrán establecer puntos de interrupción, ni se podrán ver los datos, ni se podrá realizar ninguna otra operación de depuración en el código.

Si desea obtener información más detallada sobre el motivo por el que el depurador no se ha asociado correctamente a un tipo de código, intente asociarlo de nuevo con ese tipo de código exclusivamente.

**Para obtener información específica sobre la causa por la que no se ha asociado correctamente un tipo de código:**

1. Desasocie el proceso. En el menú **Depurar**, seleccione **Desasociar todo**.

1. Vuelva a asociar el proceso, pero seleccionando solo el tipo de código que no se pudo asociar.

    1. En el cuadro de diálogo **Asociar al proceso**, seleccione el proceso en la lista **Procesos disponibles**.

    2. Elija **Seleccionar**.

    3. En el cuadro de diálogo **Seleccionar tipo de código** , seleccione **Depurar estos tipos de código** y el tipo de código que no se haya asociado correctamente. Anule la selección de los otros tipos de código.

    4. Seleccione **Aceptar**.

    5. En el cuadro de diálogo **Asociar al proceso**, seleccione **Asociar**.

    Esta vez se producirá un error en todo el proceso de asociación y aparecerá un mensaje de error específico.

## <a name="see-also"></a>Vea también

- [Depuración de varios procesos](../debugger/debug-multiple-processes.md)
- [Depuración Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Depuración remota](../debugger/remote-debugging.md)
