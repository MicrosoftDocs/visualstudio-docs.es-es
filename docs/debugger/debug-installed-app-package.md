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
ms.openlocfilehash: d5c2e94e9fa80145489bddfb005b7136bdff8a71
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211293"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Depurar un paquete de aplicación para UWP instalado en Visual Studio

Visual Studio puede depurar paquetes de aplicaciones Plataforma universal de Windows instalados (UWP) en equipos con Windows 10 y dispositivos Xbox, HoloLens y IoT.

>[!NOTE]
>No se admite la depuración de Visual Studio para aplicaciones UWP instaladas en teléfonos.

Para obtener más información sobre la depuración de aplicaciones para UWP, vea las entradas de blog sobre cómo [depurar paquetes de aplicaciones instalados](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) y [compilar aplicaciones universales de Windows (UWP)](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>Depurar una aplicación de UWP instalada en un equipo local

1. En Visual Studio >  **, seleccione Depurar****otros destinos** > de depuración**depurar paquete de aplicaciones instalado**.

1. En el cuadro de diálogo **depurar paquete de aplicaciones instalado** , en **tipo de conexión**, seleccione **equipo local**.

1. En **paquetes de aplicaciones instalados**, seleccione la aplicación que desea depurar o escriba su nombre en el cuadro de búsqueda. Los paquetes de aplicaciones instalados no en ejecución aparecen en **no en ejecución**y las aplicaciones en ejecución se están **ejecutando**.

   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

1. Si es necesario, cambie el tipo de código en **depurar este tipo de código**y seleccione otras opciones.
   - Seleccione no **iniciar, pero depurar mi código cuando comience** a iniciar la depuración cuando se inicie la aplicación. Iniciar la depuración cuando se inicia la aplicación es una manera eficaz de depurar las rutas de acceso de control de [diferentes métodos de inicio](/windows/uwp/xbox-apps/automate-launching-uwp-apps), como la activación del Protocolo con parámetros personalizados.

1. Seleccione **Inicio**, o bien, si la aplicación se está ejecutando, seleccione **adjuntar**.

> [!NOTE]
> También puede conectarse a cualquier UWP en ejecución u otro proceso de aplicación seleccionando **depurar** > **asociar al proceso** en Visual Studio. No es necesario que el proyecto original de Visual Studio se adjunte a un proceso en ejecución, pero la carga de los símbolos de la aplicación le ayudará de forma significativa al depurar un proceso para el que no tiene el código original. Vea [especificar archivos de símbolos y de origen en el depurador](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="remote"></a>Depurar una aplicación de UWP instalada en un equipo o dispositivo remoto

La primera vez que Visual Studio depura una aplicación de UWP instalada en un dispositivo de Windows 10 o un equipo de Windows 10 de actualización posterior al creador remoto, instala las herramientas de depuración remota en el dispositivo de destino.

1. [Habilite el modo de desarrollador](/windows/uwp/get-started/enable-your-device-for-development) en el equipo de Visual Studio y en el dispositivo o equipo remoto.

1. Si se está conectando a un equipo remoto que ejecuta Windows 10 de la actualización del creador anterior, [instale e inicie manualmente el depurador remoto](../debugger/remote-debugging.md) en el equipo remoto.

1. En el equipo de Visual Studio > , **Seleccione depurar****otros destinos** > de depuración**depurar paquete de aplicaciones instalado**.

1. En el cuadro de diálogo **depurar paquete de aplicaciones instalado** , en **tipo de conexión**, seleccione **equipo remoto** o **dispositivo**.

   Si selecciona **dispositivo**, el equipo debe estar conectado físicamente a un dispositivo de Windows 10.

   En el caso de una máquina remota, si la dirección del equipo no aparece junto a **Dirección**, seleccione **cambiar**.

   1. En el cuadro de diálogo **conexión remota** , junto a **Dirección**, escriba el nombre o la dirección IP del equipo al que desea conectarse.

      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

      Si el depurador no se puede conectar a un equipo remoto con el nombre de equipo, use la dirección IP en su lugar. Use la dirección IP de los dispositivos Xbox, HoloLens o IoT.
   1. Seleccione una opción de autenticación junto a **modo de autenticación**.

      Para la mayoría de las aplicaciones, conserve el valor predeterminado, **universal (protocolo sin cifrar)**.
   1. Seleccione **seleccionar**.

1. En **paquetes de aplicaciones instalados**, seleccione la aplicación que desea depurar o escriba su nombre en el cuadro de búsqueda. Los paquetes de aplicaciones instalados no en ejecución aparecen en **no en ejecución**y las aplicaciones en ejecución se están **ejecutando**.

1. Si es necesario, cambie el tipo de código en **depurar este tipo de código**y seleccione otras opciones.
   - Seleccione no **iniciar, pero depurar mi código cuando comience** a iniciar la depuración cuando se inicie la aplicación. Iniciar la depuración cuando se inicia la aplicación es una manera eficaz de depurar las rutas de acceso de control de [diferentes métodos de inicio](/windows/uwp/xbox-apps/automate-launching-uwp-apps), como la activación del Protocolo con parámetros personalizados.

1. Seleccione **Inicio**, o bien, si la aplicación se está ejecutando, seleccione **adjuntar**.

Cuando inicia la depuración de un paquete de la aplicación instalada en un dispositivo Xbox, HoloLens o IoT conectado por primera vez, Visual Studio instala la versión correcta del Depurador remoto para el dispositivo de destino. La instalación del Depurador remoto puede tardar algún tiempo y el mensaje que **inicia el depurador remoto** se muestra mientras se está produciendo.

>[!NOTE]
>Actualmente, un dispositivo de Xbox o HoloLens reinicia la aplicación con el depurador asociado si ya se estaba ejecutando.

Para obtener más información sobre la implementación remota de aplicaciones para UWP, consulte [implementación y depuración](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) de aplicaciones para UWP y [depuración de aplicaciones para UWP en máquinas remotas](run-windows-store-apps-on-a-remote-machine.md).

## <a name="see-also"></a>Vea también

- [Depurar en Visual Studio](../debugger/index.yml)
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
- [Depuración remota](../debugger/remote-debugging.md)
- [Configuración del Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Asignaciones de puerto del depurador remoto](../debugger/remote-debugger-port-assignments.md)
- [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)