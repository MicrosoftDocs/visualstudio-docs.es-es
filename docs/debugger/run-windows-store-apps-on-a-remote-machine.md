---
title: Depuración de aplicaciones para UWP en máquinas remotas | Microsoft Docs
description: Consulte cómo usar Visual Studio para ejecutar, depurar y probar una aplicación de la Plataforma universal de Windows (UWP), además de generar perfiles para ella, en otro equipo o dispositivo de forma remota.
ms.custom: SEO-VS-2020
ms.date: 10/05/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: f75c1c2420a356a38148f67daab05eadf5a073e6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881326"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Depuración de aplicaciones para UWP en máquinas remotas desde Visual Studio

Puede usar Visual Studio para ejecutar, depurar y probar una aplicación de la Plataforma universal de Windows (UWP), además de generar perfiles para ella, en otro equipo o dispositivo. Ejecutar la aplicación para UWP en una máquina remota es especialmente útil cuando el equipo de Visual Studio no admite la funcionalidad específica de UWP, como la entrada táctil, la ubicación geográfica o la orientación física.

## <a name="prerequisites"></a><a name="BKMK_Prerequisites"></a> Requisitos previos

Para depurar una aplicación para UWP en un dispositivo remoto desde Visual Studio:

- El proyecto de Visual Studio debe estar configurado para la depuración remota.
- La máquina remota y el equipo de Visual Studio se deben conectar a través de una red o directamente mediante un cable USB o Ethernet. No se admite la depuración a través de Internet.
- Debe [activar el modo de desarrollador](/windows/uwp/get-started/enable-your-device-for-development) tanto en el equipo de Visual Studio como en la máquina remota.
- Los equipos remotos deben ejecutar las Herramientas remotas para Visual Studio.
  - Algunas versiones de Windows 10 inician y ejecutan automáticamente las herramientas remotas. Si no es así, [instale y ejecute las Herramientas remotas para Visual Studio](#BKMK_download).
  - Los dispositivos Windows Mobile 10 no necesitan ni admiten las herramientas remotas.

## <a name="configure-a-visual-studio-project-for-remote-debugging"></a><a name="BKMK_ConnectVS"></a> Configuración de un proyecto de Visual Studio para la depuración remota
<a name="BKMK_DirectConnect"></a> Usará la página **Propiedades** del proyecto para especificar el dispositivo al que conectarse. La configuración varía en función del lenguaje de programación.

> [!CAUTION]
> De forma predeterminada, la página de propiedades establece **Universal (protocolo sin cifrar)** como **Tipo de autenticación** para las conexiones remotas de Windows 10. Es posible que deba establecer **Sin autenticación** para conectarse al depurador remoto. Los protocolos **Universal (protocolo sin cifrar)** y **Sin autenticación** no disponen de seguridad de red, por lo que los datos que se pasan entre las máquinas de desarrollo y remotas son vulnerables. Elija estos tipos de autenticación solo con redes de confianza que esté seguro de que no corren peligro debido a tráfico hostil o malintencionado.
>
>Si elige **Autenticación de Windows** como **Tipo de autenticación**, tendrá que iniciar sesión en la máquina remota durante la depuración. El depurador remoto también debe ejecutarse en modo de **Autenticación de Windows**, con la misma cuenta de usuario que en la máquina de Visual Studio.

### <a name="configure-a-c-or-visual-basic-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Configuración de un proyecto de C# o Visual Basic para la depuración remota

1. Seleccione el proyecto de C# o Visual Basic en el **Explorador de soluciones** de Visual Studio, seleccione el icono **Propiedades** y presione **Alt**+**Entrar** o haga clic con el botón derecho y seleccione **Propiedades**.

1. Seleccione la pestaña **Depurar**.

1. En **Dispositivo de destino**, seleccione **Máquina remota** si el equipo es remoto, o **Dispositivo** si se trata de un dispositivo de Windows Mobile 10 conectado directamente.

1. En el caso de una máquina remota, escriba el nombre o la dirección IP de la red en el campo **Máquina remota**, o bien seleccione **Buscar** para buscar el dispositivo en el [cuadro de diálogo Conexiones remotas](#remote-connections).

    ![Propiedades de proyectos administrados para la depuración remota](../debugger/media/vsrun_managed_projprop_remote.png "Propiedades del proyecto de depuración administrada")

### <a name="configure-a-c-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Configuración de un proyecto de C++ para la depuración remota

1. Seleccione el proyecto de C++ o Visual Studio en el **Explorador de soluciones**, elija el icono **Propiedades** y presione **Alt**+**Entrar** o haga clic con el botón derecho y seleccione **Propiedades**.

1. Seleccione la pestaña **Depuración**.

3. En **Depurador para iniciar**, seleccione **Máquina remota** si es un equipo remoto, o **Dispositivo** si se trata de un dispositivo Windows Mobile 10 conectado directamente.

1. En el caso de una máquina remota, escriba el nombre o la dirección IP de la red en el campo **Nombre de la máquina**, o baje y seleccione **Buscar** para buscar el dispositivo en el [cuadro de diálogo Conexiones remotas](#remote-connections).

    ![Propiedades del proyecto de C++ para la depuración remota](../debugger/media/vsrun_cpp_projprop_remote.png "Propiedades del proyecto de depuración de C++")

### <a name="use-the-remote-connections-dialog-box"></a><a name="remote-connections"></a> Uso del cuadro de diálogo Conexiones remotas

En el cuadro de diálogo **Conexiones remotas**, puede buscar una dirección IP o un nombre de equipo remoto específico o detectar las conexiones automáticamente seleccionando el icono de actualización de flecha redondeada. El cuadro de diálogo solo busca en los dispositivos de la subred local que ejecutan actualmente el depurador remoto. No todos los dispositivos se pueden detectar en el cuadro de diálogo **Conexiones remotas**.

 ![Cuadro de diálogo Conexión remota](../debugger/media/vsrun_selectremotedebuggerdlg.png "Cuadro de diálogo Conexiones remotas")

>[!TIP]
>Si no puede conectarse a un dispositivo remoto por nombre, pruebe a usar su dirección IP. Para determinar la dirección IP, en el dispositivo remoto, escriba **ipconfig** en una ventana de comandos. La dirección IP aparece como **Dirección IPv4**.

## <a name="download-and-install-the-remote-tools-for-visual-studio"></a><a name="BKMK_download"></a> Descargue e instale Herramientas remotas para Visual Studio

Para que Visual Studio depure aplicaciones en un equipo remoto, el equipo remoto debe ejecutar las Herramientas remotas para Visual Studio.

- Los dispositivos Windows Mobile 10 no necesitan ni admiten las herramientas remotas.
- Los equipos con Windows 10 que ejecutan Creator's Update (versión 1703) y versiones posteriores y los dispositivos de Windows 10 Xbox, IoT y HoloLens instalan las herramientas remotas automáticamente al implementar la aplicación.
- En los equipos con Windows 10 anteriores a Creator's Update, debe descargar, instalar y ejecutar manualmente las herramientas remotas en el equipo remoto antes de iniciar la depuración.

**Para descargar e instalar las herramientas remotas:**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="configure-the-remote-tools"></a><a name="BKMK_setup"></a> Configuración de las herramientas remotas

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

## <a name="debug-uwp-apps-remotely"></a><a name="BKMK_RunRemoteDebug"></a> Depuración remota de aplicaciones para UWP

La depuración remota funciona igual que la depuración local.

1. En las versiones de Windows 10 anteriores a Creator's Update, asegúrese de que el Monitor de depuración remota (*msvsmon.exe*) se está ejecutando en el dispositivo remoto.

1. En el equipo de Visual Studio, asegúrese de que el destino de depuración correcto (**Máquina remota** o **Dispositivo**) aparezca junto a la flecha verde en la barra de herramientas.

1. Para iniciar la depuración, seleccione **Depurar** > **Iniciar depuración** y presione **F5** o seleccione la flecha verde en la barra de herramientas.

   El proyecto se vuelve a compilar y, luego, se implementa y se inicia en el dispositivo remoto. El depurador suspende la ejecución en los puntos de interrupción y puede depurar paso a paso por instrucciones o por procedimientos y hasta salir del código.

1. Si es necesario, seleccione **Depurar** > **Detener depuración** o presione **Mayús**+**F5** para detener la depuración y cerrar la aplicación remota.

## <a name="see-also"></a>Vea también
- [Opciones avanzadas de implementación remota](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Prueba de aplicaciones para UWP con Visual Studio](../test/unit-test-your-code.md)
- [Depuración de aplicaciones para UWP en Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
