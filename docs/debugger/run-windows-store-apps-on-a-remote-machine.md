---
title: Depurar aplicaciones para UWP en equipos remotos | Microsoft Docs
ms.date: 10/05/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 50d307cd65bfdf534b6ca3586e69bbc27be25e36
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62902901"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Depurar aplicaciones para UWP en equipos remotos desde Visual Studio

Puede usar Visual Studio para ejecutar, depurar, generar perfiles y probar una aplicación de plataforma Universal de Windows (UWP) en otro equipo o dispositivo. Ejecutando la aplicación para UWP en un equipo remoto es especialmente útil cuando el equipo de Visual Studio no admite la funcionalidad específica de UWP como táctil, ubicación geográfica o la orientación física.

## <a name="BKMK_Prerequisites"></a> Requisitos previos

Para depurar una aplicación para UWP en un dispositivo remoto desde Visual Studio:

- El proyecto de Visual Studio debe configurarse para la depuración remota.
- El equipo remoto y el equipo de Visual Studio deben conectados a través de una red o conectados directamente a través de un cable Ethernet o USB. No se admite la depuración a través de Internet.
- Debe [activar el modo de programador](/windows/uwp/get-started/enable-your-device-for-development) en el equipo de Visual Studio y el equipo remoto.
- Los equipos remotos deben ejecutar las herramientas remotas para Visual Studio.
  - Algunas versiones de Windows 10 iniciar y ejecutan automáticamente las herramientas remotas. En caso contrario, [instalar y ejecutar las herramientas remotas para Visual Studio](#BKMK_download).
  - Dispositivos móviles de Windows 10 no requiere ni admite las herramientas remotas.

## <a name="BKMK_ConnectVS"></a> Configurar un proyecto de Visual Studio para la depuración remota
<a name="BKMK_DirectConnect"></a> Usar el proyecto **propiedades** para especificar el dispositivo remoto al que conectarse. Las opciones varían según el lenguaje de programación.

> [!CAUTION]
> De forma predeterminada, se establece la página de propiedades **Universal (protocolo sin cifrar)** como el **tipo de autenticación** para las conexiones remotas de Windows 10. Es posible que deba establecer **sin autenticación** para conectarse al depurador remoto. **Universal (protocolo sin cifrar)** y **sin autenticación** protocolos no tienen ninguna seguridad de red, por lo que los datos transferidos entre el desarrollo y los equipos remotos están vulnerables. Elija estos tipos de autenticación solo para redes de confianza que se está seguro de que no corren riesgo de tráfico hostil o malintencionado.
>
>Si elige **Windows autenticación** para el **tipo de autenticación**, deberá iniciar sesión en el equipo remoto al depurar. También se debe ejecutar el depurador remoto bajo **Windows autenticación** modo con la misma cuenta de usuario como en el equipo de Visual Studio.

### <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Configurar un C# o proyecto de Visual Basic para la depuración remota

1. Seleccione el C# o proyecto de Visual Basic en Visual Studio **el Explorador de soluciones** y seleccione el **propiedades** icono, presione **Alt** +  **Escriba**, o bien haga clic en y elija **propiedades**.

1. Seleccione la pestaña **Depurar**.

1. En **dispositivo de destino**, seleccione **máquina remota** para un equipo remoto, o **dispositivo** para un dispositivo de Windows Mobile 10 conectados directamente.

1. Para un equipo remoto, escriba el nombre de red o la dirección IP en el **máquina remota** campo o seleccione **buscar** para buscar el dispositivo en el [cuadro de diálogo conexiones remotas](#remote-connections).

    ![Administra las propiedades del proyecto para la depuración remota](../debugger/media/vsrun_managed_projprop_remote.png "administrados depurar las propiedades del proyecto")

### <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Configurar un C++ proyecto para la depuración remota

1. Seleccione el C++ proyecto en Visual Studio **el Explorador de soluciones** y seleccione el **propiedades** icono, presione **Alt**+**ENTRAR**, o bien haga clic en y elija **propiedades**.

1. Seleccione el **depuración** ficha.

3. En **depurador para iniciar**, seleccione **máquina remota** para un equipo remoto, o **dispositivo** para un dispositivo de Windows Mobile 10 conectados directamente.

1. Para un equipo remoto, escriba o seleccione el nombre de red o la dirección IP en el **nombre de la máquina** campo o drop abajo y seleccione **buscar** para buscar el dispositivo en el [cuadro de diálogo conexiones remotas ](#remote-connections).

    ![Propiedades del proyecto de C++ para la depuración remota](../debugger/media/vsrun_cpp_projprop_remote.png "propiedades del proyecto de depuración de C++")

### <a name="remote-connections"></a> Utilice el cuadro de diálogo conexiones remotas

En el **conexiones remotas** cuadro de diálogo, puede buscar una dirección IP o nombre de equipo remoto específico o detectar automáticamente las conexiones seleccionando el icono de flecha redondea actualización. Busca solo los dispositivos en la subred local que se están ejecutando al depurador remoto en el cuadro de diálogo. No todos los dispositivos se pueden detectar en el **conexiones remotas** cuadro de diálogo.

 ![Cuadro de diálogo de conexión remoto](../debugger/media/vsrun_selectremotedebuggerdlg.png "cuadro de diálogo conexiones remotas")

>[!TIP]
>Si no se puede conectar a un dispositivo remoto por su nombre, pruebe a usar su dirección IP. Para averiguar la dirección IP, en el dispositivo remoto, escriba **ipconfig** en una ventana de comandos. La dirección IP aparece como **dirección IPv4**.

## <a name="BKMK_download"></a> Descargue e instale Herramientas remotas para Visual Studio

Para que Visual Studio depurar aplicaciones en un equipo remoto, el equipo remoto debe ejecutar las herramientas remotas para Visual Studio.

- Dispositivos móviles de Windows 10 no requiere ni admite las herramientas remotas.
- Actualización de ejecutando del creador de equipos de Windows 10 (versión 1703) y versiones posteriores, los dispositivos Windows 10 Xbox, IoT y HoloLens instalación las herramientas remotas automáticamente al implementar la aplicación.
- En equipos Windows 10 del creador anterior a Update, manualmente debe descargar, instalar y ejecutar las herramientas remotas en el equipo remoto antes de iniciar la depuración.

**Para descargar e instalar las herramientas remotas:**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="BKMK_setup"></a> Configurar las herramientas remotas

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

## <a name="BKMK_RunRemoteDebug"></a> Depuración remota de aplicaciones para UWP

Depuración remota funciona igual que la depuración local.

1. En las versiones de actualización del pre-creador de Windows 10, asegúrese de que el Monitor de depuración remota (*msvsmon.exe*) se está ejecutando en el dispositivo remoto.

1. En el equipo de Visual Studio, asegúrese de que el destino de depuración correcto (**máquina remota** o **dispositivo**) aparece junto a la flecha verde en la barra de herramientas.

1. Iniciar la depuración seleccionando **depurar** > **Iniciar depuración**, presiona **F5**, o seleccione la flecha verde en la barra de herramientas.

   El proyecto vuelve a compilar, a continuación, implementa y se inicia en el dispositivo remoto. El depurador suspende la ejecución en los puntos de interrupción, y puede ir a través de o fuera del código.

1. Si es necesario, seleccione **depurar** > **Detener depuración** o presione **MAYÚS**+**F5** para detener la depuración y Cierre la aplicación remota.

## <a name="see-also"></a>Vea también
- [Opciones avanzadas de implementación remota](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Prueba de aplicaciones para UWP con Visual Studio](/visualstudio/test/create-and-run-unit-tests-for-a-store-app-in-visual-studio/)
- [Depuración de aplicaciones para UWP en Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
