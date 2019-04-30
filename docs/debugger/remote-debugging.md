---
title: Depuración remota | Microsoft Docs
ms.custom:
- remotedebugging
- seodec18
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eecde0bc5e488cd91632a45406c621ce45bd4447
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63407752"
---
# <a name="remote-debugging"></a>Remote Debugging
Puede depurar una aplicación de Visual Studio que se ha implementado en un equipo diferente. Para ello, use el depurador remoto de Visual Studio

Para obtener instrucciones sobre la depuración remota, vea estos temas.

|Escenario|Link|
|-|-|-|
|Azure App Service|[Depurador de instantáneas](../debugger/debug-live-azure-applications.md) o [depuración remota de ASP.NET en Azure](../debugger/remote-debugging-azure.md)|
|Máquina virtual de Azure|[Depuración remota de ASP.NET en Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Depurar una aplicación de Azure Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Depuración remota de ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) o [ASP.NET de depuración remota](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# o Visual Basic|[Depuración remota de un proyecto de C# o Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Depuración remota de un proyecto de C++](../debugger/remote-debugging-cpp.md)|
|Aplicaciones universales de Windows (UWP)|[Ejecutar aplicaciones para UWP en un equipo remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md) o [depuración de un paquete de aplicación instalada](../debugger/debug-installed-app-package.md)|

Si simplemente desea descargar e instalar al depurador remoto y no necesita todas las instrucciones adicionales para su escenario, siga los pasos descritos en este artículo.

## <a name="download-and-install-the-remote-tools"></a>Descarga e instalación de las herramientas remotas

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements_msvsmon"></a> Requisitos

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="fileshare_msvsmon"></a> (Opcional) Para ejecutar al depurador remoto desde un recurso compartido de archivos

Puede encontrar el depurador remoto (*msvsmon.exe*) en un equipo con Visual Studio Community, Professional o Enterprise ya instalado. En algunos escenarios, la manera más fácil de configurar la depuración remota es ejecutar al depurador remoto (msvsmon.exe) desde un recurso compartido de archivos. Para conocer las limitaciones de uso, consulte la página de Ayuda del depurador remoto (**Ayuda > uso** en el depurador remoto).

1. Buscar *msvsmon.exe* en el directorio que coincida con su versión de Visual Studio:

   ::: moniker range=">=vs-2019"

   *Programa archivos (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Programa archivos (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Programa archivos (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Programa archivos (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. Recurso compartido de la **Remote Debugger** carpeta en el equipo de Visual Studio.

3. En el equipo remoto, ejecute *msvsmon.exe* desde la carpeta compartida. Siga el [instrucciones de instalación](#bkmk_setup).

> [!TIP]
> Para la instalación de línea de comandos y referencia de línea de comandos, consulte la página de ayuda para *msvsmon.exe* escribiendo ``msvsmon.exe /?`` en la línea de comandos en el equipo con Visual Studio instalada (o vaya a **Ayuda > uso**en el depurador remoto).

## <a name="bkmk_setup"></a> Establecimiento del depurador remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure_msvsmon"></a> Configuración del depurador remoto
Puede cambiar algunos aspectos de la configuración del depurador remoto tras iniciarlo por primera vez.

- Si necesita agregar permisos para otros usuarios se conecten al depurador remoto, elija **Herramientas > permisos**. Debe tener privilegios de administrador para conceder o denegar permisos.

     > [!IMPORTANT]
     > Puede ejecutar al depurador remoto bajo una cuenta de usuario que difiere de la cuenta de usuario que está usando en el equipo de Visual Studio, pero debe agregar la cuenta de usuario diferente a los permisos del depurador remoto.

     Como alternativa, puede iniciar el depurador remoto desde la línea de comandos con el **/ allow \<username >** parámetro: **msvsmon /Allow \< username@computer>**.

- Si necesita cambiar el modo de autenticación o el número de puerto o especificar un valor de tiempo de espera para las herramientas remotas: elija **Herramientas > opciones**.

     Para obtener una lista de los números de puerto que usa de forma predeterminada, consulte [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     > Puede elegir ejecutar las herramientas remotas en el Modo sin autenticación, aunque se recomienda no usar este modo. No hay ninguna seguridad de red cuando se ejecuta en este modo. Elija el modo sin autenticación solo si está seguro de que la red no presenta riesgos de tráfico malintencionado u hostil.

## <a name="bkmk_configureService"></a> (Opcional) Configurar al depurador remoto como servicio
Para la depuración en ASP.NET y otros entornos de servidor, debe ejecutar al depurador remoto como administrador o, si desea que siempre en ejecución, ejecute al depurador remoto como un servicio.

 Si desea configurar al depurador remoto como un servicio, siga estos pasos.

1. Busque el **Asistente para configuración del depurador remoto** (rdbgwiz.exe). (Esta es una aplicación independiente del Depurador remoto). Está disponible solo cuando se instalan las herramientas remotas. No se instala con Visual Studio.

2. Inicie el asistente para la configuración. Cuando aparezca la primera página, haga clic en **Siguiente**.

3. Active la casilla **Ejecutar el depurador remoto de Visual Studio 2015 como servicio** .

4. Agregue el nombre de la cuenta de usuario y la contraseña.

    Es posible que deba agregar el **iniciar sesión como un servicio** directamente a esta cuenta de usuario (buscar **directiva de seguridad Local** (secpol.msc) en el **iniciar** ventana o página (o tipo  **secpol** en un símbolo del sistema). Cuando aparezca la ventana, haga doble clic en **Asignación de derechos de usuario**y, a continuación, busque **Iniciar sesión como servicio** en el panel derecho. Haga doble clic en ella. Agregue la cuenta de usuario a la ventana **Propiedades** y haga clic en **Aceptar**. Haga clic en **Siguiente**.

5. Seleccione el tipo de red con el que desea que se comuniquen las herramientas remotas. Debe seleccionar al menos un tipo de red. Si los equipos están conectados a través de un dominio, debe elegir el primer elemento. Si los equipos están conectados a través de un grupo de trabajo o un grupo en el hogar, debe elegir el segundo o tercer elemento. Haga clic en **Siguiente**.

6. Si se puede iniciar el servicio, se mostrará el mensaje **Completó correctamente el Asistente para configuración de Visual Studio Remote Debugger**. Si no se puede iniciar el servicio, se mostrará el mensaje **Error al completar el Asistente para la configuración de Visual Studio Remote Debugger**. La página también proporciona algunas sugerencias para conseguir que se inicie el servicio.

7. Haga clic en **Finalizar**.

   En este momento, el depurador remoto se ejecuta como servicio. Puede comprobarlo en **Panel de Control > Servicios**, buscando **Depurador remoto de Visual Studio 2015**.

   Puede detener e iniciar el servicio del depurador remoto desde **Panel de Control > Servicios**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurar la depuración con símbolos remotos

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Vea también

- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
- [Configurar el Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Asignaciones de puertos del depurador remoto](../debugger/remote-debugger-port-assignments.md)
- [ASP.NET Core en un equipo remoto de IIS de depuración remota](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)