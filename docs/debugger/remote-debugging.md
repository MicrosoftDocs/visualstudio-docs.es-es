---
title: Depuración remota ( Remote debugging) Microsoft Docs
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
ms.openlocfilehash: 9918a2de67693c0232c94a736f12c7af0a0b959c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301060"
---
# <a name="remote-debugging"></a>Depuración remota
Puede depurar una aplicación de Visual Studio que se ha implementado en un equipo diferente. Para ello, use el depurador remoto de Visual Studio

Para obtener instrucciones detalladas sobre la depuración remota, consulte estos temas.

|Escenario|Vínculo|
|-|-|-|
|Azure App Service|[Depurador de instantáneas](../debugger/debug-live-azure-applications.md) o [depuración remota ASP.NET en Azure](../debugger/remote-debugging-azure.md)|
|Azure VM|[Depuración remota de ASP.NET en Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Depurar una aplicación de Azure Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Depuración remota ASP.NET núcleo](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) o [depuración remota ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# o Visual Basic|[Depuración remota de un proyecto de C# o Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Depuración remota de un proyecto C++](../debugger/remote-debugging-cpp.md)|
|Aplicaciones universales de Windows (UWP)|[Ejecutar aplicaciones para UWP en un equipo remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md) o depurar un paquete de aplicación [instalado](../debugger/debug-installed-app-package.md)|

Si solo desea descargar e instalar el depurador remoto y no necesita ninguna instrucción adicional para su escenario, siga los pasos de este artículo.

## <a name="download-and-install-the-remote-tools"></a>Descarga e instalación de las herramientas remotas

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a>Requisitos

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a>(Opcional) Para ejecutar el depurador remoto desde un recurso compartido de archivos

Puede encontrar el depurador remoto (*msvsmon.exe*) en un equipo con Visual Studio Community, Professional o Enterprise ya instalado. Para algunos escenarios, la forma más sencilla de configurar la depuración remota es ejecutar el depurador remoto (msvsmon.exe) desde un recurso compartido de archivos. Para conocer las limitaciones de uso, consulte la página Ayuda del depurador remoto **(Ayuda > uso** en el depurador remoto).

1. Busque *msvsmon.exe* en el directorio que coincida con su versión de Visual Studio:

   ::: moniker range=">=vs-2019"

   *Archivos de programa (x86)-Microsoft Visual Studio-2019-Empresa-Common7-IDE-Remote Debugger-x86-msvsmon.exe*

   *Archivos de programa (x86)-Microsoft Visual Studio-2019-Empresa-Common7-IDE-Remote Debugger-x64-msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Archivos de programa (x86)-Microsoft Visual Studio-2017-Empresa-Common7-IDE-Remote Debugger-x86-msvsmon.exe*

   *Archivos de programa (x86)-Microsoft Visual Studio-2017-Empresa-Common7-IDE-Remote Debugger-x64-msvsmon.exe*

   ::: moniker-end

2. Comparta la carpeta **Depurador remoto** en el equipo de Visual Studio.

3. En el equipo remoto, ejecute *msvsmon.exe* desde la carpeta compartida. Siga las [instrucciones de configuración](#bkmk_setup).

> [!TIP]
> Para obtener información sobre la instalación de la línea de comandos ``msvsmon.exe /?`` y la referencia de línea de comandos, vea la página Ayuda de *msvsmon.exe* escribiendo en la línea de comandos del equipo con Visual Studio instalado (o vaya a **Ayuda > uso** en el depurador remoto).

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a>Configurar el depurador remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a> Configuración del depurador remoto
Puede cambiar algunos aspectos de la configuración del depurador remoto tras iniciarlo por primera vez.

- Si necesita agregar permisos para que otros usuarios se conecten al depurador remoto, elija **Herramientas > Permisos**. Debe tener privilegios de administrador para conceder o denegar permisos.

     > [!IMPORTANT]
     > Puede ejecutar el depurador remoto en una cuenta de usuario que difiere de la cuenta de usuario que está utilizando en el equipo de Visual Studio, pero debe agregar la cuenta de usuario diferente a los permisos del depurador remoto.

     Como alternativa, puede iniciar el depurador remoto desde la línea de comandos con el parámetro ** \</allow username>:** **msvsmon \< username@computer /allow>**.

- Si necesita cambiar el modo de autenticación o el número de puerto, o especificar un valor de tiempo de espera para las herramientas remotas: elija **Herramientas > Opciones**.

     Para obtener una lista de los números de puerto utilizados de forma predeterminada, vea Asignaciones de [puertos](../debugger/remote-debugger-port-assignments.md)de depurador remoto .

     > [!WARNING]
     > Puede elegir ejecutar las herramientas remotas en el Modo sin autenticación, aunque se recomienda no usar este modo. No hay ninguna seguridad de red cuando se ejecuta en este modo. Elija el modo sin autenticación solo si está seguro de que la red no presenta riesgos de tráfico malintencionado u hostil.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a>(Opcional) Configure el depurador remoto como un servicio
Para depurar en ASP.NET y otros entornos de servidor, debe ejecutar el depurador remoto como administrador o, si lo desea, ejecutar el depurador remoto como un servicio.

 Si desea configurar el depurador remoto como un servicio, siga estos pasos.

1. Busque el **Asistente para configuración del depurador remoto** (rdbgwiz.exe). (Esta es una aplicación independiente del depurador remoto.) Solo está disponible cuando se instalan las herramientas remotas. No se instala con Visual Studio.

2. Inicie el asistente para la configuración. Cuando aparezca la primera página, haga clic en **Siguiente**.

3. Active la casilla **Ejecutar el depurador remoto de Visual Studio 2015 como servicio** .

4. Agregue el nombre de la cuenta de usuario y la contraseña.

    Es posible que deba agregar el derecho **Iniciar sesión como** usuario de servicio a esta cuenta (Buscar directiva de **seguridad local** (secpol.msc) en la página o ventana **Inicio** (o escriba **secpol** en un símbolo del sistema). Cuando aparezca la ventana, haga doble clic en **Asignación de derechos de usuario**y, a continuación, busque **Iniciar sesión como servicio** en el panel derecho. Haga doble clic en ella. Agregue la cuenta de usuario a la ventana **Propiedades** y haga clic en **Aceptar**. Haga clic en **Siguiente**.

5. Seleccione el tipo de red con el que desea que se comuniquen las herramientas remotas. Debe seleccionar al menos un tipo de red. Si los equipos están conectados a través de un dominio, debe elegir el primer elemento. Si los equipos están conectados a través de un grupo de trabajo o un grupo en el hogar, debe elegir el segundo o tercer elemento. Haga clic en **Siguiente**.

6. Si se puede iniciar el servicio, se mostrará el mensaje **Completó correctamente el Asistente para configuración de Visual Studio Remote Debugger**. Si no se puede iniciar el servicio, se mostrará el mensaje **Error al completar el Asistente para la configuración de Visual Studio Remote Debugger**. La página también proporciona algunas sugerencias para conseguir que se inicie el servicio.

7. Haga clic en **Finalizar**.

   En este momento, el depurador remoto se ejecuta como servicio. Para comprobarlo, vaya a **Control Panel > Services** y busque Visual Studio **2015 Remote Debugger**.

   Puede detener e iniciar el servicio de depurador remoto desde Panel de **control > Services**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurar depuración con símbolos remotos

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Consulte también

- [Primero mire el depurador](../debugger/debugger-feature-tour.md)
- [Configurar el Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Asignaciones de puerto del depurador remoto](../debugger/remote-debugger-port-assignments.md)
- [Depuración remota ASP.NET núcleo en un equipo IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)