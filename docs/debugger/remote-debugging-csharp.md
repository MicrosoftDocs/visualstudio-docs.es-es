---
title: Depuración remota de un proyecto de C o VB Microsoft Docs
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
ms.openlocfilehash: 5f147acae956ad380c6e85984de29d5316394c0a
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301078"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Depuración remota de un proyecto de Visual Basic o de C.
Para depurar una aplicación de Visual Studio que se ha implementado en un equipo diferente, instale y ejecute las herramientas remotas en el equipo donde implementó la aplicación, configure el proyecto para conectarse al equipo remoto desde Visual Studio y, a continuación, ejecute la aplicación.

![Componentes del depurador remoto](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Para obtener información acerca de la depuración remota de aplicaciones universales de Windows (UWP), vea [Depurar un paquete](debug-installed-app-package.md)de aplicación instalado .

## <a name="requirements"></a>Requisitos

El depurador remoto es compatible con Windows 7 y versiones posteriores (no teléfono) y versiones de Windows Server a partir de Windows Server 2008 Service Pack 2. Para obtener una lista completa de los requisitos, consulte [Requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> No se admite la depuración entre dos equipos conectados a través de un proxy. No se recomienda depurar a través de una conexión de alta latencia o bajo ancho de banda, como Internet de acceso telefónico o a través de Internet entre países, y puede fallar o ser inaceptablemente lento.

## <a name="download-and-install-the-remote-tools"></a>Descarga e instalación de las herramientas remotas

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> En algunos escenarios, puede ser más eficaz ejecutar el depurador remoto desde un recurso compartido de archivos. Para obtener más información, vea [Ejecutar el depurador remoto desde un recurso compartido](../debugger/remote-debugging.md#fileshare_msvsmon)de archivos.

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a>Configurar el depurador remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si necesita agregar permisos para usuarios adicionales, cambiar el modo de autenticación o el número de puerto para el depurador remoto, consulte [Configurar el depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote-debug-the-project"></a><a name="remote_csharp"></a>Depuración remota del proyecto
El depurador no puede implementar aplicaciones de escritorio de Visual C# o Visual Basic en un equipo remoto, pero se pueden depurar de manera remota como se describe a continuación. En el siguiente procedimiento se supone que desea depurarlo en un equipo denominado **MJO-DL**, como se muestra en la ilustración siguiente.

1. Cree un proyecto WPF denominado **MyWpf**.

2. Establezca un punto de interrupción en alguna parte del código fácilmente accesible.

    Por ejemplo, puede establecer un punto de interrupción en un controlador de botón. Para ello, abra MainWindow.xamly agregue un Button control desde el cuadro de herramientas y, a continuación, haga doble clic en el botón para abrir su controlador.

3. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y, luego, elija **Propiedades**.

4. En la página **Propiedades**, elija la pestaña **Depurar**.

    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")

5. Asegúrese de que el cuadro de texto **Directorio de trabajo** está vacío.

6. Elija **Use remote machine (Usar máquina remota)** y escriba **yourmachinename:port** en el cuadro de texto. (El número de puerto se muestra en la ventana del depurador remoto. El número de puerto incrementa 2 en cada versión de Visual Studio).

    En este ejemplo, utilice:
    ::: moniker range=">=vs-2019"
    **MJO-DL:4024** en Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **MJO-DL:4022** en Visual Studio 2017
    ::: moniker-end

7. Asegúrese de que la opción **Habilitar la depuración de código nativo** no está seleccionada.

8. Compile el proyecto.

9. Cree una carpeta en el equipo remoto en la misma ruta de acceso que la carpeta **Depurar** del equipo de Visual Studio: **\<ruta de acceso de origen>\MyWPF\MyWPF\bin\Debug**.

10. Copie el archivo ejecutable que acaba de compilar desde el equipo de Visual Studio a la carpeta recién creada en el equipo remoto.

    > [!CAUTION]
    > No realice cambios en el código ni vuelva a generarlo (o debe repetir este paso). El archivo ejecutable que copió en el equipo remoto debe coincidir exactamente con el origen local y los símbolos.

    Puede copiar el proyecto manualmente, utilizar Xcopy, Robocopy, Powershell u otras opciones.

11. Asegúrese de que el depurador remoto se está ejecutando en el equipo de destino (si no lo está, busque **Depurador remoto** en el menú **Inicio).** La ventana del depurador remoto tiene este aspecto.

     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")

12. En Visual Studio, inicie la depuración (**Depurar > Iniciar depuración** o presione **F5**).

13. Si se le solicita, escriba las credenciales de red para conectarse al equipo remoto.

     Las credenciales necesarias varían en función de la configuración de seguridad de la red. Por ejemplo, en un equipo de dominio, puede escribir su nombre de dominio y contraseña. En un equipo que no sea de dominio, puede escribir <strong>MJO-DL\name@something.com</strong>el nombre del equipo y un nombre de cuenta de usuario válido, como , junto con la contraseña correcta.

     Verá que la ventana principal de la aplicación de WPF está abierta en el equipo remoto.

14. Si es necesario, tome medidas para alcanzar el punto de interrupción. Debe ver que el punto de interrupción está activo. Si no lo está, quiere decir que no se han cargado los símbolos de la aplicación. Vuelva a intentarlo y, si eso no funciona, obtenga información sobre cómo cargar símbolos y cómo solucionarlos en Descripción de los archivos de símbolos y la [configuración de símbolos](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)de Visual Studio.

15. En la máquina de Visual Studio, verá que la ejecución se detiene en el punto de interrupción.

    Si tiene archivos que no sean de código que la aplicación necesita usar, debe incluirlos en el proyecto de Visual Studio. Cree una carpeta de proyecto para los archivos adicionales (en el **Explorador**de soluciones , haga clic en **Agregar > nueva carpeta**). A continuación, agregue los archivos a la carpeta (en el **Explorador de soluciones**, haga clic en **Agregar > Elemento existente** y, a continuación, seleccione los archivos). En la página **Propiedades** de cada archivo, establezca **Copiar en el directorio de resultado** en **Copiar siempre**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurar la depuración con símbolos remotos

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Consulte también
- [Depuración en Visual Studio](../debugger/index.yml)
- [Primero mire el depurador](../debugger/debugger-feature-tour.md)
- [Configurar el Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Asignaciones de puerto del depurador remoto](../debugger/remote-debugger-port-assignments.md)
- [Depuración remota de ASP.NET en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)