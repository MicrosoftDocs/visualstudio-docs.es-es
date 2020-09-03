---
title: Asociar a procesos en ejecución con el depurador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
- C++
- CSharp
- FSharp
- VB
- c++
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 62
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf4d63d7d00e91daa2564992f801896075f73aab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918940"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Crear asociaciones con procesos en ejecución con el depurador de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede asociar el depurador de Visual Studio a un proceso en ejecución en un equipo local o remoto. Una vez que el proceso se esté ejecutando, haga clic en **depurar/asociar al proceso** (o presione **Ctrl + Alt + P**) para abrir el cuadro de diálogo **asociar al proceso** .

Puede usar esta funcionalidad para depurar aplicaciones que se ejecutan en un equipo local o remoto, depurar varios procesos simultáneamente o depurar una aplicación que no se creó en Visual Studio. A menudo resulta útil si desea depurar una aplicación, pero (por cualquier motivo) no inició la aplicación desde Visual Studio con el depurador asociado. Por ejemplo, si está ejecutando la aplicación sin el depurador y se encuentra una excepción, puede asociarse al proceso que ejecuta la aplicación para comenzar la depuración.

> [!TIP]
> ¿No está seguro de si necesita usar **asociar al proceso** para el escenario de depuración? Vea [Escenarios comunes de depuración](#BKMK_Scenarios). Si desea depurar aplicaciones de ASP.NET que se han implementado en IIS, consulte [depuración remota de ASP.net en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

## <a name="attach-to-a-running-process-on-the-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Asociar a un proceso en ejecución en el equipo local
 Para asociar a un proceso, debe conocer el nombre del proceso (vea [escenarios de depuración comunes](#BKMK_Scenarios) para algunos nombres de procesos comunes).

1. En Visual Studio, seleccione **depurar/asociar al proceso** (o presione **Ctrl + Alt + P**).

2. En el cuadro de diálogo **Asociar al proceso** , seleccione el programa que desea asociar en la lista **Procesos disponibles** .

     Para seleccionar rápidamente el proceso que desea, escriba la primera letra del nombre del proceso. Si no conoce el nombre del proceso, consulte [escenarios comunes de depuración](#BKMK_Scenarios).

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     Si el proceso se ejecuta con una cuenta de usuario diferente, active la casilla **Mostrar los procesos de todos los usuarios** .

3. En el cuadro **Asociar a** , asegúrese de que aparece el tipo de código que quiere depurar. El valor predeterminado **Automático** intenta determinar qué tipo de código desea depurar. Para establecer el tipo de código manualmente, haga lo siguiente:

    1. En el cuadro de diálogo **Asociar a** , haga clic en **Seleccionar**.

    2. En el cuadro de diálogo **Seleccionar tipo de código** , haga clic en **Depurar estos tipos de código** y seleccione los tipos que va a depurar.

    3. Haga clic en **OK**.

4. Haga clic en **Adjuntar**.

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Asociar a un proceso en un equipo remoto
 Para asociar a un proceso, debe conocer el nombre del proceso (vea [escenarios de depuración comunes](#BKMK_Scenarios) para algunos nombres de procesos comunes). Para obtener instrucciones más completas sobre las aplicaciones ASP.NET que se han implementado en IIS, consulte [depuración remota de ASP.net en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). En el caso de las demás aplicaciones, encontrará el nombre del proceso en el Administrador de tareas.

 En el cuadro de diálogo **Asociar al proceso** , puede seleccionar otro equipo configurado para la depuración remota. Para obtener más información, vea [Depuración remota](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c). Cuando se ha seleccionado un equipo remoto, se puede consultar una lista con los procesos disponibles que se están ejecutando en dicho equipo y establecer una asociación con uno o varios procesos para llevar a cabo la depuración.

 **Para seleccionar un equipo remoto:**

1. En Visual Studio, seleccione **depurar/asociar al proceso** (o presione **Ctrl + Alt + P**).

2. En el cuadro **Asociar al proceso** , seleccione el tipo de conexión adecuado en la lista **Transporte** . **Valor predeterminado** es la configuración correcta en la mayoría de los casos.

   La configuración de **Transporte** se conserva entre las sesiones de depuración.

3. Utilice el cuadro de lista **Calificador** para elegir el nombre del equipo remoto mediante uno de los métodos siguientes:

   1. Escriba el nombre en el cuadro de lista **Calificador** .

      > [!NOTE]
      > Si, en pasos posteriores, no se puede conectar con el nombre del equipo remoto, use la dirección IP. (El número de puerto puede aparecer automáticamente después de seleccionar el proceso. También puede escribirlo manualmente. En la ilustración siguiente, 4020 es el puerto predeterminado para el depurador remoto).

   2. Haga clic en la flecha desplegable del cuadro de lista **Calificador** y seleccione el nombre del equipo en la lista desplegable.

   3. Haga clic en el botón **Buscar** situado junto a la lista **calificador** para abrir el cuadro de diálogo **seleccionar conexión del Depurador remoto** . El cuadro **Seleccionar conexión del depurador remoto** muestra todos los dispositivos que se encuentran en su subred local, y cualquier dispositivo conectado directamente al equipo mediante un cable Ethernet. Haga clic en el equipo o el dispositivo que desee y, a continuación, haga clic en **Seleccionar**.

      La configuración de **Calificador** sólo se conserva entre las sesiones de depuración si se produce una conexión de depuración correcta con ese calificador.

4. Haga clic en **Actualizar**.

     La lista **Procesos disponibles** aparecerá automáticamente al abrir el cuadro de diálogo **Procesos** . Los procesos se pueden iniciar y detener en segundo plano mientras el cuadro de diálogo está abierto. Sin embargo, el contenido no siempre estará actualizado. Es posible actualizar la lista en cualquier momento y ver los procesos en curso haciendo clic en **Actualizar**.

5. En el cuadro de diálogo **Asociar al proceso** , seleccione el programa que desea asociar en la lista **Procesos disponibles** .

    Si el proceso se ejecuta con una cuenta de usuario diferente, active la casilla **Mostrar los procesos de todos los usuarios** .

6. Haga clic en **Adjuntar**.

## <a name="additional-info"></a>Información adicional

Puede tener asociados varios programas mientras realiza la depuración, pero sólo un programa estará activo en el depurador en cada momento. Puede establecer el programa activo en la barra de herramientas **Ubicación de depuración** o en la ventana **Procesos** . Para obtener más información, vea [Cómo: Establecer el programa actual](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).

Si intenta asociar a un proceso que pertenece a una cuenta de usuario que no es de confianza, aparecerá un cuadro de diálogo de confirmación con una advertencia de seguridad. Para obtener más información, vea [Advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario que no sea de confianza puede ser peligroso. Si la información siguiente le resulta sospechosa o no está seguro de su procedencia, no la adjunte a este proceso](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015).

En algunos casos, al depurar en una sesión de Escritorio remoto (Terminal Services), en la lista **Procesos disponibles** no aparecerán todos los procesos disponibles. Si se ejecuta Visual Studio como usuario que tiene una cuenta de usuario limitada, la lista **Procesos disponibles** no mostrará los procesos que se estén ejecutando en la sesión 0, la cual se usa para los servicios y otros procesos de servidor, incluido w3wp.exe. Para resolver el problema, ejecute [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] con una cuenta de administrador o ejecute [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] desde la consola de servidor en lugar de una sesión de Terminal Services. Si ninguna de estas dos soluciones es posible, existe una tercera opción que consiste en asociar al proceso mediante la ejecución de `vsjitdebugger.exe -p` *ProcessId* en la línea de comandos de Windows. Puede determinar el identificador de proceso mediante tlist.exe. Para obtener tlist.exe, descargue e instale las herramientas de depuración para Windows, disponibles en  [descargas de WDK y WinDbg](/windows-hardware/drivers/dashboard/).

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> Escenarios comunes de depuración

Para ayudarle a identificar si necesita usar **asociar al proceso** y qué proceso asociar a, aquí se muestran algunos escenarios comunes de depuración (la lista no es exhaustiva). Si hay más instrucciones disponibles, se proporcionan vínculos.

Para algunos tipos de aplicaciones (como las aplicaciones de la tienda Windows), no se adjunta directamente a un nombre de proceso, pero en su lugar use la opción de menú **depurar paquete de aplicaciones instalado** (vea la tabla).

> [!NOTE]
> Para obtener información sobre la depuración básica en Visual Studio, consulte [Introducción al depurador](../debugger/getting-started-with-the-debugger.md).

|Escenario|Debug (método)|Nombre del proceso|Notas y vínculos|
|-|-|-|-|
|Depurar una aplicación administrada o nativa en el equipo local|Usar asociar al proceso o [depuración estándar](../debugger/getting-started-with-the-debugger.md)|*appname*. exe|Para obtener acceso rápidamente al cuadro de diálogo, use **Ctrl + Alt + P** y, a continuación, escriba la primera letra del nombre del proceso.|
|Depurar aplicaciones de ASP.NET en el equipo local después de iniciar la aplicación sin el depurador|Usar asociar al proceso|iiexpress.exe|Puede resultar útil para agilizar la carga de la aplicación, como (por ejemplo,) al generar perfiles. |
|Depuración remota de ASP.NET 4 o 4.5 en un servidor IIS|Usar herramientas remotas y asociar al proceso|w3wp.exe|Consulte [depuración remota ASP.net en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Depuración remota de ASP.NET Core en un servidor de IIS|Usar herramientas remotas y asociar al proceso|dnx.exe|Para la implementación de aplicaciones, vea [Publicación en IIS](https://docs.asp.net/en/latest/publishing/iis.html). Para la depuración, consulte [depuración remota ASP.net en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Depuración de otros tipos de aplicaciones compatibles en un proceso de servidor|Usar herramientas remotas (si el servidor es remoto) y asociar al proceso|iexplore.exe u otros procesos|Si es necesario, use el administrador de tareas para ayudar a identificar el proceso. Vea la sección [depuración remota](../debugger/remote-debugging.md) y versiones posteriores de este tema.|
|Depuración remota de una aplicación de escritorio de Windows|Herramientas remotas y F5|N/D| Vea [depuración remota](../debugger/remote-debugging.md)|
|Depuración remota de una aplicación universal de Windows (UWP), OneCore, HoloLens o IoT|Depurar paquete de aplicaciones instalado|N/D|Usar depurar **/otros destinos de depuración/depurar paquete de aplicaciones instalado** en lugar de **asociar al proceso**|
|Depuración de una aplicación Windows universal (UWP), OneCore, HoloLens o IoT que no se inició desde Visual Studio|Depurar paquete de aplicaciones instalado|N/D|Usar depurar **/otros destinos de depuración/depurar paquete de aplicaciones instalado** en lugar de **asociar al proceso**|

> [!WARNING]
> Para asociar a una aplicación universal de Windows escrita en JavaScript, primero debe habilitar la depuración de la aplicación. Vea [Attach the debugger](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) en el Centro de desarrollo de Windows.

> [!NOTE]
> Para que el depurador se asocie al código escrito en C++, el código debe emitir `DebuggableAttribute`. Puede agregar este atributo automáticamente al código vinculando con la opción [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) del vinculador.

## <a name="what-debugger-features-can-i-use"></a>¿Qué características del depurador puedo usar?

Para usar todas las características del depurador de Visual Studio (como los puntos de interrupción) al asociar a un proceso, el ejecutable debe coincidir exactamente con el código fuente y los símbolos locales (es decir, el depurador debe poder cargar los archivos de símbolos correctos [(. PBD)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). De forma predeterminada, esto requiere una compilación de depuración.

En escenarios de depuración remota, debe tener el código fuente (o una copia del código fuente) ya abierto en Visual Studio. Los archivos binarios de la aplicación compilada en el equipo remoto deben provenir de la misma compilación que en el equipo local.

En algunos escenarios de depuración local, puede depurar en Visual Studio sin acceso al origen si los archivos de símbolos correctos están presentes en la aplicación (de forma predeterminada, esto requiere una compilación de depuración). Para obtener más información, vea [especificar archivos de símbolos y de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Solucionar problemas de errores de asociación
 Cuando el depurador se asocia a un proceso en ejecución, el proceso puede contener uno o varios tipos de código. Los tipos de código a los que se puede asociar el depurador se muestran y seleccionan en el cuadro de diálogo **Seleccionar tipo de código** .

 A veces, el depurador puede asociarse correctamente a un tipo de código, pero no a otro. Esto puede ocurrir cuando se intenta asociar el depurador a un proceso que está ejecutándose en un equipo remoto. Puede que el equipo remoto tenga instalados los componentes de depuración remota para algunos tipos de código, pero no para otros. También puede ocurrir al intentar asociar el depurador a dos o varios procesos para realizar una depuración directa de la base de datos. La depuración de SQL sólo admite la asociación a un único proceso.

 Si el depurador logra asociarse a algunos tipos de código, pero no a todos, aparecerá un mensaje en el que se identifican los tipos sin asociar:

 Si el depurador se asocia correctamente a un tipo de código por lo menos, podrá reanudar la depuración del proceso. Sólo podrá depurar los tipos de código que se hayan asociado correctamente. El mensaje de ejemplo anterior indica que el tipo de código de script no se ha asociado correctamente. Por lo tanto, no podrá depurar código de script dentro del proceso. El código de script del proceso seguirá ejecutándose, pero no se podrán establecer puntos de interrupción, ni se podrán ver los datos, ni se podrá realizar ninguna otra operación de depuración en el script.

 Si desea obtener información más detallada sobre el motivo por el que el depurador no se ha asociado correctamente a un tipo de código, puede intentar asociarlo de nuevo con ese tipo de código exclusivamente.

 **Para obtener información específica sobre por qué no se pudo asociar un tipo de código**

1. Desasocie el proceso. En el menú **Depurar** , haga clic en **Desasociar todo**.

2. Vuelva a asociar el proceso, pero seleccionando un único tipo de código.

   1. En el cuadro de diálogo **asociar al proceso** , seleccione el proceso en la lista **procesos disponibles** .

   2. Haga clic en **Seleccionar**.

   3. En el cuadro de diálogo **Seleccionar tipo de código** , seleccione **Depurar estos tipos de código** y el tipo de código que no se haya asociado correctamente. Borre cualquier otro código.

   4. Haga clic en **OK**. El cuadro de diálogo **Seleccionar tipo de código** se cierra.

   5. En el cuadro de diálogo **Asociar al proceso** , haga clic en **Asociar**.

      Esta vez se producirá un error en todo el proceso de asociación y aparecerá un mensaje de error específico.

## <a name="see-also"></a>Consulte también
 Depurar [varios procesos](../debugger/debug-multiple-processes.md) depuración [remota](../debugger/remote-debugging.md) [Just-in-Time](../debugger/just-in-time-debugging-in-visual-studio.md)
