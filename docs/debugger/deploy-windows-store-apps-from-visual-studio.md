---
title: Implementar aplicaciones UWP desde Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 01/16/2018
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
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 28b1897fad45ae0c2bd174c39433645caf011f09
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2018
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Implementar aplicaciones UWP desde Visual Studio
  
 La funcionalidad de implementación de Visual Studio crea y registra aplicaciones para UWP que se crean con Visual Studio en un dispositivo de destino. El modo en que se registra la aplicación depende de si el dispositivo de destino es local o remoto.  
  
-   Cuando el destino es un equipo local de Visual Studio, Visual Studio registra la aplicación desde su carpeta de compilación.  
  
-   Cuando el destino es un dispositivo remoto, Visual Studio copia los archivos necesarios en el equipo remoto y registra la aplicación en ese dispositivo.  
  
 Implementación es automática cuando se depura la aplicación desde Visual Studio mediante el **Iniciar depuración** opción (teclado: F5) o el **iniciar sin depurar** opción (teclado: CTRL + F5). También puede implementar la aplicación manualmente. La implementación manual es útil en los siguientes casos:  
  
-   Pruebas ad hoc en un equipo local o remoto.  
  
-   Implementación de una aplicación que iniciará otra aplicación que querrá depurar.  
  
-   Implementación de una aplicación que se depurará cuando la inicie otra aplicación u otro método.
  
##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a>Cómo implementar una aplicación de UWP  
 La implementación manual de una aplicación es un proceso simple:  
  
1.  Si implementa a un dispositivo remoto, especifique el nombre o la dirección IP del dispositivo en la página de proyecto de la propiedad del proyecto de inicio de la aplicación. Los pasos necesarios se mencionan más adelante dentro de este tema.  
  
2.  En la barra de herramientas de Visual Studio del depurador, seleccione el destino de la implementación en la lista desplegable que hay junto al botón **Iniciar depuración** .  
  
     ![Ejecutar en el equipo Local](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")  
  
3.  En el menú **Compilar** , elija **Implementar**  
  
##  <a name="BKMK_How_to_specify_a_remote_device"></a> Cómo especificar un dispositivo remoto  

**Requisitos previos**  
  
En un dispositivo remoto de Windows 10, debe habilitar [modo de programador](/windows/uwp/get-started/enable-your-device-for-development). En dispositivos Windows 10 que ejecutan la actualización del creador o versiones posteriores, las herramientas remotas se instalan automáticamente al implementar la aplicación. Para obtener más información, consulte [depurar un paquete de aplicación instalados](../debugger/debug-installed-app-package.md).

> [!NOTE]
> En versiones de actualización del creador anterior de Windows 10, las herramientas remotas para Visual Studio debe instalarse en el dispositivo remoto y el depurador remoto debe estar ejecutándose.
  
En la implementación se usa el canal de la red del depurador remoto para enviar los archivos de aplicación al dispositivo remoto.  
  
#### <a name="to-specify-a-remote-device"></a>Para especificar un dispositivo remoto  
  
1.  En la página de propiedades de depuración del proyecto de inicio, especifique el nombre o la dirección IP de un dispositivo de implementación remoto.  
  
2.  Para abrir la página de propiedades de depuración, elija el proyecto en el Explorador de soluciones y, luego, seleccione **Propiedades** en el menú contextual.  
  
3.  A continuación, elija el nodo **Depurar** en la ventana de las páginas de propiedad.

4. Para **dispositivo de destino**, seleccione **equipo remoto**.

5. En **equipo remoto**, haga clic en **buscar**.
  
4.  Puede escribir el nombre o dirección IP del dispositivo remoto, o puede elegir el dispositivo en el **conexión remota** cuadro de diálogo.  
  
     ![Cuadro de diálogo Seleccionar conexión del depurador remoto](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
     El **conexión remota** cuadro de diálogo muestra los dispositivos en la subred local y cualquier dispositivo que esté conectado directamente al equipo de Visual Studio mediante un cable Ethernet.  
  
 **Cómo especificar el dispositivo remoto en una página de proyecto de JavaScript o Visual C++**  
  
 ![C &#43; &#43; proyectar las propiedades para la depuración remota](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1.  Elige **Depurador remoto** en la lista **Depurador para iniciar** .  
  
2.  Especifique el nombre de la red del dispositivo remoto en el cuadro **Nombre de equipo** . O bien puede seleccionar la flecha abajo del cuadro para seleccionar el dispositivo desde el cuadro de diálogo Seleccionar conexión del depurador remoto.  
  
 **Cómo especificar el dispositivo remoto en una página de proyecto de Visual C# y Visual Basic**  
  
 ![Administrar propiedades del proyecto para la depuración remota](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1.  Elige **Equipo remoto** en la lista **Dispositivo de destino** .  
  
2.  Escribe el nombre de red del dispositivo remoto en el cuadro **Equipo remoto** o haz clic en **Buscar** para elegir el dispositivo en el cuadro de diálogo **Seleccionar conexión del depurador remoto** .  
  
##  <a name="BKMK_Deployment_options"></a> Opciones de implementación  
 Puede establecer las siguientes opciones de implementación en la página de propiedades de depuración del proyecto de inicio.  
  
 **Permitir bucle invertido de red**  
 Por motivos de seguridad, un UWP o [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] no se permiten realizar llamadas de red para el dispositivo está instalado en las aplicaciones instaladas en la manera estándar. De forma predeterminada, la implementación de Visual Studio crea una exención respecto a esta regla para la aplicación implementada. Esta exención te permite probar procedimientos de comunicación en un mismo equipo. Antes de enviar su aplicación a la [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)], debe probarla sin la exención.  
  
 Para quitar la exención de bucle invertido de red en la aplicación:  
  
-   En C# y en la página de propiedades de depuración de VB, desactive la casilla **Permitir bucle invertido de red** .  
  
-   En JavaScript y en la página de propiedades de depuración, establezca el valor de **Permitir bucle invertido de red** en **No**.  
  
 **No iniciar, pero depurar mi código al empezar (C# y VB)/Iniciar aplicación (JavaScript y C++)**  
 Para configurar el inicio automático de una sesión de depuración en la implementación cuando se inicie la aplicación:  
  
-   En C# y en la página de depuración de VB, active la casilla **No iniciar, pero depurar mi código al empezar** .  
  
-   En JavaScript y en la página de propiedades de depuración, establezca el valor de **Iniciar aplicación** en **Sí**.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de implementación remota avanzada](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)  
 [Depurar un paquete de aplicación instalada](../debugger/debug-installed-app-package.md)   
 [Ejecutar aplicaciones desde Visual Studio](../debugger/run-store-apps-from-visual-studio.md)