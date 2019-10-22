---
title: Adjuntar a procesos en ejecución con el depurador | Microsoft Docs
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
ms.openlocfilehash: 15b9921514f76d788430c1eda66603e9fc446361
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67891023"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Crear asociaciones con procesos en ejecución con el depurador de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede asociar el depurador de Visual Studio a un proceso en ejecución en un equipo local o remoto. Después de que el proceso se está ejecutando, haga clic en **depurar / asociar al proceso** (o presione **CTRL + ALT + P**) para abrir el **asociar al proceso** cuadro de diálogo.

Puede usar esta capacidad para depurar aplicaciones que se ejecutan en un equipo local o remoto, depurar varios procesos simultáneamente o depurar una aplicación que no se creó en Visual Studio. A menudo resulta útil cuando desea depurar una aplicación, pero (por cualquier motivo) no inició la aplicación desde Visual Studio con el depurador adjunto. Por ejemplo, si está ejecutando la aplicación sin el depurador y encuentra una excepción, a continuación, podría adjuntar al proceso de ejecución de la aplicación para empezar a depurar.

> [!TIP]
> ¿No está seguro de que si se debe usar **asociar al proceso** para su escenario de depuración? Consulte [comunes en escenarios de depuración](#BKMK_Scenarios). Si desea depurar aplicaciones de ASP.NET que se han implementado en IIS, consulte [Remote Debugging ASP.NET en un equipo IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

## <a name="BKMK_Attach_to_a_running_process"></a> Adjuntar a un proceso en ejecución en el equipo local
 Para asociar a un proceso, debe conocer el nombre del proceso (consulte [comunes en escenarios de depuración](#BKMK_Scenarios) para algunos nombres comunes de proceso).

1. En Visual Studio, seleccione **depurar / asociar al proceso** (o presione **CTRL + ALT + P**).

2. En el cuadro de diálogo **Asociar al proceso** , seleccione el programa que desea asociar en la lista **Procesos disponibles** .

     Para seleccionar rápidamente el proceso que desea, escriba la primera letra del nombre del proceso. Si no conoce el nombre del proceso, consulte [comunes en escenarios de depuración](#BKMK_Scenarios).

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     Si el proceso se ejecuta con una cuenta de usuario diferente, active la casilla **Mostrar los procesos de todos los usuarios** .

3. En el cuadro **Asociar a** , asegúrese de que aparece el tipo de código que quiere depurar. El valor predeterminado **Automático** intenta determinar qué tipo de código desea depurar. Para establecer el tipo de código manualmente, haga lo siguiente:

    1. En el cuadro de diálogo **Asociar a** , haga clic en **Seleccionar**.

    2. En el cuadro de diálogo **Seleccionar tipo de código** , haga clic en **Depurar estos tipos de código** y seleccione los tipos que va a depurar.

    3. Haga clic en **OK**.

4. Haga clic en **Adjuntar**.

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Asociar a un proceso en un equipo remoto
 Para asociar a un proceso, debe conocer el nombre del proceso (consulte [comunes en escenarios de depuración](#BKMK_Scenarios) para algunos nombres comunes de proceso). Para obtener más detalles para las aplicaciones ASP.NET que se han implementado en IIS, consulte [Remote Debugging ASP.NET en un equipo IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). En el caso de las demás aplicaciones, encontrará el nombre del proceso en el Administrador de tareas.

 En el cuadro de diálogo **Asociar al proceso** , puede seleccionar otro equipo configurado para la depuración remota. Para obtener más información, consulte [depuración remota](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c). Cuando se ha seleccionado un equipo remoto, se puede consultar una lista con los procesos disponibles que se están ejecutando en dicho equipo y establecer una asociación con uno o varios procesos para llevar a cabo la depuración.

 **Para seleccionar un equipo remoto:**

1. En Visual Studio, seleccione **depurar / asociar al proceso** (o presione **CTRL + ALT + P**).

2. En el cuadro **Asociar al proceso** , seleccione el tipo de conexión adecuado en la lista **Transporte** . **Valor predeterminado** es la configuración correcta en la mayoría de los casos.

   La configuración de **Transporte** se conserva entre las sesiones de depuración.

3. Utilice el cuadro de lista **Calificador** para elegir el nombre del equipo remoto mediante uno de los métodos siguientes:

   1. Escriba el nombre en el cuadro de lista **Calificador** .

      > [!NOTE]
      > Si, en pasos posteriores, no se puede conectar con el nombre del equipo remoto, use la dirección IP. (El número de puerto puede aparecer automáticamente después de seleccionar el proceso. También puede escribir manualmente. En la ilustración siguiente, 4020 es el puerto predeterminado para el depurador remoto.)

   2. Haga clic en la flecha desplegable del cuadro de lista **Calificador** y seleccione el nombre del equipo en la lista desplegable.

   3. Haga clic en el **buscar** situado junto a la **calificador** lista para abrir el **Seleccionar conexión del depurador remoto** cuadro de diálogo. El cuadro **Seleccionar conexión del depurador remoto** muestra todos los dispositivos que se encuentran en su subred local, y cualquier dispositivo conectado directamente al equipo mediante un cable Ethernet. Haga clic en el equipo o el dispositivo que desee y, a continuación, haga clic en **Seleccionar**.

      La configuración de **Calificador** sólo se conserva entre las sesiones de depuración si se produce una conexión de depuración correcta con ese calificador.

4. Haga clic en **Actualizar**.

     La lista **Procesos disponibles** aparecerá automáticamente al abrir el cuadro de diálogo **Procesos** . Los procesos se pueden iniciar y detener en segundo plano mientras el cuadro de diálogo está abierto. Sin embargo, el contenido no siempre estará actualizado. Es posible actualizar la lista en cualquier momento y ver los procesos en curso haciendo clic en **Actualizar**.

5. En el cuadro de diálogo **Asociar al proceso** , seleccione el programa que desea asociar en la lista **Procesos disponibles** .

    Si el proceso se ejecuta con una cuenta de usuario diferente, active la casilla **Mostrar los procesos de todos los usuarios** .

6. Haga clic en **Adjuntar**.

## <a name="additional-info"></a>Información adicional

Puede tener asociados varios programas mientras realiza la depuración, pero sólo un programa estará activo en el depurador en cada momento. Puede establecer el programa activo en la barra de herramientas **Ubicación de depuración** o en la ventana **Procesos** . Para obtener más información, consulte [Cómo Establecer el programa actual](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).

Si intenta asociar a un proceso que pertenece a una cuenta de usuario que no es de confianza, aparecerá un cuadro de diálogo de confirmación con una advertencia de seguridad. Para obtener más información, consulte [advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario que no sea de confianza puede ser peligroso. Si la información siguiente parece sospechosa o no está seguro, no la adjunte a este proceso](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015).

En algunos casos, al depurar en una sesión de Escritorio remoto (Terminal Services), en la lista **Procesos disponibles** no aparecerán todos los procesos disponibles. Si se ejecuta Visual Studio como usuario que tiene una cuenta de usuario limitada, la lista **Procesos disponibles** no mostrará los procesos que se estén ejecutando en la sesión 0, la cual se usa para los servicios y otros procesos de servidor, incluido w3wp.exe. Para resolver el problema, ejecute [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] con una cuenta de administrador o ejecute [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] desde la consola de servidor en lugar de una sesión de Terminal Services. Si ninguna de estas dos soluciones es posible, existe una tercera opción que consiste en asociar al proceso mediante la ejecución de `vsjitdebugger.exe -p` *ProcessId* en la línea de comandos de Windows. Puede determinar el identificador de proceso mediante tlist.exe. Para obtener el archivo tlist.exe, descargue e instale las Herramientas de depuración para Windows, disponibles en  [Descargas de WDK y WinDbg](http://go.microsoft.com/fwlink/?LinkId=168279).

## <a name="BKMK_Scenarios"></a> Escenarios comunes de depuración

Para ayudarle a identificar si se debe usar **asociar al proceso** y qué proceso de asociación con, aquí se muestran algunos escenarios comunes de depuración (la lista no es exhaustiva). Cuando se disponga de más instrucciones, se proporcionan vínculos.

Para algunos tipos de aplicación (por ejemplo, las aplicaciones de Windows Store), no conecte directamente a un nombre de proceso, pero usar el **depurar paquete de aplicaciones instalado** opción de menú en su lugar (consulte la tabla).

> [!NOTE]
> Para obtener información sobre la depuración básica en Visual Studio, consulte [introducción con el depurador](../debugger/getting-started-with-the-debugger.md).

|Escenario|Depurar (método)|Nombre del proceso|Notas y vínculos|
|-|-|-|-|
|Depurar una aplicación administrada o nativa en el equipo local|Use asociar al proceso o [depuración estándar](../debugger/getting-started-with-the-debugger.md)|*appname*.exe|Para obtener acceso rápidamente el cuadro de diálogo, utilice **CTRL + ALT + P** y, a continuación, escriba la primera letra del nombre del proceso.|
|Depurar aplicaciones ASP.NET en el equipo local después de iniciar la aplicación sin el depurador|Use asociar al proceso|iiexpress.exe|Esto puede resultar útil para realizar la aplicación carga más rápida, por ejemplo, (por ejemplo) al generar perfiles. |
|Depuración remota de ASP.NET 4 o 4.5 en un servidor IIS|Utilizar las herramientas remotas y asociar al proceso|w3wp.exe|Consulte [Remote Debugging ASP.NET en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Depuración remota de ASP.NET Core en un servidor IIS|Utilizar las herramientas remotas y asociar al proceso|DNX.exe|Implementación de aplicaciones, consulte [publicar en IIS](https://docs.asp.net/en/latest/publishing/iis.html). Para la depuración, vea [Remote Debugging ASP.NET en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Depurar otros tipos de aplicaciones compatibles en un proceso de servidor|Usar herramientas remotas (si el servidor es remoto) y asociar al proceso|Iexplore.exe u otros procesos|Si es necesario, utilice el Administrador de tareas para ayudar a identificar el proceso. Consulte [depuración remota](../debugger/remote-debugging.md) y las secciones posteriores de este tema.|
|Depuración remota de una aplicación de escritorio de Windows|F5 y herramientas remotas|N/D| Consulte [depuración remota](../debugger/remote-debugging.md)|
|Depuración remota de una aplicación Universal de Windows (UWP), OneCore, HoloLens o IoT|Depurar paquete de aplicaciones instalado|N/D|Use **depurar / otros destinos de depuración / depurar paquete de la aplicación instalado** en lugar de **asociar al proceso**|
|Depurar una aplicación Universal de Windows (UWP), OneCore, HoloLens o IoT que no se inició desde Visual Studio|Depurar paquete de aplicaciones instalado|N/D|Use **depurar / otros destinos de depuración / depurar paquete de la aplicación instalado** en lugar de **asociar al proceso**|

> [!WARNING]
> Para asociar a una aplicación universal de Windows escrita en JavaScript, primero debe habilitar la depuración de la aplicación. Vea [Attach the debugger](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) en el Centro de desarrollo de Windows.

> [!NOTE]
> Para que el depurador se asocie al código escrito en C++, el código debe emitir `DebuggableAttribute`. Puede agregar este atributo automáticamente al código vinculando con la opción [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) del vinculador.

## <a name="what-debugger-features-can-i-use"></a>¿Qué características del depurador se debe usar?

Para usar todas las características del depurador de Visual Studio (por ejemplo, para alcanzar los puntos de interrupción) cuando se asocia a un proceso, el archivo ejecutable debe coincidir exactamente con el origen local y símbolos (es decir, el depurador debe ser capaz de cargar el valor correcto [(.pbd) archivos de símbolos ](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). De forma predeterminada, esto requiere una compilación de depuración.

Para escenarios de depuración remotos, debe tener el código fuente (o una copia del código fuente) está abierto en Visual Studio. Los archivos binarios de la aplicación compilada en el equipo remoto deben proceder de la misma compilación como en el equipo local.

En algunos escenarios de depuración locales, puede depurar en Visual Studio sin acceso al origen si los archivos de símbolos correctos están presentes con la aplicación (de forma predeterminada, esto requiere una compilación de depuración). Para obtener más información, consulte [especificar archivos de código fuente y símbolos](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="BKMK_Troubleshoot_attach_errors"></a> Solucionar problemas de errores de asociación
 Cuando el depurador se asocia a un proceso en ejecución, el proceso puede contener uno o varios tipos de código. Los tipos de código a los que se puede asociar el depurador se muestran y seleccionan en el cuadro de diálogo **Seleccionar tipo de código** .

 A veces, el depurador puede asociarse correctamente a un tipo de código, pero no a otro. Esto puede ocurrir cuando se intenta asociar el depurador a un proceso que está ejecutándose en un equipo remoto. Puede que el equipo remoto tenga instalados los componentes de depuración remota para algunos tipos de código, pero no para otros. También puede ocurrir al intentar asociar el depurador a dos o varios procesos para realizar una depuración directa de la base de datos. La depuración de SQL sólo admite la asociación a un único proceso.

 Si el depurador logra asociarse a algunos tipos de código, pero no a todos, aparecerá un mensaje en el que se identifican los tipos sin asociar:

 Si el depurador se asocia correctamente a un tipo de código por lo menos, podrá reanudar la depuración del proceso. Sólo podrá depurar los tipos de código que se hayan asociado correctamente. El mensaje de ejemplo anterior indica que el tipo de código de script no se ha asociado correctamente. Por lo tanto, no podrá depurar código de script dentro del proceso. El código de script del proceso seguirá ejecutándose, pero no se podrán establecer puntos de interrupción, ni se podrán ver los datos, ni se podrá realizar ninguna otra operación de depuración en el script.

 Si desea obtener información más detallada sobre el motivo por el que el depurador no se ha asociado correctamente a un tipo de código, puede intentar asociarlo de nuevo con ese tipo de código exclusivamente.

 **Para obtener información específica acerca de por qué un tipo de código no se pudo conectar**

1. Desasocie el proceso. En el menú **Depurar** , haga clic en **Desasociar todo**.

2. Vuelva a asociar el proceso, pero seleccionando un único tipo de código.

   1. En el cuadro de diálogo **Asociar al proceso** , seleccione el proceso en la lista **Procesos disponibles** .

   2. Haga clic en **Seleccionar**.

   3. En el cuadro de diálogo **Seleccionar tipo de código** , seleccione **Depurar estos tipos de código** y el tipo de código que no se haya asociado correctamente. Borre cualquier otro código.

   4. Haga clic en **OK**. El cuadro de diálogo **Seleccionar tipo de código** se cierra.

   5. En el cuadro de diálogo **Asociar al proceso** , haga clic en **Asociar**.

      Esta vez se producirá un error en todo el proceso de asociación y aparecerá un mensaje de error específico.

## <a name="see-also"></a>Vea también
 [Depurar varios procesos](../debugger/debug-multiple-processes.md) [depuración Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md) [depuración remota](../debugger/remote-debugging.md)
