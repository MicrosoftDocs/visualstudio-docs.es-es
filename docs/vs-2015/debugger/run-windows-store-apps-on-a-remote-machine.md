---
title: Ejecución de Windows Store apps en un equipo remoto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a3be715f58d3ed80122dfdd3aaf879c7db8aebd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784551"
---
# <a name="run-windows-store-apps-on-a-remote-machine"></a>Ejecutar aplicaciones de la Tienda Windows en un equipo remoto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Solo se aplica a Windows] (.. /Image/windows_only_content.png "windows_only_content")  
  
 La aplicación Herramientas remotas para Visual Studio permite ejecutar, depurar, generar perfiles y probar una aplicación de la Tienda Windows que se ejecuta en un dispositivo desde un segundo equipo que ejecuta Visual Studio. La ejecución en un dispositivo remoto es muy eficaz cuando el equipo de Visual Studio no admite la funcionalidad específica de las aplicaciones de la Tienda Windows, como la entrada táctil, la ubicación geográfica y la orientación física. En este tema se describen los procedimientos para configurar e iniciar una sesión remota.  
  
##  <a name="BKMK_In_this_topic"></a> En este tema  
 Puedes obtener información sobre:  
  
 [Requisitos previos](#BKMK_Prerequisites)  
  
 [Seguridad](#BKMK_Security)  
  
 [Cómo conectar directamente a un dispositivo remoto](#BKMK_DirectConnect)  
  
 [Instalar las herramientas remotas](#BKMK_Installing_the_Remote_Tools)  
  
 [Iniciar el Monitor de depuración remota](#BKMK_Starting_the_Remote_Debugger_Monitor)  
  
 [Configurar el depurador remoto](#BKMK_ConfigureRemoteDebugger)  
  
 [Configurar el proyecto de Visual Studio para la depuración remota](#BKMK_ConnectVS)  
  
- [Elegir el dispositivo remoto para los proyectos de C# y Visual Basic](#BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects)  
  
- [Elegir el dispositivo remoto para los proyectos de JavaScript y C++](#BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects)  
  
  [Ejecutar una sesión de depuración remota](#BKMK_RunRemoteDebug)  
  
##  <a name="BKMK_Prerequisites"></a> Requisitos previos  
 Para depurar en un dispositivo remoto:  
  
-   El dispositivo remoto y el equipo de Visual Studio se deben conectar a través de una red o directamente mediante un cable Ethernet. No se admite la depuración a través de Internet.  
  
-   Debe haber una licencia de desarrollador instalada en el dispositivo remoto.  
  
-   El dispositivo remoto debe ejecutar los componentes de depuración remota.  
  
-   Debes ser administrador en el dispositivo remoto para configurar el firewall durante la instalación. Debes tener acceso de usuario al dispositivo remoto para ejecutar o conectar el depurador remoto.  
  
##  <a name="BKMK_Security"></a> Seguridad  
 De forma predeterminada, el depurador remoto utiliza la autenticación de Windows.  
  
> [!WARNING]
>  También puedes ejecutar el depurador remoto en modo sin autenticación, pero se recomienda encarecidamente no usar este modo. No hay ninguna seguridad de red cuando se ejecuta en este modo. Elige el modo sin autenticación solo si estás seguro de que la red no presenta riesgos de tráfico malintencionado u hostil.  
  
##  <a name="BKMK_DirectConnect"></a> Cómo conectar directamente a un dispositivo remoto  
 Para conectar directamente a un dispositivo remoto, conecta el equipo de Visual Studio al dispositivo mediante un cable Ethernet estándar. Si el dispositivo no tiene puerto Ethernet, puedes usar un adaptador de USB a Ethernet para conectar el cable.  
  
##  <a name="BKMK_Installing_the_Remote_Tools"></a> Instalar las herramientas remotas  
  
> [!NOTE]
>  **Versiones y actualizaciones**  
>   
>  **Herramientas remotas para Visual Studio 2015** no es compatible con versiones anteriores de Visual Studio.  
>   
>  Recomendamos instalar la versión de actualización de Herramientas remotas para Visual Studio 2015 que coincida con la versión de la actualización de su instalación de Visual Studio.  
>   
>  El depurador de VS es compatible con cualquier combinación de versiones de VS 2015 y Herramientas remotas para VS 2015. Sin embargo, la funcionalidad más reciente de Visual Studio requiere que se usen las versiones de Visual Studio y las Herramientas remotas más actualizadas.  
>   
>  Otras herramientas de diagnóstico podrían requerir las mismas versiones de las herramientas remotas y Visual Studio.  
  
 **Instalar los componentes de depuración remota en un dispositivo remoto**  
  
 Para ejecutar o guardar el programa de instalación para las herramientas remotas, elija uno de los vínculos de esta tabla que coincida con su versión de Visual Studio:  
  
|Versión|Vínculo|Notas|
|-|-|-|
|Visual Studio 2015 Update 3|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si se le solicite, unirse al grupo de Visual Studio Dev Essentials gratuita o solo tiene que iniciar sesión con una suscripción válida de Visual Studio. A continuación, vuelva a abrir el vínculo si es necesario. Descargar siempre la versión que coincida con el sistema operativo del dispositivo (x 86, x64 o versión ARM)|
|Visual Studio 2015 (antigua)|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si se le solicite, unirse al grupo de Visual Studio Dev Essentials gratuita o solo tiene que iniciar sesión con una suscripción válida de Visual Studio. A continuación, vuelva a abrir el vínculo si es necesario. Descargar siempre la versión que coincida con el sistema operativo del dispositivo (x 86, x64 o versión ARM)|
|Visual Studio 2013|[Herramientas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Descargar página de documentación de Visual Studio 2013|
  
 Puedes elegir descargar el programa de instalación o puedes ejecutarlo inmediatamente. Si ejecutas el programa de instalación, acepta el acuerdo de usuario, y elige **Instalar**.  
  
 De forma predeterminada, los componentes de depuración remota se instalan en la carpeta **C:\Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger** .  
  
##  <a name="BKMK_Starting_the_Remote_Debugger_Monitor"></a> Iniciar el Monitor de depuración remota  
  
> [!NOTE]
>  Dado que el depurador remoto configura el firewall para permitir la comunicación con el host de Visual Studio, debes ser administrador en el dispositivo remoto cuando inicies el depurador remoto por primera vez.  
  
 Después de instalar las herramientas remotas, elige **Depurador remoto** en la pantalla **Iniciar** . La **configuración de depuración remota** aparecerá la primera vez que inicies el depurador remoto.  
  
 En el cuadro de diálogo **Configuración de depuración remota** :  
  
1.  Si la API de Servicios web de Windows no está instala, elige **Instalar**.  
  
2.  En el grupo **Configurar Firewall de Windows** , elige las redes a las que desea permitir conexiones. Solo se habilitan las redes a las que el dispositivo está conectado actualmente. Debes elegir al menos una red.  
  
3.  Elige **Configurar depuración remota** para establecer las opciones del firewall e iniciar el depurador remoto.  Abre el cuadro de diálogo **Monitor de depuración remota de Visual Studio** para conceder a los usuarios permisos a las herramientas remotas y establecer otras opciones avanzadas.  
  
4.  Aparece el cuadro de diálogo **Monitor de depuración remota de Visual Studio** . Puedes conceder a los usuarios permisos sobre las herramientas remotas y establecer otras opciones avanzadas de este cuadro de diálogo.  
  
##  <a name="BKMK_ConfigureRemoteDebugger"></a> Configurar el depurador remoto  
 Para modificar la configuración del depurador remoto puedes utilizar dos herramientas.  
  
1. En el menú **Herramientas** del **Monitor de depuración remota de Visual Studio**:  
  
   1.  Elige **Opciones** para cambiar el número de puerto, el modo de autenticación o el intervalo de tiempo de espera del depurador remoto.  
  
   2.  Elige **Permisos** para agregar o quitar usuarios que tengan permiso para la depuración remota.  
  
       > [!NOTE]
       >  Se deben conceder permisos a cada cuenta de usuario que depura de forma remota.  
  
   Para establecer opciones avanzadas del depurador remoto debes utilizar el **Asistente para configuración de Remote Debugger** . Para abrir el asistente, elige **Asistente para configuración de Remote Debugger** en la pantalla Inicio.  
  
2. En la página **Configurar el servicio de Visual Studio Remote Debugger** , puedes elegir que se ejecute el depurador remoto como un servicio. En la mayoría de los casos, la ejecución como un servicio no es necesaria.  
  
3. En la página **Configurar Firewall de Windows para depuración** puedes agregar o quitar el tipo de redes a las que deseas que se conecte el depurador remoto. Solo se habilitan las redes a las que el dispositivo está conectado actualmente. Debes elegir al menos una red.  
  
##  <a name="BKMK_ConnectVS"></a> Configurar el proyecto de Visual Studio para la depuración remota  
 Especifica el dispositivo remoto al que quieras conectarte en las propiedades del proyecto. El procedimiento varía según cuál sea el lenguaje de programación. Puedes escribir el nombre de red del dispositivo remoto, o bien seleccionarlo en el cuadro de diálogo Seleccionar conexión del depurador remoto.  
  
 ![Cuadro de diálogo Seleccionar conexión del depurador remoto](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 En el cuadro de diálogo se muestran solo los dispositivos que están en la subred local del equipo de Visual Studio y que ejecutan el depurador remoto.  
  
> [!TIP]
>  Si tienes dificultades para conectarte con un dispositivo remoto, intenta escribir la dirección IP del dispositivo. Para determinar la dirección IP de un dispositivo, abre una ventana de comandos y escribe **ipconfig**. La dirección IP aparece como **IPv4 Address**.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Elegir el dispositivo remoto para los proyectos de C# y Visual Basic  
 ![Administra las propiedades del proyecto para la depuración remota](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1.  En el Explorador de soluciones, selecciona el nombre del proyecto y elige **Propiedades** en el menú contextual.  
  
2.  Selecciona **Depurar**.  
  
3.  Elige **Equipo remoto** en la lista **Dispositivo de destino** .  
  
4.  Escribe el nombre de red del dispositivo remoto en el cuadro **Equipo remoto** o elige **Buscar** para elegir el dispositivo en el cuadro de diálogo **Seleccionar conexión del depurador remoto** .  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Elegir el dispositivo remoto para los proyectos de JavaScript y C++  
 ![C&#43; &#43; propiedades para la depuración remota del proyecto](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1.  En el Explorador de soluciones, selecciona el nombre del proyecto y elige **Propiedades** en el menú contextual.  
  
2.  Expande el nodo **Propiedades de configuración** y selecciona **Depuración**.  
  
3.  Elige **Depurador remoto** en la lista **Depurador para iniciar** .  
  
4.  Escribe el nombre de red del dispositivo remoto en el cuadro **Nombre de equipo** o bien elige la flecha abajo contigua para elegir el dispositivo en el cuadro de diálogo **Seleccionar conexión del depurador remoto** .  
  
##  <a name="BKMK_RunRemoteDebug"></a> Ejecutar una sesión de depuración remota  
 Una sesión de depuración remota se inicia, se detiene y se navega por ella de la misma forma que una sesión local. Antes de iniciar la depuración, asegúrate de que el Monitor de depuración remota se ejecute en el dispositivo remoto.  
  
 A continuación, elige **Iniciar depuración** en el menú **Depurar** (teclado: F5). El proyecto se recompila. Luego, se implementa e inicia en el dispositivo remoto. El depurador suspende la ejecución en los puntos de interrupción. Puedes depurar paso a paso por instrucciones o por procedimientos y hasta salir del código. Elige **Detener depuración** para finalizar la sesión de depuración y cerrar la aplicación remota. Para obtener más información, consulte [depurar aplicaciones en Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también  
 [Probar aplicaciones de la Tienda con Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Depurar aplicaciones en Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)



