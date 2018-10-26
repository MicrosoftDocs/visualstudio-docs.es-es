---
title: Depuración de un paquete de aplicación instalada (UWP) | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 07/17/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 3bb858f2ee20eb65c09dd4979f2bbba1470cbe0d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908254"
---
# <a name="debug-an-installed-app-package-in-visual-studio-uwp"></a>Depuración de un paquete de aplicación instalada en Visual Studio (UWP)

Puede depurar cualquier paquete de aplicación instalada, haga clic en **Depurar > otros destinos de depuración > Depurar paquete de aplicaciones instalado**. Este método de depuración está disponible para las aplicaciones universales de Windows (UWP) en estos dispositivos:

* Windows 10 (no se admite en los teléfonos)
* XBox
* HoloLens
* IoT

Para obtener más información acerca de estas características, consulte la entrada de blog sobre las actualizaciones para [depuración instalado paquetes de aplicaciones](https://blogs.msdn.microsoft.com/devops/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) y la publicación en [compilar las aplicaciones universales de Windows (UWP)](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-app-package-or-running-app-on-a-local-machine-or-device"></a>Depurar una aplicación en ejecución en un dispositivo o equipo Local o paquete de aplicaciones instalado

1. Con el proyecto UWP abierto en Visual Studio, haga clic en **Depurar > otros destinos de depuración > Depurar paquete de aplicaciones instalado**.

2. Seleccione **máquina Local** o **dispositivo**.

     Si elige **dispositivo**, el equipo debe estar conectado físicamente a un dispositivo Windows 10.

     ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

     Está ejecutando actualmente instalado app paquetes aparecen bajo el **ejecutando** nodo. Instala los paquetes de aplicaciones que no se ejecutan show copia **no se está ejecutando**.

3. Seleccione el nombre de la aplicación que desea depurar en **ejecutando** o **no se está ejecutando** y elija **iniciar** o bien, si la aplicación ya se está ejecutando, elija **adjuntar**.

     Si selecciona **no iniciar, pero depurar mi código al empezar**, esto hará que el depurador de Visual Studio adjuntar a la aplicación cuando se inicia a la vez personalizado. Esto es una forma eficaz para depurar las rutas de acceso de control de [métodos de inicio diferentes](/windows/uwp/xbox-apps/automate-launching-uwp-apps), como la activación de protocolos con parámetros personalizados.

> [!NOTE]
> Visual Studio también puede adjuntar a cualquier proceso en ejecución UWP app seleccionando **depurar**y, a continuación, **asociar al proceso**. Asociar a un proceso en ejecución no exigen que el proyecto de Visual Studio original, pero la carga de símbolos del proceso ayudará significativamente cuando se depura un proceso que no tiene el código original para.
  
## <a name="remote"></a> Depurar una aplicación instalada o se está ejecutando en un equipo remoto 

Al depurar un paquete de aplicación instalada en un equipo remoto por primera vez, Visual Studio instala la versión correcta de las herramientas remotas para el dispositivo de destino. El dispositivo de destino debe ser un equipo Windows 10, el dispositivo de IoT, HoloLens o XBox.

1. En el dispositivo Windows 10, habilite [modo de programador](/windows/uwp/get-started/enable-your-device-for-development).

2. Si se conecta a un equipo remoto que ejecuta versión de actualización del pre-creador de Windows 10, primero manualmente [instalar e iniciar el depurador remoto](../debugger/remote-debugging.md).

     Para un dispositivo de IoT, HoloLens o XBox y dispositivos de Windows que ejecutan Update Windows 10 Creators, no es necesario instalar manualmente el depurador remoto. Las herramientas remotas se instalará automáticamente al implementar la aplicación.

3. Haga clic en **Depurar > otros destinos de depuración > Depurar paquete de aplicaciones instalado**.

4. En la primera lista desplegable, elija **máquina remota**.

5. Escriba el nombre o dirección IP del equipo que desea asociar.

     ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

     Si no se puede adjuntar mediante nombre de equipo (después de elegir **iniciar**), use la dirección IP en su lugar. Use la dirección IP para dispositivos de IoT, HoloLens o XBox.

6. Elija cómo desea autenticar seleccionando una opción en **modo de autenticación**.

    Para la mayoría de las aplicaciones, mantenga el valor predeterminado, **Universal (protocolo sin cifrar)**.

7. Seleccione el nombre de la aplicación que desea depurar en **ejecutando** o **no se está ejecutando** y elija **iniciar** o (para ejecutar las aplicaciones) **adjuntar**.

     Si selecciona **no iniciar, pero depurar mi código al empezar**, esto hará que el depurador de Visual Studio adjuntar a su paquete de aplicación cuando se inicia a la vez personalizado. Esto es una forma eficaz para depurar las rutas de acceso de control de [métodos de inicio diferentes](/windows/uwp/xbox-apps/automate-launching-uwp-apps), como la activación de protocolos con parámetros personalizados.

     Al depurar un paquete de aplicación instalada en un dispositivo conectado XBox, HoloLens o IoT por primera vez, Visual Studio instala la versión correcta del depurador remoto para el dispositivo de destino. Esta operación puede tardar un poco de tiempo y verá un mensaje ``Starting remote debugger`` mientras esto ocurre.

     > [!NOTE]
   > En el presente, una consola XBox o dispositivo HoloLens reiniciará la aplicación con el depurador adjuntado si ya se está ejecutando.

Para obtener información sobre las opciones avanzadas para la implementación remota de aplicaciones para UWP, consulte [implementación y depuración apps]((/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) UWP. 
  
## <a name="see-also"></a>Vea también  
 [Depurar en Visual Studio](../debugger/index.md)  
 [Guía de características del depurador](../debugger/debugger-feature-tour.md)  
 [Remote Debugging](../debugger/remote-debugging.md)  
 [Configurar el Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [Asignaciones de puertos del depurador remoto](../debugger/remote-debugger-port-assignments.md)  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)