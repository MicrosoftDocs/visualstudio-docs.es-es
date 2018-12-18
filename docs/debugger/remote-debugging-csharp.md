---
title: Depuración remota de un proyecto C# o VB en Visual Studio | Microsoft Docs
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: a9753fbb-e7f4-47f0-9dbe-9de90c6c8457
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 9d6bd68f5e94e04cab01dcb7bafd7dcc3cf3c17d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49936130"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Depuración remota de un proyecto C# o Visual Basic en Visual Studio
Para depurar una aplicación de Visual Studio que se ha implementado en un equipo diferente, instalar y ejecutar las herramientas remotas en el equipo donde ha implementado la aplicación, configurar el proyecto para conectarse al equipo remoto desde Visual Studio y, a continuación, ejecute la aplicación.

![Componentes del depurador remoto](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")
  
Para obtener información acerca de las aplicaciones universales de Windows (UWP) de depuración remota, vea [depurar un paquete de aplicaciones instalado](debug-installed-app-package.md).

## <a name="requirements"></a>Requisitos

El depurador remoto es compatible con Windows 7 y versiones más recientes (no de teléfono) y las versiones de Windows Server a partir de Windows Server 2008 Service Pack 2. Para obtener una lista completa de requisitos, consulte [requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> No se admite la depuración entre dos equipos conectados a través de un servidor proxy. Depuración mediante una conexión de ancho de banda bajo, por ejemplo, acceso telefónico a Internet, o una latencia alta o a través de Internet entre países no se recomienda y puede ser un error o inaceptablemente bajo.
  
## <a name="download-and-install-the-remote-tools"></a>Descargue e instale las herramientas remotas

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> En algunos escenarios, puede ser más eficaz para ejecutar al depurador remoto desde un recurso compartido de archivos. Para obtener más información, consulte [ejecutar el depurador remoto desde un recurso compartido de archivos](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Configurar el depurador remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si necesita agregar permisos para usuarios adicionales, cambiar el modo de autenticación, o número de puerto para el depurador remoto, consulte [configurar el depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).
  
## <a name="remote_csharp"></a> El proyecto de depuración remota
El depurador no puede implementar aplicaciones de escritorio de Visual C# o Visual Basic en un equipo remoto, pero se pueden depurar de manera remota como se describe a continuación. El siguiente procedimiento se da por supuesto que desea depurar en un equipo denominado **MJO DL**, como se muestra en la ilustración siguiente.
  
1. Cree un proyecto WPF denominado **MyWpf**.  
  
2. Establezca un punto de interrupción en alguna parte del código fácilmente accesible.  
  
    Por ejemplo, puede establecer un punto de interrupción en un controlador de botón. Para ello, abra MainWindow.xaml y agregar un control de botón en el cuadro de herramientas, a continuación, haga doble clic en el botón para abrir su controlador.
  
3. En el Explorador de soluciones, haga clic en el proyecto y elija **propiedades**.  
  
4. En el **propiedades** página, elija el **depurar** ficha.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Asegúrese de que el **directorio de trabajo** cuadro de texto está vacío.  
  
6. Elija **usar equipo remoto**y el tipo **MJO-DL:4022** en el cuadro de texto. (4022 es el número de puerto que se muestra en la ventana del depurador remoto. El número de puerto incrementa 2 en cada versión de Visual Studio).
  
7. Asegúrese de que **Habilitar depuración de código nativo** no está seleccionada.  
  
8. Compile el proyecto.  
  
9. Cree una carpeta en el equipo remoto que es la misma ruta que el **depurar** carpeta del equipo de Visual Studio:  **\<ruta de acceso de origen > \MyWPF\MyWPF\bin\Debug**.  
  
10. Copie el archivo ejecutable que acaba de compilar desde el equipo de Visual Studio a la carpeta recién creada en el equipo remoto.
  
    > [!CAUTION]
    >  No realice cambios en el código o volver a generar (o debe repetir este paso). El archivo ejecutable que copió en el equipo remoto debe coincidir exactamente con el origen local y los símbolos.

    Puede copiar manualmente el proyecto, use Xcopy, Robocopy, Powershell u otras opciones.
  
11. Asegúrese de que el depurador remoto se está ejecutando en el equipo de destino (si no es así, busque **Remote Debugger** en el **iniciar** menú). La ventana del depurador remoto tiene este aspecto.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. En Visual Studio, inicie la depuración (**Depurar > Iniciar depuración**, o **F5**).  
  
13. Si se le solicite, escriba las credenciales de red para conectarse a la máquina remota.  
  
     Las credenciales requeridas varían según la configuración de seguridad de su red. Por ejemplo, en un equipo de dominio, puede escribir el nombre de dominio y la contraseña. En un equipo que no sea de dominio, puede escribir el nombre del equipo y un nombre de cuenta de usuario válido, como <strong>MJO-DL\name@something.com</strong>, junto con la contraseña correcta.

     Debería ver que la ventana principal de la aplicación de WPF está abierta en el equipo remoto.
  
14. Si es necesario, tome medidas para el punto de interrupción. Debe ver que el punto de interrupción está activo. Si no lo está, no ha cargado los símbolos para la aplicación. Vuelva a intentar y si esto no funciona, obtener información sobre la carga de símbolos y cómo solucionarlos en [descripción de los archivos de símbolos y Visual Studio Lores](https://blogs.msdn.microsoft.com/devops/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/).
  
15. En la máquina de Visual Studio, verá que la ejecución se detiene en el punto de interrupción.
  
    Si tiene los archivos que no son de código que necesitan ser utilizadas por la aplicación, deberá incluirlos en el proyecto de Visual Studio. Cree una carpeta de proyecto para los archivos adicionales (en el **el Explorador de soluciones**, haga clic en **Agregar > nueva carpeta**). A continuación, agregue los archivos a la carpeta (en el **el Explorador de soluciones**, haga clic en **Agregar > elemento existente**, a continuación, seleccione los archivos). En el **propiedades** para cada archivo, establezca **Copy to Output Directory** a **copiar siempre**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurar la depuración con símbolos remotos 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]  
  
## <a name="see-also"></a>Vea también  
 [Depurar en Visual Studio](../debugger/index.md)  
 [Guía de características del depurador](../debugger/debugger-feature-tour.md)   
 [Configurar el Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [Depuración remota de ASP.NET en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)