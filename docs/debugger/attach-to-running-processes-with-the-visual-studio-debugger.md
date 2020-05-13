---
title: Adjuntar a los procesos en ejecución con el depurador . Microsoft Docs
ms.custom: seodec18
ms.date: 04/14/2020
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
ms.openlocfilehash: 075f5b0df703e31ea265085f422567a4fb5298a4
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385493"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Asociar con procesos en ejecución con el depurador de Visual Studio
Puede asociar el depurador de Visual Studio a un proceso en ejecución en un equipo local o remoto. Después de ejecutar el proceso, seleccione **Depurar** > **adjuntar al proceso** o presione **Ctrl**+**Alt**+**P** en Visual Studio y use el asociar **al proceso** diálogo para asociar el depurador al proceso.

Puede usar **Adjuntar al proceso** para depurar aplicaciones en ejecución en equipos locales o remotos, depurar varios procesos simultáneamente, depurar aplicaciones que no se crearon en Visual Studio o depurar cualquier aplicación que no haya iniciado desde Visual Studio con el depurador adjunto. Por ejemplo, si está ejecutando una aplicación sin el depurador y alcanza una excepción, puede asociar el depurador al proceso que ejecuta la aplicación y comenzar la depuración.

> [!TIP]
> ¿No está seguro de si desea usar **Adjuntar al proceso** para su escenario de depuración? Consulte [Escenarios de depuración comunes](#BKMK_Scenarios).

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a>Adjuntar a un proceso en ejecución en su máquina local

Para volver a adjuntar rápidamente a un proceso al que se adjuntó anteriormente, consulte [Volver a adjuntar a un proceso](#BKMK_reattach).

Para depurar un proceso en un equipo remoto, consulte [Adjuntar a un proceso en un equipo remoto.](#BKMK_Attach_to_a_process_on_a_remote_computer)

::: moniker range=">= vs-2019"
Para depurar un proceso de .NET Core en un contenedor de Docker de Linux, consulte [Adjuntar a un contenedor de Docker](#BKMK_Linux_Docker_Attach)de Linux .
::: moniker-end

**Para adjuntar a un proceso en el equipo local:**

1. En Visual Studio, seleccione **Depurar** > **adjuntar al proceso** (o presione **Ctrl**+**Alt**+**P**) para abrir el asociar **al proceso** cuadro de diálogo.

   **El tipo** de conexión debe establecerse en **Predeterminado**. **El destino** de conexión debe ser el nombre del equipo local.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. En la lista **Procesos disponibles,** busque y seleccione el proceso o los procesos a los que desea adjuntar.

   - Para seleccionar rápidamente un proceso, escriba su nombre o primera letra en el cuadro **Filtrar procesos.**

   - Si no conoce el nombre del proceso, examine la lista o vea Escenarios de [depuración comunes](#BKMK_Scenarios) para algunos nombres de proceso comunes.

   >[!TIP]
   >Los procesos pueden iniciarse y detenerse en segundo plano mientras el cuadro de diálogo **Adjuntar al proceso** está abierto, por lo que la lista de procesos en ejecución puede no estar siempre actualizada. Puede seleccionar **Actualizar** en cualquier momento para ver la lista actual.

3. En el campo **Asociar a,** asegúrese de que aparece el tipo de código que va a depurar. La configuración **predeterminada Automática** funciona para la mayoría de los tipos de aplicaciones.

   Para seleccionar tipos de código manualmente:
   1. Haga clic en **Seleccionar**.
   1. En el cuadro de diálogo Seleccionar tipo de **código,** seleccione **Depurar estos tipos**de código .
   1. Seleccione los tipos de código que desea depurar.
   1. Seleccione **Aceptar**.

4. Seleccione **Adjuntar**.

>[!NOTE]
>Puede adjuntarse a varias aplicaciones para la depuración, pero solo una aplicación está activa en el depurador a la vez. Puede establecer la aplicación activa en la barra de herramientas Ubicación de **depuración** de Visual Studio o en la ventana **Procesos.**

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>Adjuntar a un proceso en un equipo remoto

También puede seleccionar un equipo remoto en el cuadro de diálogo **Adjuntar al proceso,** ver una lista de los procesos disponibles que se ejecutan en ese equipo y adjuntar a uno o varios de los procesos para la depuración. El depurador remoto (*msvsmon.exe*) debe estar ejecutándose en el equipo remoto. Para obtener más información, consulte [Depuración remota](../debugger/remote-debugging.md).

Para obtener instrucciones más completas para depurar ASP.NET aplicaciones que se han implementado en IIS, vea [depuración remota ASP.NET en un equipo IIS remoto.](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)

**Para conectar a un proceso en ejecución en un equipo remoto:**

1. En Visual Studio, seleccione **Depurar** > **adjuntar al proceso** (o presione **Ctrl**+**Alt**+**P**) para abrir el asociar **al proceso** cuadro de diálogo.

2. **El tipo** de conexión debe ser **Predeterminado** para la mayoría de los casos. En el cuadro Destino de **conexión,** seleccione el equipo remoto mediante uno de los métodos siguientes:

   - Seleccione la flecha desplegable situada junto a **Destino de conexión**y seleccione el nombre del equipo en la lista desplegable.
   - Escriba el nombre del equipo en el cuadro Destino de **conexión** y pulse **Intro**.

     Compruebe que Visual Studio agrega el puerto necesario al nombre del equipo, que aparece en el formato: ** \<nombre de equipo remoto>:port**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Si no puede conectarse con el nombre del equipo remoto, intente `123.45.678.9:4022`usar la dirección IP y la dirección de puerto (por ejemplo, ). 4024 es el puerto predeterminado para el depurador remoto de Visual Studio 2019 x64. Para otras asignaciones de puertos de depurador remoto, vea Asignaciones de [puertos](remote-debugger-port-assignments.md)del depurador remoto .

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Si no puede conectarse con el nombre del equipo remoto, intente `123.45.678.9:4022`usar la dirección IP y la dirección de puerto (por ejemplo, ). 4022 es el puerto predeterminado para el depurador remoto de Visual Studio 2017 x64. Para otras asignaciones de puertos de depurador remoto, vea Asignaciones de [puertos](remote-debugger-port-assignments.md)del depurador remoto .

     ::: moniker-end

   - Seleccione el botón **Buscar** situado junto al cuadro **Destino de conexión** para abrir el cuadro de diálogo **Conexiones remotas.** El cuadro de diálogo **Conexiones remotas** muestra todos los dispositivos que se encuentran en la subred local o conectados directamente al equipo. Es posible que deba abrir el [puerto UDP 3702](../debugger/remote-debugger-port-assignments.md) en el servidor para detectar dispositivos remotos. Seleccione el equipo o dispositivo que desee y, a continuación, haga clic en **Seleccionar**.

   > [!NOTE]
   > La configuración Tipo de **conexión** persiste entre sesiones de depuración. La configuración **De destino** de conexión persiste entre sesiones de depuración solo si se produjo una conexión de depuración correcta con ese destino.

3. Haga clic en **Actualizar** para rellenar la lista **Procesos disponibles.**

    >[!TIP]
    >Los procesos pueden iniciarse y detenerse en segundo plano mientras el cuadro de diálogo **Adjuntar al proceso** está abierto, por lo que la lista de procesos en ejecución puede no estar siempre actualizada. Puede seleccionar **Actualizar** en cualquier momento para ver la lista actual.

4. En la lista **Procesos disponibles,** busque y seleccione el proceso o los procesos a los que desea adjuntar.

   - Para seleccionar rápidamente un proceso, escriba su nombre o primera letra en el cuadro **Filtrar procesos.**

   - Si no conoce el nombre del proceso, examine la lista o vea Escenarios de [depuración comunes](#BKMK_Scenarios) para algunos nombres de proceso comunes.

   - Para buscar procesos que se ejecutan en todas las cuentas de usuario, active la casilla **Mostrar procesos de todos los usuarios.**

     >[!NOTE]
     >Si intenta asociar a un proceso que pertenece a una cuenta de usuario que no es de confianza, aparecerá un cuadro de diálogo de confirmación con una advertencia de seguridad. Para obtener más información, consulte Advertencia de seguridad: Adjuntar a un proceso propiedad de un usuario que no es de [confianza puede ser peligroso. Si la siguiente información parece sospechosa o no está seguro, no se adjunte a este proceso.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)

5. En el campo **Asociar a,** asegúrese de que aparece el tipo de código que va a depurar. La configuración **predeterminada Automática** funciona para la mayoría de los tipos de aplicaciones.

   Para seleccionar tipos de código manualmente:
   1. Haga clic en **Seleccionar**.
   1. En el cuadro de diálogo Seleccionar tipo de **código,** seleccione **Depurar estos tipos**de código .
   1. Seleccione los tipos de código que desea depurar.
   1. Seleccione **Aceptar**.

6. Seleccione **Adjuntar**.

>[!NOTE]
>Puede adjuntarse a varias aplicaciones para la depuración, pero solo una aplicación está activa en el depurador a la vez. Puede establecer la aplicación activa en la barra de herramientas Ubicación de **depuración** de Visual Studio o en la ventana **Procesos.**

En algunos casos, al depurar en una sesión de Escritorio remoto (Servicios terminales), la lista **Procesos disponibles** no mostrará todos los procesos disponibles. Si ejecuta Visual Studio como un usuario que tiene una cuenta de usuario limitada, la lista **Procesos disponibles** no mostrará los procesos que se ejecutan en la sesión 0. La sesión 0 se utiliza para servicios y otros procesos de servidor, incluido *w3wp.exe*. Para resolver el problema, ejecute [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] con una cuenta de administrador o ejecute [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde la consola de servidor en lugar de una sesión de Terminal Services.

Si ninguna de estas dos soluciones es posible, existe una tercera opción que consiste en asociar al proceso mediante la ejecución de `vsjitdebugger.exe -p <ProcessId>` en la línea de comandos de Windows. Puede determinar el identificador de proceso mediante *tlist.exe*. Para obtener el archivo *tlist.exe*, descargue e instale las Herramientas de depuración para Windows, disponibles en  [Descargas de WDK y WinDbg](/windows-hardware/drivers/download-the-wdk).

::: moniker range=">= vs-2019"


## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>Adjuntar a un proceso de .NET Core que se ejecuta en Linux mediante SSH

Para obtener más información, consulte Depuración remota de [.NET Core que se ejecuta en Linux mediante SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a>Adjuntar a un proceso que se ejecuta en un contenedor de Docker de Linux

Puede asociar el depurador de Visual Studio a un proceso que se ejecuta en un contenedor de Docker de Linux .NET Core en el equipo local o remoto mediante el cuadro de diálogo **Asociar al proceso.**

> [!IMPORTANT]
> Para usar esta característica, debe instalar la carga de trabajo de desarrollo multiplataforma de .NET Core y tener acceso local al código fuente.

**Para adjuntar a un proceso en ejecución en un contenedor de Docker de Linux:**

1. En Visual Studio, seleccione **Depurar > Adjuntar al proceso (CTRL+ALT+P)** para abrir el cuadro de diálogo Asociar al **proceso.**

![Adjuntar al menú de proceso](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Establezca el Tipo de **conexión** en **Docker (contenedor Linux).**
3. Seleccione **Buscar...** para establecer el **destino de conexión** a través del cuadro de diálogo Seleccionar contenedor de **Docker.**

    Puede depurar un proceso de contenedor de Docker de forma local o remota.
    
    **Para depurar un proceso de contenedor de Docker localmente:**
    1. Establezca **el host de la CLI** de Docker en Local **Machine**.
    1. Seleccione un contenedor en ejecución al que adjuntar en la lista y pulse **Aceptar**.
    
    ![Seleccione Docker Container Menu](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. Para depurar un proceso de contenedor de Docker de forma remota:**
    
    > [!NOTE] 
    > Hay dos opciones para conectarse de forma remota a un proceso en ejecución en un contenedor de Docker. La primera opción, para usar SSH, es ideal si no tiene herramientas de Docker instaladas en el equipo local.  Si tiene herramientas de Docker instaladas localmente y tiene un demonio de Docker configurado para aceptar solicitudes remotas, pruebe la segunda opción mediante un demonio de Docker.

    1. ***Para conectarse a un equipo remoto a través de SSH:***
        1. Seleccione **Agregar...** para conectarse a un sistema remoto.<br/>
        ![Conéctese a un sistema remoto](../debugger/media/connect-remote-system.png "Conéctese a un sistema remoto")
        1. Seleccione un contenedor en ejecución al que conectar después de conectarse al SSH o al demonio correctamente y pulse **Aceptar**.

    
    1. ***Para establecer el destino en un contenedor remoto que ejecuta un proceso a través de un [demonio de Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)***
        1. Especifique la dirección del demonio (es decir, a través de TCP, IP, etc.) en **Host Docker (Opcional)** y haga clic en el vínculo de actualización.
        1. Seleccione un contenedor en ejecución al que adjuntar después de conectarse al demonio correctamente y pulse **Aceptar**.

4. Elija el proceso de contenedor correspondiente de la lista de **procesos disponibles** y seleccione **Adjuntar** para iniciar la depuración del proceso de contenedor de C- en Visual Studio!

    ![Completado Docker Attach Menu](../debugger/media/docker-attach-complete.png "Completado Linux Docker Attach Menu")
    

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a><a name="BKMK_Windows_Docker_Attach"></a>Adjuntar a un proceso que se ejecuta en un contenedor de Docker de Windows

Puede asociar el depurador de Visual Studio a un proceso que se ejecuta en un contenedor de Docker de Windows en el equipo local mediante el cuadro de diálogo **Asociar al proceso.**

> [!IMPORTANT]
> Para usar esta característica con un proceso de .NET Core, debe instalar la carga de trabajo de desarrollo multiplataforma de .NET Core y tener acceso local al código fuente.

**Para adjuntar a un proceso en ejecución en un contenedor de Docker de Windows:**

1. En Visual Studio, seleccione **Depurar > Adjuntar al proceso** (o **CTRL+ALT+P**) para abrir el cuadro de diálogo **Asociar al proceso.**

   ![Adjuntar al menú de proceso](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Establezca el Tipo de **conexión** en **Docker (contenedor de Windows).**
3. Seleccione **Buscar...** para establecer el **destino de conexión** mediante el cuadro de diálogo Seleccionar contenedor de **Docker.**

    > [!IMPORTANT]
    > El proceso de destino debe tener la misma arquitectura de procesador que el contenedor de Docker Windows en el que se ejecuta.
    
   Establecer el destino en un contenedor remoto a través de SSH no está disponible actualmente y solo se puede realizar mediante un demonio de Docker.
    
    ***Para establecer el destino en un contenedor remoto que ejecuta un proceso a través de un [demonio de Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)***
    1. Especifique la dirección del demonio (es decir, a través de TCP, IP, etc.) en **Host Docker (Opcional)** y haga clic en el vínculo de actualización. 

    1. Seleccione un contenedor en ejecución al que adjuntar después de conectarse al demonio correctamente y elija OK.
    
4. Elija el proceso de contenedor correspondiente de la lista de **procesos disponibles** y seleccione **Adjuntar** para iniciar la depuración del proceso de contenedor de C.

    ![Completado Docker Attach Menu](../debugger/media/docker-attach-complete-windows.png "Completado Windows Docker Attach Menu")
    

5.  Elija el proceso de contenedor correspondiente de la lista de procesos disponibles y elija **Attach** para iniciar la depuración del proceso de contenedor de C.


::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a>Volver a adjuntar a un proceso

Puede volver a adjuntar rápidamente a los procesos a los que se adjuntó anteriormente seleccionando **Depurar** > **volver a adjuntar al proceso** (**Mayúsculas**+**Alt**+**P**). Al elegir este comando, el depurador intentará asociarse inmediatamente a los últimos procesos a los que se asentaba al intentar primero hacer coincidir el identificador de proceso anterior y, si se produce un error, haciendo coincidir con el nombre del proceso anterior. Si no se encuentran coincidencias, o si varios procesos tienen el mismo nombre, se abrirá el cuadro de diálogo **Adjuntar al proceso** para que pueda seleccionar el proceso correcto.

> [!NOTE]
> El comando **Volver a adjuntar a proceso** está disponible a partir de Visual Studio 2017.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a>Escenarios comunes de depuración

Para ayudarle a determinar si desea usar **Adjuntar al proceso** y a qué proceso adjuntar, la tabla siguiente muestra algunos escenarios de depuración comunes, con vínculos a más instrucciones cuando estén disponibles. (La lista no es exhaustiva.)

Para algunos tipos de aplicaciones, como las aplicaciones de aplicación universal de Windows (UWP), no se adjunta directamente a un nombre de proceso, pero se usa la opción de menú **Depurar paquete** de aplicación instalado en Visual Studio en su lugar (consulte la tabla).

Para que el depurador se asocie al código escrito en C++, el código debe emitir `DebuggableAttribute`. Puede agregar este atributo automáticamente al código vinculando con la opción [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) del vinculador.

Para la depuración de scripts del lado cliente, la depuración de scripts debe estar habilitada en el explorador. Para depurar el script del lado cliente en Chrome, elija **JavaScript (Chrome)** o **JavaScript (Microsoft Edge - Chromium)** como tipo de código y, dependiendo `chrome.exe --remote-debugging-port=9222` del tipo de aplicación, es posible que deba cerrar todas las instancias de Chrome e iniciar el explorador en modo de depuración (tipo desde una línea de comandos). En versiones anteriores de Visual Studio, el depurador de scripts para Chrome era **Web kit.**

Para seleccionar rápidamente un proceso en ejecución al que adjuntar, en Visual Studio, escriba **Ctrl**+**Alt**+**P**y, a continuación, escriba la primera letra del nombre del proceso.

|Escenario|Método de depuración|Nombre del proceso|Notas y enlaces|
|-|-|-|-|
|Depuración remota ASP.NET 4 o 4.5 en un servidor IIS|Usar herramientas remotas y **Adjuntar al proceso**|*w3wp.exe*|Consulte [Depuración remota ASP.NET en un equipo IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Depuración remota ASP.NET Core en un servidor IIS|Usar herramientas remotas y **Adjuntar al proceso**|*w3wp.exe* o *dotnet.exe*|A partir de .NET Core 3, el proceso *w3wp.exe* se utiliza para el modelo de [hospedaje en la aplicación](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models)predeterminado. Para la implementación de aplicaciones, consulte Publicar en [IIS](/aspnet/core/host-and-deploy/iis/). Para obtener información más detallada, consulte [Depuración remota ASP.NET Core en un equipo IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach)|
|Depurar script del lado cliente en un servidor IIS local, para los tipos de aplicación compatibles |Usar **Adjuntar al proceso**|*chrome.exe*, *MicrosoftEdgeCP.exe*o *iexplore.exe*|La depuración de scripts debe estar habilitada. Para Chrome, también debe ejecutar Chrome `chrome.exe --remote-debugging-port=9222` en modo de depuración (tipo desde una línea de comandos) y seleccionar **JavaScript (Chrome)** en el campo **Adjuntar a.**|
|Depurar una aplicación de C, Visual Basic o C++ en el equipo local|Utilice la depuración estándar (**F5**) o **Adjuntar al proceso**|*\<nombredeaplicación>.exe*|En la mayoría de los escenarios, utilice la depuración estándar y no **Adjuntar al proceso**.|
|Depuración remota de una aplicación de escritorio de Windows|Herramientas remotas|N/D| Consulte [Depuración remota](../debugger/remote-debugging-csharp.md) de una aplicación de C o Visual Basic o [Depuración remota de una aplicación de C++](../debugger/remote-debugging-cpp.md)|
|Depurar .NET Core en Linux|Usar **Adjuntar al proceso**|*dotnet.exe*|Para usar SSH, consulte [Depuración remota de .NET Core que se ejecuta en Linux mediante SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md). |
|Depurar una aplicación ASP.NET en el equipo local después de iniciar la aplicación sin el depurador|Usar **Adjuntar al proceso**|*iiexpress.exe*|Esto puede ser útil para que la aplicación se cargue más rápido, como (por ejemplo) al generar perfiles. |
|Depurar otros tipos de aplicaciones compatibles en un proceso de servidor|Si el servidor es remoto, utilice herramientas remotas y **Adjuntar al proceso**|*chrome.exe*, *iexplore.exe*u otros procesos|Si es necesario, utilice el Monitor de recursos para ayudar a identificar el proceso. Vea [Depuración remota](../debugger/remote-debugging.md).|
|Depuración remota de una aplicación universal de Windows (UWP), OneCore, HoloLens o aplicación de IoT|Depurar paquete de aplicaciones instalado|N/D|Consulte [Depurar un paquete](debug-installed-app-package.md) de aplicación instalado en lugar de usar Adjuntar al **proceso**|
|Depurar una aplicación universal de Windows (UWP), OneCore, HoloLens o ioT aplicación que no se inició desde Visual Studio|Depurar paquete de aplicaciones instalado|N/D|Consulte [Depurar un paquete](debug-installed-app-package.md) de aplicación instalado en lugar de usar Adjuntar al **proceso**|

## <a name="use-debugger-features"></a>Usar características del depurador

Para usar las características completas del depurador de Visual Studio (como golpear puntos de interrupción) al asociara a un proceso, la aplicación debe coincidir exactamente con el origen local y los símbolos. Es decir, el depurador debe poder cargar los archivos de [símbolo (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)correctos. De forma predeterminada, esto requiere una compilación de depuración.

Para escenarios de depuración remota, debe tener el código fuente (o una copia del código fuente) ya abierto en Visual Studio. Los archivos binarios de la aplicación compilada en el equipo remoto deben provenir de la misma compilación que en el equipo local.

En algunos escenarios de depuración locales, puede depurar en Visual Studio sin acceso al origen si los archivos de símbolos correctos están presentes con la aplicación. De forma predeterminada, esto requiere una compilación de depuración. Para obtener más información, consulte Especificar archivos de [símbolo y de origen.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Solucionar problemas de errores de asociación
 Cuando el depurador se asocia a un proceso en ejecución, el proceso puede contener uno o varios tipos de código. Los tipos de código a los que se puede asociar el depurador se muestran y seleccionan en el cuadro de diálogo **Seleccionar tipo de código** .

 A veces, el depurador puede asociarse correctamente a un tipo de código, pero no a otro. Esto puede ocurrir cuando se intenta asociar el depurador a un proceso que está ejecutándose en un equipo remoto. Puede que el equipo remoto tenga instalados los componentes de depuración remota para algunos tipos de código, pero no para otros. También puede ocurrir al intentar asociar el depurador a dos o varios procesos para realizar una depuración directa de la base de datos. La depuración de SQL sólo admite la asociación a un único proceso.

 Si el depurador puede adjuntar a algunos tipos de código, pero no a todos, verá un mensaje que identifica qué tipos no se han podido adjuntar.

 Si el depurador se asocia correctamente a un tipo de código por lo menos, podrá reanudar la depuración del proceso. Sólo podrá depurar los tipos de código que se hayan asociado correctamente. El código no asociado en el proceso seguirá ejecutándose, pero no podrá establecer puntos de interrupción, ver datos ni realizar otras operaciones de depuración en ese código.

 Si desea obtener información más específica sobre por qué el depurador no pudo asociarse a un tipo de código, intente volver a adjuntar solo a ese tipo de código.

 **Para obtener información específica sobre la causa por la que no se ha asociado correctamente un tipo de código:**

1. Desasocie el proceso. En el menú **Depurar** , seleccione **Separar todo**.

1. Vuelva a adjuntar al proceso, seleccionando solo el tipo de código que no se pudo adjuntar.

    1. En el cuadro de diálogo **Asociar al proceso**, seleccione el proceso en la lista **Procesos disponibles**.

    2. Elija **Seleccionar**.

    3. En el cuadro de diálogo **Seleccionar tipo de código** , seleccione **Depurar estos tipos de código** y el tipo de código que no se haya asociado correctamente. Anule la selección de los otros tipos de código.

    4. Seleccione **Aceptar**.

    5. En el cuadro de diálogo **Adjuntar al proceso,** seleccione **Adjuntar**.

    Esta vez se producirá un error en todo el proceso de asociación y aparecerá un mensaje de error específico.

## <a name="see-also"></a>Consulte también

- [Depuración de varios procesos](../debugger/debug-multiple-processes.md)
- [Deshabilitar al depurador Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Depuración remota](../debugger/remote-debugging.md)
