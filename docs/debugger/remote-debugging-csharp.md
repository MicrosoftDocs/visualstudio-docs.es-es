---
title: Remoto depurar un proyecto C# o VB en Visual Studio | Documentos de Microsoft
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
ms.openlocfilehash: 18cd64e24481111e22b3b9b842433bb1b1c19e0f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477711"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Un proyecto de C# o Visual Basic en Visual Studio la depuración remota
Para depurar una aplicación de Visual Studio que se ha implementado en un equipo diferente, instalar y ejecutar las herramientas remotas en el equipo donde se implementa la aplicación y, a continuación, configure el proyecto para conectarse al equipo remoto desde Visual Studio y, a continuación, ejecutar la aplicación.

![Los componentes del depurador remoto](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")
  
Para obtener información acerca de las aplicaciones universales de Windows (UWP) la depuración remota, vea [depurar un paquete de aplicaciones instalado](debug-installed-app-package.md).

## <a name="requirements"></a>Requisitos

El depurador remoto es compatible con Windows 7 y versiones más recientes (no de teléfono) y versiones de Windows Server a partir de Windows Server 2008 Service Pack 2. Para obtener una lista completa de requisitos, consulte [requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> No se admite la depuración entre dos equipos conectados a través de un servidor proxy. Depuración mediante una conexión de poco ancho de banda, como acceso telefónico a Internet, o una latencia alta o a través de Internet a través de países no se recomienda y puede ser un error o inaceptablemente bajo.
  
## <a name="download-and-install-the-remote-tools"></a>Descargue e instale las herramientas remotas

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> En algunos casos, puede ser más eficaz para ejecutar al depurador remoto desde un recurso compartido de archivos. Para obtener más información, consulte [ejecutar el depurador remoto desde un recurso compartido de archivos](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Configurar el depurador remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si necesita agregar permisos para los usuarios adicionales, cambiar el modo de autenticación o número de puerto para el depurador remoto, consulte [configurar el depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).
  
## <a name="remote_csharp"></a> El proyecto de depuración remota
El depurador no puede implementar aplicaciones de escritorio de Visual C# o Visual Basic en un equipo remoto, pero se pueden depurar de manera remota como se describe a continuación. El siguiente procedimiento se da por supuesto que va a depurar en un equipo denominado **MJO DL**, tal y como se muestra en la ilustración siguiente.
  
1.  Crear un proyecto WPF denominado **MyWpf**.  
  
2.  Establezca un punto de interrupción en alguna parte del código fácilmente accesible.  
  
     Por ejemplo, puede establecer un punto de interrupción en un controlador de botón. Para ello, abra MainWindow.xaml y agregar un control de botón desde el cuadro de herramientas y, a continuación, haga doble clic en el botón para abrir su controlador.
  
3.  En el Explorador de soluciones, haga clic en el proyecto y elija **propiedades**.  
  
4.  En el **propiedades** página, elija la **depurar** ficha.  
  
     ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5.  Asegúrese de que el **directorio de trabajo** cuadro de texto está vacío.  
  
6.  Elija **usar equipo remoto**y el tipo de **MJO-DL:4022** en el cuadro de texto. (4022 es el número de puerto que se muestra en la ventana del depurador remoto. El número de puerto incrementa 2 en cada versión de Visual Studio).
  
7.  Asegúrese de que **habilitar la depuración de código nativo** no está seleccionada.  
  
8.  Compile el proyecto.  
  
9. Cree una carpeta en el equipo remoto que sea la misma ruta que la **depurar** carpeta en el equipo de Visual Studio:  **\<ruta de acceso de origen > \MyWPF\MyWPF\bin\Debug**.  
  
10. Copie el archivo ejecutable que acaba de compilar desde el equipo de Visual Studio a la carpeta recién creada en el equipo remoto.
  
    > [!CAUTION]
    >  No realice cambios en el código o volver a generar (o debe repetir este paso). El archivo ejecutable que copió en el equipo remoto debe coincidir exactamente con el origen local y los símbolos.

    Puede copiar manualmente el proyecto, utilizar Xcopy, Robocopy, Powershell u otras opciones.
  
11. Asegúrese de que el depurador remoto se ejecuta en el equipo de destino (si no es así, busque **depurador remoto** en el **iniciar** menú). La ventana del depurador remoto tiene el siguiente aspecto.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. En Visual Studio, inicie la depuración (**Depurar > Iniciar depuración**, o **F5**).  
  
13. Si se le solicite, escriba las credenciales de red para conectarse al equipo remoto.  
  
     Las credenciales requeridas varían según la configuración de seguridad de su red. Por ejemplo, en un equipo de dominio, puede especificar el nombre de dominio y la contraseña. En un equipo no es de dominio, puede escribir el nombre del equipo y un nombre de cuenta de usuario válido, como **MJO-DL\name@something.com**, junto con la contraseña correcta.

     Debería ver que la ventana principal de la aplicación de WPF está abierta en el equipo remoto.
  
14. Si es necesario, tome medidas para el punto de interrupción. Debe ver que el punto de interrupción está activo. Si no es así, se han cargado los símbolos de la aplicación. Vuelva a intentar y, si esto no funciona, obtener información sobre la carga de símbolos y cómo solucionar problemas con ellos en [configuración de símbolos de los archivos de símbolos de descripción y Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/05/understanding-symbol-files-and-visual-studio-s-symbol-settings.aspx).
  
15. En la máquina de Visual Studio, verá que la ejecución se detiene en el punto de interrupción.
  
 Si tiene archivos de código que debe usar la aplicación, deberá incluirlos en el proyecto de Visual Studio. Cree una carpeta de proyecto para los archivos adicionales (en el **el Explorador de soluciones**, haga clic en **Agregar > nueva carpeta**). A continuación, agregue los archivos a la carpeta (en el **el Explorador de soluciones**, haga clic en **Agregar > elemento existente**, a continuación, seleccione los archivos). En el **propiedades** para cada archivo, establezca **copiar en el directorio de salida** a **copiar siempre**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurar la depuración con símbolos remotos 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]  
  
## <a name="see-also"></a>Vea también  
 [Depurar en Visual Studio](../debugger/index.md)  
 [Guía de características del depurador](../debugger/debugger-feature-tour.md)   
 [Configurar el Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Asignaciones de puerto del depurador remoto](../debugger/remote-debugger-port-assignments.md)   
 [Depuración remota de ASP.NET en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)