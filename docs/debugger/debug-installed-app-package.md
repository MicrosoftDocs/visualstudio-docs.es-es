---
title: Depuración de un paquete de aplicaciones para UWP instalado | Microsoft Docs
ms.custom: ''
ms.date: 11/07/2018
ms.topic: how-to
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
ms.openlocfilehash: eabc694665bede7d193a360a01c42366568e33c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350737"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Depuración de un paquete de aplicaciones para UWP instalado en Visual Studio

Visual Studio puede depurar paquetes de aplicaciones para Plataforma universal de Windows (UWP) instalados en equipos con Windows 10 y dispositivos Xbox, HoloLens e IoT.

>[!NOTE]
>No se admite la depuración de Visual Studio en aplicaciones para UWP instaladas en teléfonos.

Para más información sobre la depuración de aplicaciones para UWP, vea las entradas de blog sobre [depuración de paquetes de aplicaciones instalados](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) y [compilación de aplicaciones universales de Windows (UWP)](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>Depuración de una aplicación de UWP instalada en una máquina local

1. En Visual Studio, seleccione **Depurar** > **Otros destinos de depuración** > **Depurar paquete de aplicaciones instalado**.

1. En el cuadro de diálogo **Depurar paquete de aplicaciones instalado**, en **Tipo de conexión**, seleccione **Máquina local**.

1. En **Paquetes de aplicaciones instalados**, seleccione la aplicación que quiere depurar o escriba su nombre en el cuadro de búsqueda. Los paquetes de aplicaciones instalados que no se están ejecutando aparecen en **No están en ejecución** y las aplicaciones que se están ejecutando se encuentran en **En ejecución**.

   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

1. Si es necesario, cambie el tipo de código en **Depurar este tipo de código** y seleccione otras opciones.
   - Seleccione **No iniciar, pero depurar mi código al empezar** para empezar la depuración cuando se inicie la aplicación. Empezar la depuración cuando se inicia la aplicación es una manera eficaz de depurar las rutas de acceso de control desde [diferentes métodos de inicio](/windows/uwp/xbox-apps/automate-launching-uwp-apps), como la activación del protocolo con parámetros personalizados.

1. Seleccione **Iniciar** o, si la aplicación se está ejecutando, seleccione **Asociar**.

> [!NOTE]
> También puede asociar a cualquier UWP que se esté ejecutando o a otro proceso de aplicación si selecciona **Depurar** > **Asociar al proceso** en Visual Studio. No es necesario que el proyecto original de Visual Studio se asocie a un proceso en ejecución, pero la carga de los símbolos de la aplicación le ayudará de forma significativa al depurar un proceso para el que no tiene el código original. Vea [Especificar archivos de código fuente y símbolos (.pdb) en el depurador de Visual Studio (C#, C++, Visual Basic, F#)](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="debug-an-installed-uwp-app-on-a-remote-computer-or-device"></a><a name="remote"></a> Depurar una aplicación de UWP instalada en un equipo o dispositivo remoto

La primera vez que Visual Studio depura una aplicación de UWP instalada en un dispositivo de Windows 10 o un equipo de Windows 10 de actualización posterior al creador remoto, instala las herramientas de depuración remota en el dispositivo de destino.

1. [Habilite el modo de desarrollador](/windows/uwp/get-started/enable-your-device-for-development) en el equipo de Visual Studio y en el dispositivo o equipo remoto.

1. Si se va a conectar a un equipo remoto que ejecuta Windows 10 de actualización anterior al creador, [instale e inicie manualmente el depurador remoto](../debugger/remote-debugging.md) en el equipo remoto.

1. En el equipo con Visual Studio, seleccione **Depurar** > **Otros destinos de depuración** > **Depurar paquete de aplicaciones instalado**.

1. En el cuadro de diálogo **Depurar paquete de aplicaciones instalado**, en **Tipo de conexión**, seleccione **Máquina local** o **Dispositivo**.

   Si selecciona **Dispositivo**, el equipo debe estar conectado físicamente a un dispositivo de Windows 10.

   En el caso de una máquina remota, si la dirección del equipo no aparece junto a **Dirección**, seleccione **Cambiar**.

   1. En el cuadro de diálogo **Conexión remota**, junto a **Dirección**, escriba el nombre o la dirección IP del equipo al que quiere conectarse.

      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

      Si el depurador no se puede conectar a un equipo remoto con el nombre de equipo, use entonces la dirección IP. Use la dirección IP de los dispositivos Xbox, HoloLens o IoT.
   1. Seleccione una opción de autenticación junto a **Modo de autenticación**.

      Para la mayoría de las aplicaciones, conserve el valor predeterminado **Universal (protocolo sin cifrar)** .
   1. Elija **Seleccionar**.

1. En **Paquetes de aplicaciones instalados**, seleccione la aplicación que quiere depurar o escriba su nombre en el cuadro de búsqueda. Los paquetes de aplicaciones instalados que no se están ejecutando aparecen en **No están en ejecución** y las aplicaciones que se están ejecutando se encuentran en **En ejecución**.

1. Si es necesario, cambie el tipo de código en **Depurar este tipo de código** y seleccione otras opciones.
   - Seleccione **No iniciar, pero depurar mi código al empezar** para empezar la depuración cuando se inicie la aplicación. Empezar la depuración cuando se inicia la aplicación es una manera eficaz de depurar las rutas de acceso de control desde [diferentes métodos de inicio](/windows/uwp/xbox-apps/automate-launching-uwp-apps), como la activación del protocolo con parámetros personalizados.

1. Seleccione **Iniciar** o, si la aplicación se está ejecutando, seleccione **Asociar**.

Cuando inicia la depuración de un paquete de aplicaciones instalado en un dispositivo Xbox, HoloLens o IoT conectado por primera vez, Visual Studio instala la versión correcta del depurador remoto para el dispositivo de destino. La instalación del depurador remoto puede tardar algún tiempo y el mensaje **Iniciando el depurador remoto** se muestra mientras se está produciendo.

>[!NOTE]
>Actualmente, un dispositivo Xbox u HoloLens reinicia la aplicación con el depurador asociado si ya se estaba ejecutando.

Para más información sobre la implementación remota de aplicaciones para UWP, vea [Implementación y depuración de aplicaciones para UWP](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) y [Depuración de aplicaciones para UWP en máquinas remotas](run-windows-store-apps-on-a-remote-machine.md).

## <a name="see-also"></a>Vea también

- [Depurar en Visual Studio](../debugger/index.yml)
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
- [Depuración remota](../debugger/remote-debugging.md)
- [Configuración del Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Asignaciones de puerto del depurador remoto](../debugger/remote-debugger-port-assignments.md)
- [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)