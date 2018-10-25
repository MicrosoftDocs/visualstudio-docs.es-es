---
title: Depuración remota de un proyecto de Visual C++ | Microsoft Docs
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
ms.assetid: 8b8eca0d-122f-4eda-848a-cf0945f207d0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 4677380081aaa0ac79f589ea7594f19f78750613
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844112"
---
# <a name="remote-debugging-a-visual-c-project-in-visual-studio"></a>Un proyecto de Visual C++ en Visual Studio de depuración remota
Para depurar una aplicación de Visual Studio en otro equipo, instalar y ejecutar las herramientas remotas en el equipo donde se implementará la aplicación, configure el proyecto para conectarse al equipo remoto desde Visual Studio y, a continuación, implementar y ejecutar la aplicación.

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

## <a name="remote_cplusplus"></a> Depuración remota de un proyecto de Visual C++  
 En el siguiente procedimiento, el nombre y ruta de acceso del proyecto es C:\remotetemp\MyMfc y el nombre del equipo remoto es **MJO DL**.  
  
1. Crear una aplicación MFC denominada **mymfc.**  
  
2. Establecer un punto de interrupción en alguna parte de la aplicación que esté fácilmente accesible, por ejemplo en **MainFrm.cpp**, al principio de `CMainFrame::OnCreate`.  
  
3. En el Explorador de soluciones, haga doble clic en el proyecto y seleccione **propiedades**. Abra el **depuración** ficha.  
  
4. Establecer el **depurador para iniciar** a **depurador remoto de Windows**.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Realice los siguientes cambios de las propiedades:  
  
   |Parámetro|Valor|
   |-|-|  
   |Comando remoto|C:\remotetemp\mymfc.exe|  
   |Directorio de trabajo|C:\remotetemp|  
   |Nombre de servidor remoto|Lista de distribución MJO:*númeroDePuerto*|  
   |Conexión|Remoto con autenticación de Windows|  
   |Tipo de depurador|Solo nativo|  
   |Directorio de implementación|C:\remotetemp.|  
   |Archivos adicionales para implementar|C:\data\mymfcdata.txt.|  
  
    Si implementa archivos adicionales (opcionales), la carpeta debe existir en ambos equipos.  
  
6. En el Explorador de soluciones, haga clic en la solución y elija **Configuration Manager**.  
  
7. Para el **depurar** configuración, seleccione el **implementar** casilla de verificación.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Iniciar la depuración (**Depurar > Iniciar depuración**, o **F5**).  
  
9. El archivo ejecutable se implementa automáticamente en el equipo remoto.  
  
10. Si se le solicite, escriba las credenciales de red para conectarse a la máquina remota.  
  
     Las credenciales necesarias son específicas de la configuración de seguridad de su red. Por ejemplo, en un equipo de dominio, puede elegir un certificado de seguridad o escriba su nombre de dominio y contraseña. En un equipo que no sea de dominio, puede escribir el nombre del equipo y un nombre de cuenta de usuario válido, como <strong>MJO-DL\name@something.com</strong>, junto con la contraseña correcta.  
  
11. En el equipo de Visual Studio, verá que la ejecución se detiene en el punto de interrupción.  
  
    > [!TIP]
    >  De manera alternativa, puede implementar los archivos como un paso independiente. En el **el Explorador de soluciones,** haga clic en el **mymfc** nodo y, a continuación, elija **implementar**.  
  
    Si tiene archivos de código que debe usar la aplicación, deberá incluirlos en el proyecto de Visual Studio. Cree una carpeta de proyecto para los archivos adicionales (en el **el Explorador de soluciones**, haga clic en **Agregar > nueva carpeta**.) A continuación, agregue los archivos a la carpeta (en el **el Explorador de soluciones**, haga clic en **Agregar > elemento existente**, a continuación, seleccione los archivos). En el **propiedades** para cada archivo, establezca **Copy to Output Directory** a **copiar siempre**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Configurar la depuración con símbolos remotos 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)] 
  
## <a name="see-also"></a>Vea también  
 [Depurar en Visual Studio](../debugger/index.md)  
 [Guía de características del depurador](../debugger/debugger-feature-tour.md)   
 [Configurar el Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [Depuración remota de ASP.NET en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)