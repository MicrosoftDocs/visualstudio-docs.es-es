---
title: Ejecutar aplicaciones UWP en un equipo remoto | Documentos de Microsoft
ms.custom: ''
ms.date: 01/05/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 2c09d29340584f3f6187175342fd1171dd59ba37
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477321"
---
# <a name="run-uwp-apps-on-a-remote-machine-in-visual-studio"></a>Ejecutar aplicaciones UWP en un equipo remoto en Visual Studio
  
Para ejecutar una aplicación de UWP en un equipo remoto, debe asociar a él mediante las herramientas remotas para Visual Studio. Las herramientas remotas permiten ejecutar, depurar, generar perfiles y probar una aplicación para UWP que se ejecuta en un dispositivo desde un segundo equipo que ejecuta Visual Studio. La ejecución en un dispositivo remoto es muy eficaz cuando el equipo de Visual Studio no admite la funcionalidad que es específica para las aplicaciones UWP, como la entrada táctil, ubicación geográfica y orientación física. En este tema se describen los procedimientos para configurar e iniciar una sesión remota.

En algunos casos, las herramientas remotas se instalan automáticamente cuando se implementa en un dispositivo remoto.

- Para equipos con Windows 10 ejecutan creadores de actualización y versiones posteriores, herramientas remotas se instalarán automáticamente.
- Para dispositivos Windows 10 Xbox, IOT y HoloLens, herramientas remotas se instalarán automáticamente.
- Para dispositivos móviles de Windows 10, debe estar conectado físicamente al teléfono, debe habilitar [modo de programador](/windows/uwp/get-started/enable-your-device-for-development) y deberá seleccionar **dispositivo** como el destino de depuración. Herramientas remotas no se requiere o admite.

Para equipos con Windows 10 ejecutando una versión de actualización del pre-creador de Windows, debe instalar las herramientas remotas en el equipo remoto manualmente antes de poder depurar. Siga las instrucciones de este tema. 
  
##  <a name="BKMK_Prerequisites"></a> Requisitos previos  
 Para depurar en un dispositivo remoto:  
  
- El dispositivo remoto y el equipo de Visual Studio deben ser conectados a través de una red o conectados directamente a través de un cable USB o Ethernet. No se admite la depuración a través de Internet.  

- Debe habilitar [modo de programador](/windows/uwp/get-started/enable-your-device-for-development). 
  
- Para equipos con Windows 10 ejecutando una versión anterior a la actualización del creador de Windows 10 de Windows 10, debe [instalar y ejecutar los componentes de depuración remota](#BKMK_download).
  
##  <a name="BKMK_Security"></a> Seguridad  
De forma predeterminada, **Universal (protocolo sin cifrar)** se usa en Windows 10. Este protocolo sólo debe utilizarse en redes de confianza. La conexión de depuración es vulnerable a los usuarios malintencionados que pudieron interceptar y cambiar los datos que se pasan entre el desarrollo y el equipo remoto.
  
> [!WARNING]
>  No hay ninguna seguridad de red al establecer el modo de autenticación en **Universal (protocolo sin cifrar)** o **ninguno**. Elegir estos modos solamente si está seguro de que la red no presenta riesgos de tráfico hostil o malintencionado.  
  
##  <a name="BKMK_DirectConnect"></a> Cómo conectar directamente con un cable USB 

En Windows 10, puede implementar en un dispositivo conectado por USB eligiendo **dispositivo** en lugar de **equipo remoto** como el destino de implementación (puede hacer esto en el **estándar** barra de herramientas o en la página de propiedades de depuración).

##  <a name="BKMK_ConnectVS"></a> Configurar el proyecto de Visual Studio para la depuración remota  
 Especifica el dispositivo remoto al que quieras conectarte en las propiedades del proyecto. El procedimiento varía según cuál sea el lenguaje de programación. Puede escribir el nombre de red del dispositivo remoto o puede seleccionarlo en el **conexión remota** cuadro de diálogo.  
  
 ![Cuadro de diálogo Seleccionar conexión del depurador remoto](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 En el cuadro de diálogo se muestran solo los dispositivos que están en la subred local del equipo de Visual Studio y que ejecutan el depurador remoto.  
  
> [!TIP]
>  Si tienes dificultades para conectarte con un dispositivo remoto, intenta escribir la dirección IP del dispositivo. Para determinar la dirección IP de un dispositivo, abre una ventana de comandos y escribe **ipconfig**. La dirección IP aparece como **IPv4 Address**.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Elija el dispositivo remoto para los proyectos de C# y Visual Basic  
  
1.  En el Explorador de soluciones, selecciona el nombre del proyecto y elige **Propiedades** en el menú contextual.  
  
2.  Selecciona **Depurar**.  
  
3.  Elige **Equipo remoto** en la lista **Dispositivo de destino** .  
  
4.  Escribe el nombre de red del dispositivo remoto en el cuadro **Equipo remoto** o elige **Buscar** para elegir el dispositivo en el cuadro de diálogo **Seleccionar conexión del depurador remoto** . 

    ![Administrar propiedades del proyecto para la depuración remota](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Elija el dispositivo remoto para los proyectos de JavaScript y C++  
  
1.  En el Explorador de soluciones, selecciona el nombre del proyecto y elige **Propiedades** en el menú contextual.  
  
2.  Expande el nodo **Propiedades de configuración** y selecciona **Depuración**.  
  
3.  Elige **Depurador remoto** en la lista **Depurador para iniciar** .  
  
4.  Escribe el nombre de red del dispositivo remoto en el cuadro **Nombre de equipo** o bien elige la flecha abajo contigua para elegir el dispositivo en el cuadro de diálogo **Seleccionar conexión del depurador remoto** .  

    ![C&#43; &#43; proyectar las propiedades para la depuración remota](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")
  
## <a name="BKMK_download"></a> Descargue e instale las herramientas remotas (actualización creadores previa)

Si usa versiones de actualización del pre-creador de Windows 10, a continuación, siga estas instrucciones. En caso contrario, puede omitir esta sección.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Configurar el depurador remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]  
  
##  <a name="BKMK_RunRemoteDebug"></a> Iniciar una sesión de depuración remota  
 Una sesión de depuración remota se inicia, se detiene y se navega por ella de la misma forma que una sesión local. En versiones de actualización del creador anterior de Windows 10, asegúrese de que el Monitor de depuración remota se ejecuta en el dispositivo remoto.  
  
 A continuación, elige **Iniciar depuración** en el menú **Depurar** (teclado: F5). El proyecto se recompila. Luego, se implementa e inicia en el dispositivo remoto. El depurador suspende la ejecución en los puntos de interrupción. Puedes depurar paso a paso por instrucciones o por procedimientos y hasta salir del código. Elige **Detener depuración** para finalizar la sesión de depuración y cerrar la aplicación remota.
  
## <a name="see-also"></a>Vea también  
 [Opciones de implementación remota avanzada](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)  
 [Testing UWP apps with Visual Studio (Probar aplicaciones para UWP con Visual Studio)](../test/testing-store-apps-with-visual-studio.md)   
 [Depurar aplicaciones en Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)