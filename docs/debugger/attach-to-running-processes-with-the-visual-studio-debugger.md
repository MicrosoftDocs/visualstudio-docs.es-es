---
title: Adjuntar a procesos en ejecución con el depurador de Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 06/20/2018
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdd83cb8b2d20d3e3abcacbb69d50e1a68831ca4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843267"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Asociar con procesos en ejecución con el depurador de Visual Studio
Puede asociar el depurador de Visual Studio a un proceso en ejecución en un equipo local o remoto. Una vez que se ejecuta el proceso, seleccione **depurar** > **asociar al proceso** o presione **Ctrl**+**Alt** + **P** en Visual Studio y usan el **asociar al proceso** cuadro de diálogo para asociar el depurador al proceso.

Puede usar **asociar al proceso** para depurar aplicaciones en ejecución en equipos locales o remotos, depurar varios procesos simultáneamente, depurar aplicaciones que no se crearon en Visual Studio o depurar cualquier aplicación que no se inició desde Visual Studio con el depurador asociado. Por ejemplo, si está ejecutando una aplicación sin el depurador y encuentra una excepción, a continuación, puede asociar al depurador al proceso que ejecuta la aplicación y comenzar la depuración.

Para obtener información sobre la depuración básica en Visual Studio, consulte [introducción con el depurador](../debugger/getting-started-with-the-debugger.md).

> [!TIP]
> ¿No está seguro de si se debe usar **asociar al proceso** para su escenario de depuración? Consulte [comunes en escenarios de depuración](#BKMK_Scenarios). 

##  <a name="BKMK_Attach_to_a_running_process"></a> Adjuntar a un proceso en ejecución en el equipo local  

Para volver a asociar rápidamente a un proceso que ha adjuntado a previamente, vea [volver a adjuntar a un proceso](#BKMK_reattach). 

Para depurar un proceso en un equipo remoto, consulte [asociar a un proceso en un equipo remoto](#BKMK_Attach_to_a_process_on_a_remote_computer).

**Para adjuntar a un proceso en el equipo local:**  

1. En Visual Studio, seleccione **depurar** > **asociar al proceso** (o presione **Ctrl**+**Alt** + **P**) para abrir el **asociar al proceso** cuadro de diálogo.
  
   **Tipo de conexión** debe establecerse en **predeterminado**. **Destino de la conexión** debe ser el nombre del equipo local. 
  
   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process") 
  
2. En el **procesos disponibles** lista, busque y seleccione el proceso o procesos que desea asociar a.  

   - Para seleccionar rápidamente un proceso, escriba su nombre o la primera letra de la **filtrar procesos** cuadro. 
  
   - Si no conoce el nombre del proceso, examine la lista, o vea [comunes en escenarios de depuración](#BKMK_Scenarios) para algunos nombres de proceso común. 
  
   >[!TIP]
   >Los procesos pueden iniciar y detener en segundo plano mientras el **asociar al proceso** cuadro de diálogo está abierto, por lo que la lista de procesos en ejecución puede no estar siempre actualizada. Puede seleccionar **actualizar** en cualquier momento para ver la lista actual. 
  
3. En el **adjuntar a** campo, asegúrese de que se muestra el tipo de código que se va a depurar. El valor predeterminado **automática** establecimiento funciona para la mayoría de los tipos de aplicación. 
  
   Para seleccionar manualmente los tipos de código:
   1. Haga clic en **Seleccionar**. 
   1. En el **Seleccionar tipo de código** cuadro de diálogo, seleccione **depurar estos tipos de código**.
   1. Seleccione los tipos de código que desea depurar.
   1. Seleccione **Aceptar**.
  
4. Seleccione **adjuntar**.
  
>[!NOTE]
>Pueden asociarse a varias aplicaciones para la depuración, pero solo una aplicación está activa en el depurador a la vez. Puede establecer la aplicación activa en Visual Studio **ubicación de depuración** barra de herramientas o **procesos** ventana.  

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Asociar a un proceso en un equipo remoto  

También puede seleccionar un equipo remoto en el **asociar al proceso** cuadro de diálogo, ver una lista de procesos disponibles que se ejecutan en ese equipo y asociar a uno o varios de los procesos para la depuración. El depurador remoto (*msvsmon.exe*) debe ejecutarse en el equipo remoto. Para obtener más información, consulte [depuración remota](../debugger/remote-debugging.md). 

Para obtener instrucciones más completas para depurar aplicaciones de ASP.NET que se han implementado en IIS, consulte [depuración ASP.NET en un equipo remoto de IIS remota](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Para adjuntar a un proceso en ejecución en un equipo remoto:**  

1. En Visual Studio, seleccione **depurar** > **asociar al proceso** (o presione **Ctrl**+**Alt** + **P**) para abrir el **asociar al proceso** cuadro de diálogo.
  
2. **Tipo de conexión** debe ser **predeterminado** para la mayoría de los casos. En el **destino de la conexión** , seleccione el equipo remoto, utilizando uno de los métodos siguientes:

   - Seleccione la flecha desplegable situada junto a **destino de la conexión**y seleccione el nombre del equipo en la lista desplegable.  
   - Escriba el nombre del equipo en el **destino de la conexión** cuadro.
      
     > [!NOTE]
     > Si no se puede conectar con el nombre del equipo remoto, pruebe a utilizar la dirección IP y dirección de puerto (por ejemplo, `123.45.678.9:4022`). 4022 es el puerto predeterminado para el depurador remoto de Visual Studio 2017 x64. Para otras asignaciones de puerto del depurador remoto, consulte [las asignaciones de puerto del depurador remoto](remote-debugger-port-assignments.md).  
      
   - Seleccione el **buscar** situado junto a la **destino de la conexión** cuadro para abrir el **conexiones remotas** cuadro de diálogo. El **conexiones remotas** cuadro de diálogo muestra todos los dispositivos que están en la subred local o conectado directamente al equipo. Es posible que deba [abrir el puerto UDP 3702](../debugger/remote-debugger-port-assignments.md) en el servidor para detectar dispositivos remotos. Seleccione el equipo o dispositivo que desee y, a continuación, haga clic en **seleccione**. 
  
   > [!NOTE]
   > El **tipo de conexión** configuración se conserva entre sesiones de depuración. El **destino de la conexión** configuración se conserva entre sesiones de depuración solo si se ha producido una conexión de depuración correcta con ese destino.

3. Haga clic en **actualizar** para rellenar el **procesos disponibles** lista.
     
    >[!TIP]
    >Los procesos pueden iniciar y detener en segundo plano mientras el **asociar al proceso** cuadro de diálogo está abierto, por lo que la lista de procesos en ejecución puede no estar siempre actualizada. Puede seleccionar **actualizar** en cualquier momento para ver la lista actual. 
     
4. En el **procesos disponibles** lista, busque y seleccione el proceso o procesos que desea asociar a.  

   - Para seleccionar rápidamente un proceso, escriba su nombre o la primera letra de la **filtrar procesos** cuadro. 
  
   - Si no conoce el nombre del proceso, examine la lista, o vea [comunes en escenarios de depuración](#BKMK_Scenarios) para algunos nombres de proceso común. 
  
   - Para buscar procesos que se ejecutan en todas las cuentas de usuario, seleccione el **mostrar los procesos de todos los usuarios** casilla de verificación.
      
     >[!NOTE]
     >Si intenta asociar a un proceso que pertenece a una cuenta de usuario que no es de confianza, aparecerá un cuadro de diálogo de confirmación con una advertencia de seguridad. Para obtener más información, consulte [advertencia de seguridad: adjuntar a un proceso que pertenezca a un usuario de confianza puede ser peligroso. Si la información siguiente parece sospechosa o no está seguro, no la adjunte a este proceso](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).  
      
5. En el **adjuntar a** campo, asegúrese de que se muestra el tipo de código que se va a depurar. El valor predeterminado **automática** establecimiento funciona para la mayoría de los tipos de aplicación. 
  
   Para seleccionar manualmente los tipos de código:
   1. Haga clic en **Seleccionar**. 
   1. En el **Seleccionar tipo de código** cuadro de diálogo, seleccione **depurar estos tipos de código**.
   1. Seleccione los tipos de código que desea depurar.
   1. Seleccione **Aceptar**.
  
6. Seleccione **adjuntar**.
  
>[!NOTE]
>Pueden asociarse a varias aplicaciones para la depuración, pero solo una aplicación está activa en el depurador a la vez. Puede establecer la aplicación activa en Visual Studio **ubicación de depuración** barra de herramientas o **procesos** ventana.  

En algunos casos, al depurar en una sesión de escritorio remoto (Terminal Services), el **procesos disponibles** lista no mostrará todos los procesos disponibles. Si está ejecutando Visual Studio como un usuario que tenga una cuenta de usuario limitada, el **procesos disponibles** lista no mostrará los procesos que se ejecutan en la sesión 0, que se usa para los servicios y otros procesos del servidor, incluidos *w3wp.exe*. Para resolver el problema, ejecute [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] con una cuenta de administrador o ejecute [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde la consola de servidor en lugar de una sesión de Terminal Services. 

Si ninguna de estas dos soluciones es posible, una tercera opción consiste en asociar al proceso mediante la ejecución de `vsjitdebugger.exe -p <ProcessId>` desde la línea de comandos de Windows. Puede determinar el identificador de proceso mediante *tlist.exe*. Para obtener *tlist.exe*, descargue e instale las herramientas de depuración para Windows, disponible en [descargas de WDK y WinDbg](/windows-hardware/drivers/download-the-wdk).

## <a name="BKMK_reattach"></a> Volver a adjuntar a un proceso

Puede reasociar rápidamente a los procesos que anteriormente se incluían en eligiendo **depurar** > **reasociar al proceso** (**MAYÚS** + **Alt**+**P**). Cuando se elige este comando, el depurador intentará inmediatamente a la última asociar proceso asociado al primer intentando coincidir con el identificador de proceso anterior y, a continuación, si se produce un error, haciendo coincidir el nombre del proceso anterior. Si se encuentra ninguna coincidencia, o si hay varios procesos con el mismo nombre, el **asociar al proceso** se abrirá el cuadro de diálogo para que pueda seleccionar el proceso correcto.

> [!NOTE]
> El **reasociar al proceso** command es nuevo en Visual Studio 2017.

## <a name="BKMK_Scenarios"></a> Escenarios comunes de depuración

Para ayudarle a determinar si se debe usar **asociar al proceso** y qué proceso de asociación con, la tabla siguiente muestran algunos escenarios comunes de depuración, con vínculos a instrucciones más donde estén disponibles. (La lista no es exhaustiva). 

Para algunos tipos de aplicación, como las aplicaciones de la aplicación Universal de Windows (UWP), no conecte directamente a un nombre de proceso, pero usar el **depurar paquete de aplicaciones instalado** opción de menú en Visual Studio en su lugar (consulte la tabla).

Para que el depurador se asocie al código escrito en C++, el código debe emitir `DebuggableAttribute`. Puede agregar este atributo automáticamente al código vinculando con la opción [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) del vinculador.

Para la depuración de scripts del lado cliente, la depuración de scripts debe habilitarse en el explorador. Para la depuración de script de cliente en Chrome, elija **Webkit** como el tipo de código y según el tipo de aplicación, es posible que deba iniciar el explorador en modo de depuración (tipo `chrome.exe --remote-debugging-port=9222` desde una línea de comandos).

Para seleccionar rápidamente un proceso en ejecución para adjuntar a, en Visual Studio, escriba **Ctrl**+**Alt**+**P**y, a continuación, escriba la primera letra de la nombre del proceso.

|Escenario|Depurar (método)|Nombre del proceso|Notas y vínculos|
|-|-|-|-|
|Depuración remota de ASP.NET 4 o 4.5 en un servidor IIS|Utilizar las herramientas remotas y **asociar al proceso**|*w3wp.exe*|Consulte [ASP.NET en un equipo remoto de IIS de la depuración remota](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Depuración remota de ASP.NET Core en un servidor IIS|Utilizar las herramientas remotas y **asociar al proceso**|*dotnet.exe*|Implementación de aplicaciones, consulte [publicar en IIS](https://docs.asp.net/en/latest/publishing/iis.html). Para la depuración, vea [remoto depuración ASP.NET Core en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Depurar script de cliente en un servidor IIS local (solo tipos de aplicación compatible)|Use **asociar al proceso**|*Chrome.exe*, *MicrosoftEdgeCP.exe*, o *iexplore.exe*|Debe estar habilitada la depuración de scripts. Para Chrome, también debe ejecutar Chrome en modo de depuración y seleccione **código Webkit** en el **adjuntar a** campo.|
|Depurar una aplicación de C#, Visual Basic o C++ en el equipo local|Usar [depuración estándar](../debugger/getting-started-with-the-debugger.md) o **asociar al proceso**|*\<NombreAplicación > .exe*|En la mayoría de los escenarios, use la depuración estándar y no **asociar al proceso**.|
|Depuración remota de una aplicación de escritorio de Windows|Herramientas remotas|N/D| Consulte [remoto depurar una aplicación de C# o Visual Basic](../debugger/remote-debugging-csharp.md) o [depuración remota de una aplicación de C++](../debugger/remote-debugging-cpp.md)|
|Depurar aplicaciones ASP.NET en el equipo local después de iniciar la aplicación sin el depurador|Use **asociar al proceso**|*iiexpress.exe*|Esto puede resultar útil para realizar la aplicación carga más rápida, por ejemplo, (por ejemplo) al generar perfiles. |
|Depurar otros tipos de aplicaciones compatibles en un proceso de servidor|Usar herramientas remotas (si el servidor es remoto) y **asociar al proceso**|*Chrome.exe*, *iexplore.exe*, u otros procesos|Si es necesario, utilice al Monitor de recursos para ayudar a identificar el proceso. Consulte [depuración remota](../debugger/remote-debugging.md).|
|Depuración remota de una aplicación de la aplicación Universal de Windows (UWP), OneCore, HoloLens o IoT|Depurar paquete de aplicaciones instalado|N/D|Consulte [depurar un paquete de aplicación instalados](debug-installed-app-package.md) en lugar de usar **asociar al proceso**|
|Depurar una aplicación de IoT, OneCore, HoloLens o aplicación Universal de Windows (UWP) que no se inició desde Visual Studio|Depurar paquete de aplicaciones instalado|N/D|Consulte [depurar un paquete de aplicación instalados](debug-installed-app-package.md) en lugar de usar **asociar al proceso**|  
  
## <a name="use-debugger-features"></a>Usar las características del depurador

Para usar todas las características del depurador de Visual Studio (por ejemplo, para alcanzar los puntos de interrupción) cuando se asocia a un proceso, la aplicación debe coincidir exactamente con el origen local y símbolos (es decir, el depurador debe ser capaz de cargar el valor correcto [(.pbd) archivossímbolos](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). De forma predeterminada, esto requiere una compilación de depuración.

Para escenarios de depuración remotos, debe tener el código fuente (o una copia del código fuente) está abierto en Visual Studio. Los archivos binarios de la aplicación compilada en el equipo remoto deben proceder de la misma compilación como en el equipo local.

En algunos escenarios de depuración locales, puede depurar en Visual Studio sin acceso al origen si los archivos de símbolos correctos están presentes con la aplicación (de forma predeterminada, esto requiere una compilación de depuración). Para obtener más información, consulte [especificar archivos de código fuente y símbolos](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  
##  <a name="BKMK_Troubleshoot_attach_errors"></a> Solución de problemas de errores de asociación  
 Cuando el depurador se asocia a un proceso en ejecución, el proceso puede contener uno o varios tipos de código. Los tipos de código a los que se puede asociar el depurador se muestran y seleccionan en el cuadro de diálogo **Seleccionar tipo de código** .  
  
 A veces, el depurador puede asociarse correctamente a un tipo de código, pero no a otro. Esto puede ocurrir cuando se intenta asociar el depurador a un proceso que está ejecutándose en un equipo remoto. Puede que el equipo remoto tenga instalados los componentes de depuración remota para algunos tipos de código, pero no para otros. También puede ocurrir al intentar asociar el depurador a dos o varios procesos para realizar una depuración directa de la base de datos. La depuración de SQL sólo admite la asociación a un único proceso.  
  
 Si el depurador puede asociarse a algunos, pero no para todos los tipos de código, verá un mensaje que identifica los tipos no se pudo conectar.  
  
 Si el depurador se asocia correctamente a un tipo de código por lo menos, podrá reanudar la depuración del proceso. Sólo podrá depurar los tipos de código que se hayan asociado correctamente. El código no adjunta en el proceso seguirá ejecutándose, pero no podrá establecer puntos de interrupción, ver los datos o realizar otras operaciones de depuración de ese código.  
  
 Si desea obtener información más detallada sobre el motivo por el que el depurador no se ha asociado correctamente a un tipo de código, puede intentar asociarlo de nuevo con ese tipo de código exclusivamente.  
  
 **Para obtener información específica acerca de por qué un tipo de código no se pudo conectar:**  
  
1.  Desasocie el proceso. En el **depurar** menú, seleccione **Desasociar todo**.  
  
1.  Vuelva a asociar el proceso, pero seleccionando sólo el tipo de código que no se pudo conectar.  
  
    1.  En el **asociar al proceso** diálogo cuadro, seleccione el proceso en el **procesos disponibles** lista.  
  
    2.  Seleccione **seleccione**.  
  
    3.  En el cuadro de diálogo **Seleccionar tipo de código** , seleccione **Depurar estos tipos de código** y el tipo de código que no se haya asociado correctamente. Anule la selección de los otros tipos de código.  
  
    4.  Seleccione **Aceptar**.  
  
    5.  En el **asociar al proceso** cuadro de diálogo, seleccione **adjuntar**.  
  
    Esta vez se producirá un error en todo el proceso de asociación y aparecerá un mensaje de error específico.  
  
## <a name="see-also"></a>Vea también  
 [Depurar varios procesos](../debugger/debug-multiple-processes.md)   
 [Depuración Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Depuración remota](../debugger/remote-debugging.md)
 