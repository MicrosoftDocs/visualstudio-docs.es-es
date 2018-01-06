---
title: Ejecutar aplicaciones UWP en un equipo remoto | Documentos de Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
caps.latest.revision: "43"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: ebae0886db71b0b06f346d6bd174951b1c5d4752
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="run-uwp-apps-on-a-remote-machine"></a>Ejecutar aplicaciones UWP en un equipo remoto
![Solo se aplica a Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
Para ejecutar una aplicación de UWP en un equipo remoto, debe asociar a él mediante las herramientas remotas de Visual Studio. Las herramientas remotas permiten ejecutar, depurar, generar perfiles y probar una aplicación para UWP que se ejecuta en un dispositivo desde un segundo equipo que ejecuta Visual Studio. La ejecución en un dispositivo remoto es muy eficaz cuando el equipo de Visual Studio no admite la funcionalidad que es específica para las aplicaciones UWP, como la entrada táctil, ubicación geográfica y orientación física. En este tema se describen los procedimientos para configurar e iniciar una sesión remota.

En algunos casos, las herramientas remotas se instalan automáticamente cuando se implementa en un dispositivo remoto.

- Para equipos con Windows 10 ejecutan creadores de actualización y versiones posteriores, consulte [depurar un paquete de aplicaciones instalado](debug-installed-app-package.md#remote). Herramientas remotas se instalarán automáticamente.
- Para dispositivos Windows 10 Xbox, IOT y HoloLens, consulte [depurar un paquete de aplicaciones instalado](debug-installed-app-package.md#remote). Herramientas remotas se instalarán automáticamente.
- Para Windows Phone, debe estar conectado físicamente al teléfono, debe instalar un [licencia de desarrollador](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh974578.aspx) (Windows Phone 8 y 8.1) o habilitar [modo de programador](/windows/uwp/get-started/enable-your-device-for-development) (Windows Mobile 10), y se debe Seleccione **dispositivo** como el destino de depuración. Herramientas remotas no se requiere o admite.

Para equipos con Windows 8.1 y los equipos de Windows 10 que se ejecutan una versión de actualización del pre-creador de Windows, debe instalar las herramientas remotas en el equipo remoto manualmente antes de poder depurar. Siga las instrucciones de este tema.
  
##  <a name="BKMK_Prerequisites"></a> Requisitos previos  
 Para depurar en un dispositivo remoto:  
  
-   El dispositivo remoto y el equipo de Visual Studio se deben conectar a través de una red o directamente mediante un cable Ethernet. No se admite la depuración a través de Internet.  

- El dispositivo remoto debe habilitarse para el desarrollo.

    - Para dispositivos Windows 8 y Windows 8.1, una [licencia de desarrollador](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh974578.aspx) debe estar instalado en el dispositivo remoto.
    - Para dispositivos Windows 10, debe habilitar [modo de programador](/windows/uwp/get-started/enable-your-device-for-development). 
  
-   Para equipos con Windows 10 ejecutando una versión anterior a la actualización del creador de Windows 10 de Windows 10, debe instalar y ejecutar los componentes de depuración remota.
  
-   Debes ser administrador en el dispositivo remoto para configurar el firewall durante la instalación. Debes tener acceso de usuario al dispositivo remoto para ejecutar o conectar el depurador remoto.  
  
##  <a name="BKMK_Security"></a> Seguridad  
 De forma predeterminada, el depurador remoto utiliza la autenticación de Windows.  
  
> [!WARNING]
>  También puedes ejecutar el depurador remoto en modo sin autenticación, pero se recomienda encarecidamente no usar este modo. No hay ninguna seguridad de red cuando se ejecuta en este modo. Elige el modo sin autenticación solo si estás seguro de que la red no presenta riesgos de tráfico malintencionado u hostil.  
  
##  <a name="BKMK_DirectConnect"></a> Cómo conectar directamente a un dispositivo remoto  
 Para conectar directamente a un dispositivo remoto, conecta el equipo de Visual Studio al dispositivo mediante un cable Ethernet estándar. Si el dispositivo no tiene puerto Ethernet, puedes usar un adaptador de USB a Ethernet para conectar el cable.  
  
## <a name="BKMK_download"></a>Descargue e instale las herramientas remotas

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
## <a name="BKMK_setup"></a>Configurar el depurador remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]
  
##  <a name="BKMK_ConnectVS"></a> Configurar el proyecto de Visual Studio para la depuración remota  
 Especifica el dispositivo remoto al que quieras conectarte en las propiedades del proyecto. El procedimiento varía según cuál sea el lenguaje de programación. Puedes escribir el nombre de red del dispositivo remoto, o bien seleccionarlo en el cuadro de diálogo Seleccionar conexión del depurador remoto.  
  
 ![Cuadro de diálogo Seleccionar conexión del depurador remoto](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 En el cuadro de diálogo se muestran solo los dispositivos que están en la subred local del equipo de Visual Studio y que ejecutan el depurador remoto.  
  
> [!TIP]
>  Si tienes dificultades para conectarte con un dispositivo remoto, intenta escribir la dirección IP del dispositivo. Para determinar la dirección IP de un dispositivo, abre una ventana de comandos y escribe **ipconfig**. La dirección IP aparece como **IPv4 Address**.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Elegir el dispositivo remoto para los proyectos de C# y Visual Basic  
 ![Administrar propiedades del proyecto para la depuración remota](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1.  En el Explorador de soluciones, selecciona el nombre del proyecto y elige **Propiedades** en el menú contextual.  
  
2.  Selecciona **Depurar**.  
  
3.  Elige **Equipo remoto** en la lista **Dispositivo de destino** .  
  
4.  Escribe el nombre de red del dispositivo remoto en el cuadro **Equipo remoto** o elige **Buscar** para elegir el dispositivo en el cuadro de diálogo **Seleccionar conexión del depurador remoto** .  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Elegir el dispositivo remoto para los proyectos de JavaScript y C++  
 ![C &#43; &#43; proyectar las propiedades para la depuración remota](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1.  En el Explorador de soluciones, selecciona el nombre del proyecto y elige **Propiedades** en el menú contextual.  
  
2.  Expande el nodo **Propiedades de configuración** y selecciona **Depuración**.  
  
3.  Elige **Depurador remoto** en la lista **Depurador para iniciar** .  
  
4.  Escribe el nombre de red del dispositivo remoto en el cuadro **Nombre de equipo** o bien elige la flecha abajo contigua para elegir el dispositivo en el cuadro de diálogo **Seleccionar conexión del depurador remoto** .  
  
##  <a name="BKMK_RunRemoteDebug"></a> Ejecutar una sesión de depuración remota  
 Una sesión de depuración remota se inicia, se detiene y se navega por ella de la misma forma que una sesión local. Antes de iniciar la depuración, asegúrate de que el Monitor de depuración remota se ejecute en el dispositivo remoto.  
  
 A continuación, elige **Iniciar depuración** en el menú **Depurar** (teclado: F5). El proyecto se recompila. Luego, se implementa e inicia en el dispositivo remoto. El depurador suspende la ejecución en los puntos de interrupción. Puedes depurar paso a paso por instrucciones o por procedimientos y hasta salir del código. Elige **Detener depuración** para finalizar la sesión de depuración y cerrar la aplicación remota. Para obtener más información, consulte [depurar aplicaciones en Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también  
 [Testing UWP apps with Visual Studio (Probar aplicaciones para UWP con Visual Studio)](../test/testing-store-apps-with-visual-studio.md)   
 [Depurar aplicaciones en Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)