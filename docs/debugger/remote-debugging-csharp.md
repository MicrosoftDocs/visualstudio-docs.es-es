---
title: Depuración C# remota de un proyecto de o VB | Microsoft Docs
ms.custom:
- remotedebugging"=
- seodec18
ms.date: 08/14/2018
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3490cab7c902dcdf1a7d0095eb69dd44de47a727
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211125"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Depuración remota C# de un proyecto de o Visual Basic en Visual Studio
Para depurar una aplicación de Visual Studio que se ha implementado en otro equipo, instale y ejecute las herramientas remotas en el equipo en el que ha implementado la aplicación, configure el proyecto para que se conecte al equipo remoto desde Visual Studio y, a continuación, ejecute la aplicación.

![Componentes del Depurador remoto] (../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Para obtener información sobre la depuración remota de aplicaciones universales de Windows (UWP), consulte [depurar un paquete de aplicaciones instalado](debug-installed-app-package.md).

## <a name="requirements"></a>Requisitos

El depurador remoto se admite en Windows 7 y versiones más recientes (no en teléfono) y versiones de Windows Server a partir de Windows Server 2008 Service Pack 2. Para obtener una lista completa de los requisitos, consulte [requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> No se admite la depuración entre dos equipos conectados a través de un proxy. No se recomienda la depuración a través de una conexión de alta latencia o de ancho de banda bajo, como acceso telefónico a Internet o a través de Internet a través de países, y puede producir un error o ser inaceptablemente lento.

## <a name="download-and-install-the-remote-tools"></a>Descarga e instalación de las herramientas remotas

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> En algunos escenarios, puede ser más eficaz ejecutar el depurador remoto desde un recurso compartido de archivos. Para obtener más información, vea [ejecutar el depurador remoto desde un recurso compartido de archivos](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="BKMK_setup"></a> Establecimiento del depurador remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si necesita agregar permisos para usuarios adicionales, cambie el modo de autenticación o el número de puerto para el depurador remoto, vea [configurar el depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote_csharp"></a>Depuración remota del proyecto
El depurador no puede implementar aplicaciones de escritorio de Visual C# o Visual Basic en un equipo remoto, pero se pueden depurar de manera remota como se describe a continuación. En el procedimiento siguiente se da por supuesto que desea depurar en un equipo denominado **MJO-DL**, tal como se muestra en la ilustración siguiente.

1. Cree un proyecto WPF denominado **MyWpf**.

2. Establezca un punto de interrupción en alguna parte del código fácilmente accesible.

    Por ejemplo, puede establecer un punto de interrupción en un controlador de botón. Para ello, Abra MainWindow. XAML y agregue un control botón desde el cuadro de herramientas; a continuación, haga doble clic en el botón para abrir su controlador.

3. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y, luego, elija **Propiedades**.

4. En la página **Propiedades**, elija la pestaña **Depurar**.

    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")

5. Asegúrese de que el cuadro de texto **Directorio de trabajo** está vacío.

6. Elija **usar equipo remoto**y escriba **nombredelamáquina: Puerto** en el cuadro de texto. (El número de puerto se muestra en la ventana del Depurador remoto. El número de Puerto incrementa 2 en cada versión de Visual Studio.

    En este ejemplo, use:
    ::: moniker range=">=vs-2019"
    **MJO-DL: 4024** en Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **MJO-DL: 4022** en Visual Studio 2017
    ::: moniker-end

7. Asegúrese de que la opción **Habilitar la depuración de código nativo** no está seleccionada.

8. Compile el proyecto.

9. Cree una carpeta en el equipo remoto en la misma ruta de acceso que la carpeta **Depurar** del equipo de Visual Studio: **\<ruta de acceso de origen>\MyWPF\MyWPF\bin\Debug**.

10. Copie el archivo ejecutable que acaba de compilar desde el equipo de Visual Studio a la carpeta recién creada en el equipo remoto.

    > [!CAUTION]
    > No realice cambios en el código o vuelva a generarlo (o debe repetir este paso). El archivo ejecutable que copió en el equipo remoto debe coincidir exactamente con el origen local y los símbolos.

    Puede copiar el proyecto manualmente, usar xcopy, Robocopy, PowerShell u otras opciones.

11. Asegúrese de que el depurador remoto se está ejecutando en el equipo de destino (si no es así, busque el **Depurador remoto** en el menú **Inicio** ). La ventana del Depurador remoto tiene el siguiente aspecto.

     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")

12. En Visual Studio, inicie la depuración (**Depurar > Iniciar depuración** o presione **F5**).

13. Si se le solicita, escriba las credenciales de red para conectarse a la máquina remota.

     Las credenciales requeridas varían en función de la configuración de seguridad de la red. Por ejemplo, en un equipo de dominio, puede escribir el nombre de dominio y la contraseña. En una máquina que no es de dominio, puede escribir el nombre del equipo y un nombre de cuenta de <strong>MJO-DL\name@something.com</strong>usuario válido, como, junto con la contraseña correcta.

     Verá que la ventana principal de la aplicación de WPF está abierta en el equipo remoto.

14. Si es necesario, tome medidas para alcanzar el punto de interrupción. Debe ver que el punto de interrupción está activo. Si no lo está, quiere decir que no se han cargado los símbolos de la aplicación. Vuelva a intentarlo y, si eso no funciona, obtenga información sobre la carga de símbolos y cómo solucionarlos a través de [los archivos de símbolos y la configuración de símbolos de Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).

15. En la máquina de Visual Studio, verá que la ejecución se detiene en el punto de interrupción.

    Si tiene archivos que no son de código que debe usar la aplicación, debe incluirlos en el proyecto de Visual Studio. Cree una carpeta de proyecto para los archivos adicionales (en el **Explorador de soluciones**, haga clic en **Agregar > Nueva carpeta**). A continuación, agregue los archivos a la carpeta (en el **Explorador de soluciones**, haga clic en **Agregar > Elemento existente** y, a continuación, seleccione los archivos). En la página **Propiedades** de cada archivo, establezca **Copiar en el directorio de resultado** en **Copiar siempre**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurar la depuración con símbolos remotos

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Vea también
- [Depurar en Visual Studio](../debugger/index.yml)
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
- [Configurar el Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Asignaciones de puertos del depurador remoto](../debugger/remote-debugger-port-assignments.md)
- [Depuración remota de ASP.NET en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)