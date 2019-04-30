---
title: Depurar un paquete de aplicación para UWP instalado | Microsoft Docs
ms.custom: ''
ms.date: 11/07/2018
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
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 4bf9306ea1604d032ce9f4436759b11c4d17c343
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62563186"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Depurar un paquete de aplicación para UWP instalado en Visual Studio

Visual Studio puede depurar paquetes de aplicación plataforma Universal de Windows (UWP) instalados en equipos de Windows 10 y dispositivos IoT, Xbox y HoloLens.

>[!NOTE]
>No se admite la depuración para aplicaciones UWP instaladas de Visual Studio en teléfonos.

Para obtener más información sobre la depuración de aplicaciones para UWP, vea las entradas de blog en [depuración instalado paquetes de aplicaciones](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) y [compilar las aplicaciones universales de Windows (UWP)](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>Depurar una aplicación para UWP instalada en un equipo local

1. En Visual Studio, seleccione **depurar** > **otros destinos de depuración** > **depurar paquete de aplicaciones instalado**.

1. En el **depurar paquete de aplicaciones instalado** cuadro de diálogo, en **tipo de conexión**, seleccione **máquina Local**.

1. En **paquetes de aplicaciones instalados**, seleccione la aplicación que desea depurar, o escriba su nombre en el cuadro de búsqueda. Paquetes de aplicaciones instaladas de ejecución no aparecen en **no se está ejecutando**, y ejecución de aplicaciones se encuentran en **ejecutando**.

   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

1. Si es necesario, cambie el tipo de código en **depurar este tipo de código**y seleccionar otras opciones.
   - Seleccione **no iniciar, pero depurar mi código al empezar** para iniciar la depuración cuando se inicia la aplicación. Iniciar la depuración cuando se inicia la aplicación es una forma eficaz para depurar las rutas de acceso de control de [métodos de inicio diferentes](/windows/uwp/xbox-apps/automate-launching-uwp-apps), como la activación de protocolos con parámetros personalizados.

1. Seleccione **iniciar**, o si está ejecutando la aplicación, seleccione **adjuntar**.

> [!NOTE]
> También puede adjuntar a cualquier ejecución UWP u otro proceso de la aplicación seleccionando **depurar** > **asociar al proceso** en Visual Studio. No es necesario el proyecto original de Visual Studio para adjuntar a un proceso en ejecución, pero la carga de símbolos de la aplicación ayudará significativamente al depurar un proceso que no tiene el código original. Consulte [especificar archivos de símbolos y de origen en el depurador](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="remote"></a> Depurar una aplicación para UWP instalada en un equipo o dispositivo remoto

La primera vez que Visual Studio depura una aplicación para UWP instalada en un dispositivo Windows 10 o equipo de un remoto-creador de la publicación actualización de Windows 10, instala las herramientas de depuración remotas en el dispositivo de destino.

1. [Habilitar el modo de programador](/windows/uwp/get-started/enable-your-device-for-development) en el equipo de Visual Studio y el dispositivo o equipo remoto.

1. Si se conecta a un equipo remoto que ejecutan Windows 10 de pre-Creators Update, [manualmente, instale e inicie el depurador remoto](../debugger/remote-debugging.md) en el equipo remoto.

1. En el equipo de Visual Studio, seleccione **depurar** > **otros destinos de depuración** > **depurar paquete de aplicaciones instalado**.

1. En el **depurar paquete de aplicaciones instalado** cuadro de diálogo, en **tipo de conexión**, seleccione **máquina remota** o **dispositivo**.

   Si selecciona **dispositivo**, el equipo debe estar conectado físicamente a un dispositivo Windows 10.

   Para un equipo remoto, si la dirección del equipo no aparece junto a **dirección**, seleccione **cambio**.

   1. En el **conexión remota** cuadro de diálogo, junto a **dirección**, escriba el nombre o dirección IP del equipo que desea conectarse.

      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

      Si el depurador no puede conectarse a un equipo remoto mediante el nombre del equipo, use la dirección IP en su lugar. Use la dirección IP para dispositivos de IoT, HoloLens o Xbox.
   1. Seleccione una opción de autenticación junto a **modo de autenticación**.

      Para la mayoría de las aplicaciones, mantenga el valor predeterminado, **Universal (protocolo sin cifrar)**.
   1. Seleccione **seleccione**.

1. En **paquetes de aplicaciones instalados**, seleccione la aplicación que desea depurar, o escriba su nombre en el cuadro de búsqueda. Paquetes de aplicaciones instaladas de ejecución no aparecen en **no se está ejecutando**, y ejecución de aplicaciones se encuentran en **ejecutando**.

1. Si es necesario, cambie el tipo de código en **depurar este tipo de código**y seleccionar otras opciones.
   - Seleccione **no iniciar, pero depurar mi código al empezar** para iniciar la depuración cuando se inicia la aplicación. Iniciar la depuración cuando se inicia la aplicación es una forma eficaz para depurar las rutas de acceso de control de [métodos de inicio diferentes](/windows/uwp/xbox-apps/automate-launching-uwp-apps), como la activación de protocolos con parámetros personalizados.

1. Seleccione **iniciar**, o si está ejecutando la aplicación, seleccione **adjuntar**.

Al iniciar la depuración de un paquete de aplicación instalada en un dispositivo conectado Xbox, HoloLens o IoT por primera vez, Visual Studio instala la versión correcta del depurador remoto para el dispositivo de destino. Instalar el depurador remoto puede tardar algún tiempo y el mensaje **iniciando el depurador remoto** muestra mientras está ocurriendo.

>[!NOTE]
>Actualmente, un dispositivo Xbox o HoloLens reinicia la aplicación con el depurador adjuntado si ya se estaba ejecutando.

Para obtener más información sobre la implementación remota de aplicaciones para UWP, consulte [implementar y depurar aplicaciones UWP](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) y [UWP depurar aplicaciones en equipos remotos](run-windows-store-apps-on-a-remote-machine.md).

## <a name="see-also"></a>Vea también

- [Depurar en Visual Studio](../debugger/index.md)
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
- [Depuración remota](../debugger/remote-debugging.md)
- [Configuración del Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Asignaciones de puerto del depurador remoto](../debugger/remote-debugger-port-assignments.md)
- [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)