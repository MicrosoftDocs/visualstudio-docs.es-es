---
title: "Depurar un paquete de aplicación instalada (UWP) | Documentos de Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 07/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords: app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: e21d29c3a95de4e5174a9966665f3e4e6781f726
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="debug-an-installed-app-package-in-visual-studio-uwp"></a>Depurar un paquete de aplicación instalada en Visual Studio (UWP)

Puede depurar cualquier paquete de aplicación instalada, haga clic en **Depurar > otros destinos de depuración > Depurar paquete de aplicaciones instalado**. Este método de depuración está disponible para aplicaciones universales de Windows (UWP) en estos dispositivos:

* Windows 10 (no se admite en teléfonos)
* XBox
* HoloLens
* IoT

Para obtener más información acerca de estas características, consulte la entrada de blog en las actualizaciones de [depuración de paquetes de aplicación instalados](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) y la publicación en [generar aplicaciones universales de Windows (UWP)](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-app-package-or-running-app-on-a-local-machine-or-device"></a>Depurar un paquete de aplicación instalada o una aplicación en ejecución en un equipo Local o un dispositivo

1. Con el proyecto UWP abierto en Visual Studio, haga clic en **Depurar > otros destinos de depuración > Depurar paquete de aplicaciones instalado**.

2. Seleccione **equipo Local** o **dispositivo**.

     Si elige **dispositivo**, el equipo debe estar conectado físicamente a un dispositivo Windows 10.

     ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

     Está ejecutando actualmente instalado app paquetes aparecen bajo la **ejecutando** nodo. Instalar paquetes de aplicaciones que no están ejecutando mostrar una **no se está ejecutando**.

3. Seleccione el nombre de la aplicación que desea depurar en **ejecutando** o **no se está ejecutando** y elija **iniciar** o bien, si la aplicación ya se está ejecutando, elija **adjuntar**.

     Si selecciona **no iniciar, pero depurar mi código al empezar**, esto hará que el depurador de Visual Studio adjuntar a la aplicación cuando se inicia en uno personalizado. Se trata de una manera eficaz para depurar las rutas de acceso de control de [métodos de inicio diferentes](/windows/uwp/xbox-apps/automate-launching-uwp-apps), como la activación de protocolo con parámetros personalizados.

> [!NOTE]
> Visual Studio también puede conectarse a cualquier proceso de aplicación UWP ejecución seleccionando **depurar**y, a continuación, **adjuntar al proceso**. Adjuntar a un proceso en ejecución no requiere el proyecto de Visual Studio original, pero la carga de símbolos del proceso le ayudarán a significativamente cuando se depura un proceso que no tiene el código original de.
  
## <a name="remote"></a>Depurar una aplicación instalada o se está ejecutando en un equipo remoto 

Cuando se depura un paquete de aplicación instalada en un equipo remoto por primera vez, Visual Studio instala la versión correcta de las herramientas remotas para el dispositivo de destino. El dispositivo de destino debe ser un equipo Windows 10, XBox, HoloLens o IoT dispositivo.

1. En el dispositivo Windows 10, habilite [modo de programador](/windows/uwp/get-started/enable-your-device-for-development).

2. Si se conecta a un equipo remoto que ejecuta una versión de actualización del creador anterior de Windows 10, primero manualmente [instalar e iniciar el depurador remoto](../debugger/remote-debugging.md).

     Para un dispositivo de XBox, HoloLens o IoT y dispositivos de Windows que ejecutan la actualización del creador de Windows 10, no es necesario instalar manualmente el depurador remoto. Las herramientas remotas se instalará automáticamente al implementar la aplicación.

3. Haga clic en **Depurar > otros destinos de depuración > depuración instalado el paquete de la aplicación**.

4. En la primera lista desplegable, elija **equipo remoto**.

5. Escriba el nombre o dirección IP del equipo que desea adjuntar a.

     ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

     Si no se puede conectar con el nombre de equipo (después de elegir **iniciar**), utilice en su lugar la dirección IP. Utilice la dirección IP para dispositivos de IoT, HoloLens o XBox.

5. Elija cómo autenticar seleccionando una opción en **modo de autenticación**.

    Para la mayoría de las aplicaciones, mantenga el valor predeterminado, **Universal (protocolo sin cifrar)**.

6. Seleccione el nombre de la aplicación que desea depurar en **ejecutando** o **no se está ejecutando** y elija **iniciar** o (en caso de aplicaciones en ejecución) **adjuntar**.

     Si selecciona **no iniciar, pero depurar mi código al empezar**, esto hará que el depurador de Visual Studio se asocie al paquete de aplicación cuando se inicia en uno personalizado. Se trata de una manera eficaz para depurar las rutas de acceso de control de [métodos de inicio diferentes](/windows/uwp/xbox-apps/automate-launching-uwp-apps), como la activación de protocolo con parámetros personalizados.

     Cuando se depura un paquete de aplicación instalados en un dispositivo conectado de XBox, HoloLens o IoT por primera vez, Visual Studio instala la versión correcta del depurador remoto para el dispositivo de destino. Esta operación puede tardar un poco de tiempo y verá un mensaje ``Starting remote debugger`` mientras se está teniendo lugar.

     > [!NOTE]
> Al presentar una XBox o dispositivo HoloLens reiniciará la aplicación con el depurador adjuntado si ya se está ejecutando.

> [!NOTE]
> Aplicaciones UWP se pueden desarrollar y compilan en Windows 8.1 o posterior, pero requieren 10 de Windows ejecutar. Si está desarrollando una aplicación de UWP en un equipo con Windows 8.1, puede depurar de forma remota una aplicación UWP que se ejecuta en otro dispositivo de Windows 10, siempre que el equipo host y de destino están en la misma LAN. Para ello, descargue e instale las herramientas remotas para Visual Studio en ambos equipos. La versión instalada debe coincidir con la versión existente de Visual Studio que ha instalado, y la arquitectura que seleccione (x86, x 64) debe también coincidir con el de la aplicación de destino.

Para obtener información sobre las opciones avanzadas para la implementación remota de aplicaciones UWP, vea [implementar y depurar aplicaciones UWP](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps.md#advanced-remote-deployment-options). 
  
## <a name="see-also"></a>Vea también  
 [Depurar en Visual Studio](../debugger/index.md)  
 [Guía de características del depurador](../debugger/debugger-feature-tour.md)  
 [Depuración remota](../debugger/remote-debugging.md)  
 [Configurar el Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [Asignaciones de puertos del depurador remoto](../debugger/remote-debugger-port-assignments.md)  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)