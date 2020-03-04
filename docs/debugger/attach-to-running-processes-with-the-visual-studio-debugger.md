---
title: Asociar a procesos en ejecución con el depurador | Microsoft Docs
ms.custom: seodec18
ms.date: 04/08/2019
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
ms.openlocfilehash: f2f00cde0c2ea3fad79c0f5ef75f3c33ad7afc22
ms.sourcegitcommit: c98e0ccf236765b44e47095ee52836cb012e3854
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2020
ms.locfileid: "78257194"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Asociar con procesos en ejecución con el depurador de Visual Studio
Puede asociar el depurador de Visual Studio a un proceso en ejecución en un equipo local o remoto. Una vez que se esté ejecutando el proceso, seleccione **Depurar** > **adjuntar al proceso** o presione **Ctrl**+**Alt**+**P** en Visual Studio y use el cuadro de diálogo **asociar al proceso** para asociar el depurador al proceso.

Puede usar **asociar al proceso** para depurar aplicaciones en ejecución en equipos locales o remotos, depurar varios procesos simultáneamente, depurar aplicaciones que no se crearon en Visual Studio o depurar cualquier aplicación que no se haya iniciado desde Visual Studio con el depurador asociado. Por ejemplo, si está ejecutando una aplicación sin el depurador y se ha alcanzado una excepción, puede asociar el depurador al proceso que ejecuta la aplicación y comenzar la depuración.

> [!TIP]
> ¿No está seguro de si desea usar **asociar al proceso** para el escenario de depuración? Vea [escenarios comunes de depuración](#BKMK_Scenarios).

## <a name="BKMK_Attach_to_a_running_process"></a>Asociar a un proceso en ejecución en el equipo local

Para volver a asociar rápidamente a un proceso al que ha adjuntado anteriormente, vea volver [a asociar a un proceso](#BKMK_reattach).

Para depurar un proceso en un equipo remoto, vea [asociar a un proceso en un equipo remoto](#BKMK_Attach_to_a_process_on_a_remote_computer).

::: moniker range=">= vs-2019"
Para depurar un proceso de .NET Core en un contenedor de Docker de Linux, consulte [conexión a un contenedor de Docker de Linux](#BKMK_Docker_Attach).
::: moniker-end

**Para asociar a un proceso en el equipo local:**

1. En Visual Studio, seleccione **Depurar** > **asociar al proceso** (o presione **Ctrl**+**Alt**+**P**) para abrir el cuadro de diálogo **asociar al proceso** .

   El **tipo de conexión** debe establecerse en el **valor predeterminado**. El destino de la **conexión** debe ser el nombre de la máquina local.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. En la lista **procesos disponibles** , busque y seleccione el proceso o los procesos a los que desea asociar.

   - Para seleccionar rápidamente un proceso, escriba su nombre o su primera letra en el cuadro **filtrar procesos** .

   - Si no conoce el nombre del proceso, desplácese por la lista o vea [escenarios de depuración comunes](#BKMK_Scenarios) para algunos nombres de proceso comunes.

   >[!TIP]
   >Los procesos se pueden iniciar y detener en segundo plano mientras el cuadro de diálogo **asociar al proceso** está abierto, por lo que es posible que la lista de procesos en ejecución no esté siempre actualizada. Puede seleccionar **Actualizar** en cualquier momento para ver la lista actual.

3. En el campo **asociar a** , asegúrese de que aparece el tipo de código que va a depurar. La configuración **automática** predeterminada funciona en la mayoría de los tipos de aplicaciones.

   Para seleccionar tipos de código manualmente:
   1. Haga clic en **Seleccionar**.
   1. En el cuadro de diálogo **Seleccionar tipo de código** , seleccione **depurar estos tipos de código**.
   1. Seleccione los tipos de código que desea depurar.
   1. Seleccione **Aceptar**.

4. Seleccione **Adjuntar**.

>[!NOTE]
>Puede asociarse a varias aplicaciones para la depuración, pero solo una aplicación está activa en el depurador a la vez. Puede establecer la aplicación activa en la barra de herramientas de **Ubicación de depuración** de Visual Studio o en la ventana **procesos** .

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Asociar a un proceso en un equipo remoto

También puede seleccionar un equipo remoto en el cuadro de diálogo **asociar al proceso** , ver una lista de los procesos disponibles que se ejecutan en ese equipo y asociarlos a uno o varios procesos para la depuración. El depurador remoto (*msvsmon. exe*) debe ejecutarse en el equipo remoto. Para obtener más información, vea [depuración remota](../debugger/remote-debugging.md).

Para obtener instrucciones más completas sobre cómo depurar aplicaciones ASP.NET que se han implementado en IIS, consulte [depuración remota de ASP.net en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Para asociar a un proceso en ejecución en un equipo remoto:**

1. En Visual Studio, seleccione **Depurar** > **asociar al proceso** (o presione **Ctrl**+**Alt**+**P**) para abrir el cuadro de diálogo **asociar al proceso** .

2. El **tipo de conexión** debe ser **predeterminado** en la mayoría de los casos. En el cuadro destino de la **conexión** , seleccione el equipo remoto mediante uno de los métodos siguientes:

   - Seleccione la flecha desplegable situada junto a **destino de conexión**y seleccione el nombre del equipo en la lista desplegable.
   - Escriba el nombre del equipo en el cuadro destino de la **conexión** y presione **entrar**.

     Compruebe que Visual Studio agrega el puerto necesario al nombre del equipo, que aparece en el formato: **\<nombre de equipo remoto >:p ordenar**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Si no puede conectarse con el nombre del equipo remoto, pruebe a usar la dirección IP y el puerto (por ejemplo, `123.45.678.9:4022`). 4024 es el puerto predeterminado para el depurador remoto de Visual Studio 2019 x64. Para otras asignaciones de puerto del Depurador remoto, vea [asignaciones de puerto del Depurador remoto](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Si no puede conectarse con el nombre del equipo remoto, pruebe a usar la dirección IP y el puerto (por ejemplo, `123.45.678.9:4022`). 4022 es el puerto predeterminado para el depurador remoto de Visual Studio 2017 x64. Para otras asignaciones de puerto del Depurador remoto, vea [asignaciones de puerto del Depurador remoto](remote-debugger-port-assignments.md).

     ::: moniker-end

   - Seleccione el botón **Buscar** situado junto al cuadro **destino de conexión** para abrir el cuadro de diálogo **conexiones remotas** . El cuadro de diálogo **conexiones remotas** muestra todos los dispositivos que están en la subred local o conectados directamente al equipo. Es posible que tenga que [abrir el puerto UDP 3702](../debugger/remote-debugger-port-assignments.md) en el servidor para detectar dispositivos remotos. Seleccione el equipo o dispositivo que desee y, a continuación, haga clic en **seleccionar**.

   > [!NOTE]
   > La configuración del **tipo de conexión** se conserva entre las sesiones de depuración. La configuración de **destino de conexión** solo se conserva entre las sesiones de depuración si se ha producido una conexión de depuración correcta con ese destino.

3. Haga clic en **Actualizar** para rellenar la lista **procesos disponibles** .

    >[!TIP]
    >Los procesos se pueden iniciar y detener en segundo plano mientras el cuadro de diálogo **asociar al proceso** está abierto, por lo que es posible que la lista de procesos en ejecución no esté siempre actualizada. Puede seleccionar **Actualizar** en cualquier momento para ver la lista actual.

4. En la lista **procesos disponibles** , busque y seleccione el proceso o los procesos a los que desea asociar.

   - Para seleccionar rápidamente un proceso, escriba su nombre o su primera letra en el cuadro **filtrar procesos** .

   - Si no conoce el nombre del proceso, desplácese por la lista o vea [escenarios de depuración comunes](#BKMK_Scenarios) para algunos nombres de proceso comunes.

   - Para buscar procesos que se ejecutan en todas las cuentas de usuario, active la casilla **Mostrar los procesos de todos los usuarios** .

     >[!NOTE]
     >Si intenta asociar a un proceso que pertenece a una cuenta de usuario que no es de confianza, aparecerá un cuadro de diálogo de confirmación con una advertencia de seguridad. Para obtener más información, consulte [advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario de confianza puede ser peligroso. Si la información siguiente le resulta sospechosa o no está seguro de su procedencia, no la adjunte a este proceso](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. En el campo **asociar a** , asegúrese de que aparece el tipo de código que va a depurar. La configuración **automática** predeterminada funciona en la mayoría de los tipos de aplicaciones.

   Para seleccionar tipos de código manualmente:
   1. Haga clic en **Seleccionar**.
   1. En el cuadro de diálogo **Seleccionar tipo de código** , seleccione **depurar estos tipos de código**.
   1. Seleccione los tipos de código que desea depurar.
   1. Seleccione **Aceptar**.

6. Seleccione **Adjuntar**.

>[!NOTE]
>Puede asociarse a varias aplicaciones para la depuración, pero solo una aplicación está activa en el depurador a la vez. Puede establecer la aplicación activa en la barra de herramientas de **Ubicación de depuración** de Visual Studio o en la ventana **procesos** .

En algunos casos, al depurar en una sesión de Escritorio remoto (Terminal Services), la lista **procesos disponibles** no mostrará todos los procesos disponibles. Si está ejecutando Visual Studio como usuario que tiene una cuenta de usuario limitada, la lista **procesos disponibles** no mostrará los procesos que se están ejecutando en la sesión 0. La sesión 0 se utiliza para los servicios y otros procesos de servidor, incluido *w3wp. exe*. Para resolver el problema, ejecute [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] con una cuenta de administrador o ejecute [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde la consola de servidor en lugar de una sesión de Terminal Services.

Si ninguna de estas dos soluciones es posible, existe una tercera opción que consiste en asociar al proceso mediante la ejecución de `vsjitdebugger.exe -p <ProcessId>` en la línea de comandos de Windows. Puede determinar el identificador de proceso mediante *Tlist. exe*. Para obtener el archivo *tlist.exe*, descargue e instale las Herramientas de depuración para Windows, disponibles en  [Descargas de WDK y WinDbg](/windows-hardware/drivers/download-the-wdk).

::: moniker range=">= vs-2019"

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>Asociación a un proceso de .NET Core que se ejecuta en Linux mediante SSH

Para obtener más información, consulte [depuración remota de .net Core que se ejecuta en Linux con ssh](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

## <a name="BKMK_Docker_Attach"></a>Asociación a un proceso que se ejecuta en un contenedor de Docker de Linux

Puede adjuntar el depurador de Visual Studio a un proceso que se ejecuta en un contenedor de Docker de Linux .NET Core en el equipo local o remoto mediante el cuadro de diálogo **asociar al proceso** .

> [!IMPORTANT]
> Para usar esta característica, debe instalar la carga de trabajo de desarrollo multiplataforma de .NET Core y tener acceso local al código fuente.

**Para asociar a un proceso en ejecución en un contenedor de Docker de Linux:**

1. En Visual Studio, seleccione **Depurar > asociar al proceso (Ctrl + Alt + P)** para abrir el cuadro de diálogo **asociar al proceso** .

![Menú asociar al proceso](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Establezca el **tipo de conexión** en **Docker (contenedor de Linux)** .
3. Seleccione **Buscar...** para establecer el **destino** de la conexión mediante el cuadro de diálogo **seleccionar contenedor de Docker** .

    Puede depurar un proceso de contenedor de Docker de forma local o remota.
    
    **Para depurar un proceso de contenedor de Docker localmente:**
    1. Establezca el host de la **CLI de Docker** en la **máquina local**.
    1. Seleccione un contenedor en ejecución al que adjuntar de la lista y haga clic en **Aceptar**.
    
    ![Menú Seleccionar contenedor de Docker](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. para depurar un proceso de contenedor de Docker de forma remota:**
    
    > [!NOTE] 
    > Hay dos opciones para conectarse de forma remota a un proceso en ejecución en un contenedor de Docker. La primera opción, para usar SSH, es ideal si no tiene herramientas de Docker instaladas en el equipo local.  Si tiene herramientas de Docker instaladas localmente y tiene un demonio de Docker que está configurado para aceptar solicitudes remotas, pruebe la segunda opción mediante un demonio de Docker.

    1. ***Para conectarse a un equipo remoto a través de SSH:***
        1. Seleccione **Agregar...** para conectarse a un sistema remoto.<br/>
        ![Conectarse a un sistema remoto](../debugger/media/connect-remote-system.png "Conectarse a un sistema remoto")
        1. Seleccione un contenedor en ejecución al que adjuntar después de conectarse correctamente al SSH o el demonio y presione **Aceptar**.

    
    1. ***Para establecer el destino en un contenedor remoto que ejecuta un proceso a través de un [demonio de Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)***
        1. Especifique la dirección del demonio (es decir, a través de TCP, IP, etc.) en el **host de Docker (opcional)** y haga clic en el vínculo actualizar.
        1. Seleccione un contenedor en ejecución al que adjuntar después de conectarse al demonio correctamente y presione **Aceptar**.

4. Elija el proceso de contenedor correspondiente en la lista de **procesos disponibles** y seleccione **asociar** para iniciar la C# depuración del proceso de contenedor en Visual Studio.

    ![Menú de adjuntar Docker completado](../debugger/media/docker-attach-complete.png "Menú de adjuntar Docker completado")


::: moniker-end

## <a name="BKMK_reattach"></a>Volver a asociar a un proceso

Puede volver a asociar rápidamente a los procesos a los que se adjuntó previamente eligiendo **Depurar** > volver **a asociar al proceso** (**MAYÚS**+**Alt**+**P**). Cuando se elige este comando, el depurador intentará conectarse de inmediato a los últimos procesos a los que se haya adjuntado intentando buscar una coincidencia con el identificador de proceso anterior y, si se produce un error, al coincidir con el nombre del proceso anterior. Si no se encuentran coincidencias, o si varios procesos tienen el mismo nombre, se abrirá el cuadro de diálogo **asociar al proceso** para que pueda seleccionar el proceso correcto.

> [!NOTE]
> El comando volver **a asociar al proceso** está disponible a partir de Visual Studio 2017.

## <a name="BKMK_Scenarios"></a>Escenarios comunes de depuración

Para ayudarle a determinar si se debe usar **asociar al proceso** y a qué proceso se debe asociar, en la tabla siguiente se muestran algunos escenarios comunes de depuración, con vínculos a más instrucciones cuando estén disponibles. (La lista no es exhaustiva).

En el caso de algunos tipos de aplicaciones, como las aplicaciones universales de Windows (UWP), no se adjuntan directamente a un nombre de proceso, pero en su lugar se usa la opción de menú **depurar paquete de aplicaciones instalado** de Visual Studio (vea la tabla).

Para que el depurador se asocie al código escrito en C++, el código debe emitir `DebuggableAttribute`. Puede agregar este atributo automáticamente al código vinculando con la opción [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) del vinculador.

Para la depuración de scripts del lado cliente, la depuración de scripts debe estar habilitada en el explorador. Para depurar el script de cliente en Chrome, elija **Web kit** como el tipo de código y, en función del tipo de aplicación, puede que tenga que cerrar todas las instancias de Chrome e iniciar el explorador en modo de depuración (escriba `chrome.exe --remote-debugging-port=9222` desde una línea de comandos).

Para seleccionar rápidamente un proceso en ejecución al que adjuntar, en Visual Studio, escriba **Ctrl**+**Alt**+**P**y, a continuación, escriba la primera letra del nombre del proceso.

|Escenario|Debug (método)|Nombre del proceso|Notas y vínculos|
|-|-|-|-|
|Depuración remota ASP.NET 4 o 4,5 en un servidor IIS|Usar herramientas remotas y **asociar al proceso**|*w3wp.exe*|Consulte [depuración remota ASP.net en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|ASP.NET Core de depuración remota en un servidor IIS|Usar herramientas remotas y **asociar al proceso**|*dotnet. exe* o *AppName. exe*|Para la implementación de aplicaciones, vea [publicar en IIS](https://docs.asp.net/en/latest/publishing/iis.html). Para la depuración, vea [ASP.net Core de depuración remota en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Depurar el script del lado cliente en un servidor IIS local, para los tipos de aplicaciones compatibles |Usar **asociar al proceso**|*Chrome. exe*, *MicrosoftEdgeCP. exe*o *iexplore. exe*|La depuración de scripts debe estar habilitada. Para Chrome, también debe ejecutar Chrome en modo de depuración y seleccionar **código WebKit** en el campo **adjuntar a** .|
|Depuración de una C#aplicación C++ , Visual Basic o en el equipo local|Usar depuración estándar (**F5**) o **asociar al proceso**|*\<nombre_de_la_aplicación>.exe*|En la mayoría de los escenarios, se usa la depuración estándar y no **se asocia al proceso**.|
|Depuración remota de una aplicación de escritorio de Windows|Herramientas remotas|N/D| Vea [depuración C# remota a o Visual Basic aplicación](../debugger/remote-debugging-csharp.md) o [depuración remota de una C++ aplicación](../debugger/remote-debugging-cpp.md)|
|Depuración de .NET Core en Linux|Usar **asociar al proceso**|*dotnet.exe*|Para usar SSH, consulte [depuración remota .net Core que se ejecuta en Linux con ssh](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md). |
|Depuración de una aplicación ASP.NET en el equipo local después de iniciar la aplicación sin el depurador|Usar **asociar al proceso**|*iiexpress.exe*|Esto puede resultar útil para agilizar la carga de la aplicación, como (por ejemplo,) al generar perfiles. |
|Depurar otros tipos de aplicaciones compatibles en un proceso de servidor|Si el servidor es remoto, usa herramientas remotas y **asociar al proceso** .|*Chrome. exe*, *iexplore. exe*u otros procesos|Si es necesario, utilice Monitor de recursos para ayudar a identificar el proceso. Vea [Depuración remota](../debugger/remote-debugging.md).|
|Depuración remota de una aplicación universal de Windows (UWP), OneCore, HoloLens o IoT|Depurar paquete de aplicaciones instalado|N/D|Consulte [depuración de un paquete de aplicaciones instalado](debug-installed-app-package.md) en lugar de usar **asociar al proceso** .|
|Depuración de una aplicación universal de Windows (UWP), OneCore, HoloLens o IoT que no se inició desde Visual Studio|Depurar paquete de aplicaciones instalado|N/D|Consulte [depuración de un paquete de aplicaciones instalado](debug-installed-app-package.md) en lugar de usar **asociar al proceso** .|

## <a name="use-debugger-features"></a>Usar las características del depurador

Para usar todas las características del depurador de Visual Studio (como golpear los puntos de interrupción) al asociarse a un proceso, la aplicación debe coincidir exactamente con el código fuente y los símbolos locales. Es decir, el depurador debe ser capaz de cargar los [archivos de símbolos (. pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)correctos. De forma predeterminada, esto requiere una compilación de depuración.

En escenarios de depuración remota, debe tener el código fuente (o una copia del código fuente) ya abierto en Visual Studio. Los archivos binarios de la aplicación compilada en el equipo remoto deben provienen de la misma compilación que en el equipo local.

En algunos escenarios de depuración local, puede depurar en Visual Studio sin acceso al origen si los archivos de símbolos correctos están presentes en la aplicación. De forma predeterminada, esto requiere una compilación de depuración. Para obtener más información, vea [especificar archivos de símbolos y de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="BKMK_Troubleshoot_attach_errors"></a> Solucionar problemas de errores de asociación
 Cuando el depurador se asocia a un proceso en ejecución, el proceso puede contener uno o varios tipos de código. Los tipos de código a los que se puede asociar el depurador se muestran y seleccionan en el cuadro de diálogo **Seleccionar tipo de código** .

 A veces, el depurador puede asociarse correctamente a un tipo de código, pero no a otro. Esto puede ocurrir cuando se intenta asociar el depurador a un proceso que está ejecutándose en un equipo remoto. Puede que el equipo remoto tenga instalados los componentes de depuración remota para algunos tipos de código, pero no para otros. También puede ocurrir al intentar asociar el depurador a dos o varios procesos para realizar una depuración directa de la base de datos. La depuración de SQL sólo admite la asociación a un único proceso.

 Si el depurador puede asociarse a algunos tipos de código, pero no a todos, verá un mensaje que identifica los tipos que no se pudieron adjuntar.

 Si el depurador se asocia correctamente a un tipo de código por lo menos, podrá reanudar la depuración del proceso. Sólo podrá depurar los tipos de código que se hayan asociado correctamente. El código no adjunto del proceso seguirá ejecutándose, pero no podrá establecer puntos de interrupción, ver datos ni realizar otras operaciones de depuración en ese código.

 Si desea obtener información más específica sobre el motivo por el que el depurador no se ha asociado a un tipo de código, intente volver a adjuntar solo a ese tipo de código.

 **Para obtener información específica sobre la causa por la que no se ha asociado correctamente un tipo de código:**

1. Desasocie el proceso. En el menú **depurar** , seleccione **Desasociar todo**.

1. Vuelva a adjuntar al proceso, seleccionando solo el tipo de código que no se pudo adjuntar.

    1. En el cuadro de diálogo **Asociar al proceso**, seleccione el proceso en la lista **Procesos disponibles**.

    2. Elija **Seleccionar**.

    3. En el cuadro de diálogo **Seleccionar tipo de código** , seleccione **Depurar estos tipos de código** y el tipo de código que no se haya asociado correctamente. Anule la selección de los otros tipos de código.

    4. Seleccione **Aceptar**.

    5. En el cuadro de diálogo **asociar al proceso** , seleccione **adjuntar**.

    Esta vez se producirá un error en todo el proceso de asociación y aparecerá un mensaje de error específico.

## <a name="see-also"></a>Consulte también

- [Depuración de varios procesos](../debugger/debug-multiple-processes.md)
- [Depuración Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Depuración remota](../debugger/remote-debugging.md)
