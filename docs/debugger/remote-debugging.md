---
title: Depuración remota | Microsoft Docs
description: Puede depurar una aplicación de Visual Studio que se haya implementado en otro equipo usando el depurador remoto de Visual Studio.
ms.custom:
- remotedebugging
- seodec18
- SEO-VS-2020
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
ms.openlocfilehash: e97fd8979235f8ea89b43c6466b3119debe5b3ca
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205676"
---
# <a name="remote-debugging"></a>Depuración remota
Puede depurar una aplicación de Visual Studio que se ha implementado en un equipo diferente. Para ello, use el depurador remoto de Visual Studio

Para obtener instrucciones detalladas sobre la depuración remota, vea estos temas.

|Escenario|Link|
|-|-|-|
|Azure App Service|[Depuración remota de ASP.NET en Azure](../debugger/remote-debugging-azure.md) o, en el caso de Visual Studio Enterprise, [Snapshot Debugger](../debugger/debug-live-azure-applications.md)|
|Azure VM|[Depuración remota de ASP.NET en Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Depurar una aplicación de Service Fabric remota](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Depuración remota de ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) o [Depuración remota de ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# o Visual Basic|[Depuración remota de un proyecto de C# o Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Depuración remota de un proyecto de C++](../debugger/remote-debugging-cpp.md)|
|Aplicaciones de Windows universales (UWP)|[Ejecución de aplicaciones para UWP en un equipo remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md) o [Depuración de un paquete de aplicaciones instalado](../debugger/debug-installed-app-package.md)|

Si solo quiere descargar e instalar el depurador remoto y no necesita instrucciones adicionales para su escenario, siga los pasos de este artículo.

## <a name="download-and-install-the-remote-tools"></a>Descarga e instalación de las herramientas remotas

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a> Requisitos

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a> (Opcional) Ejecución del depurador remoto desde un recurso compartido de archivos

Encontrará el depurador remoto (*msvsmon.exe*) en un equipo con Visual Studio Community, Professional o Enterprise ya instalado. En algunos escenarios, la manera más sencilla de configurar la depuración remota es ejecutar el depurador remoto (msvsmon.exe) desde un recurso compartido de archivos. Para conocer las limitaciones de uso, consulte la página de ayuda del depurador remoto (**Ayuda > Uso** en el depurador remoto).

1. Busque *msvsmon.exe* en el directorio y elija el archivo que corresponda a su versión de Visual Studio:

   ::: moniker range=">=vs-2019"

   *Archivos de programa (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Archivos de programa (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Archivos de programa (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Archivos de programa (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. Comparta la carpeta **Remote Debugger** en el equipo de Visual Studio.

3. En el equipo remoto, ejecute *msvsmon.exe* desde la carpeta compartida. Siga las [instrucciones de instalación](#bkmk_setup).

> [!TIP]
> Para obtener la referencia de la línea de comandos y la instalación de la línea de comandos, consulte la página de ayuda de *msvsmon.exe* escribiendo ``msvsmon.exe /?`` en la línea de comandos del equipo con Visual Studio instalado (o vaya a **Ayuda > Uso** en el depurador remoto).

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a> Establecimiento del depurador remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a> Configuración del depurador remoto
Puede cambiar algunos aspectos de la configuración del depurador remoto tras iniciarlo por primera vez.

- Si necesita agregar permisos para que otros usuarios se conecten al depurador remoto, elija **Herramientas > Permisos**. Debe tener privilegios de administrador para conceder o denegar permisos.

     > [!IMPORTANT]
     > Puede ejecutar el depurador remoto con una cuenta de usuario distinta de la que se usa en el equipo de Visual Studio, pero debe agregar dicha cuenta de usuario a los permisos del depurador remoto.

     También puede iniciar el depurador remoto desde la línea de comandos con el parámetro **/allow \<username>** : **msvsmon /allow \<username@computer>** .

- Si necesita cambiar el modo de autenticación o el número de puerto, o especificar un valor de tiempo de espera para las herramientas remotas, elija **Herramientas > Opciones**.

     Para obtener una lista de los números de puerto que se usan de forma predeterminada, consulte [Asignaciones de puertos del depurador remoto](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     > Puede elegir ejecutar las herramientas remotas en el Modo sin autenticación, aunque se recomienda no usar este modo. No hay ninguna seguridad de red cuando se ejecuta en este modo. Elija el modo sin autenticación solo si está seguro de que la red no presenta riesgos de tráfico malintencionado u hostil.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a> (Opcional) Configuración del depurador remoto como servicio
Para la depuración en ASP.NET y en otros entornos de servidor, debe ejecutar el depurador remoto como administrador o, si quiere que siempre esté en ejecución, inicie el depurador remoto como servicio.

 Si quiere configurar el depurador remoto como servicio, siga estos pasos.

1. Busque el **Asistente para configuración del depurador remoto** (rdbgwiz.exe). (Esta es una aplicación independiente del Depurador remoto). Está disponible solo cuando se instalan las herramientas remotas. No se instala con Visual Studio.

2. Inicie el asistente para la configuración. Cuando aparezca la primera página, haga clic en **Siguiente**.

3. Active la casilla **Ejecutar el depurador remoto de Visual Studio 2015 como servicio**.

4. Agregue el nombre de la cuenta de usuario y la contraseña.

    Es posible que necesite agregar el derecho de usuario **Iniciar sesión como servicio** a esta cuenta. Para ello, busque **Directiva de seguridad local** (secpol.msc) en la ventana o la página **Iniciar**, o bien escriba **secpol** en un símbolo del sistema. Cuando aparezca la ventana, haga doble clic en **Asignación de derechos de usuario** y, a continuación, busque **Iniciar sesión como servicio** en el panel derecho. Haga doble clic en ella. Agregue la cuenta de usuario a la ventana **Propiedades** y haga clic en **Aceptar**. Haga clic en **Siguiente**.

5. Seleccione el tipo de red con el que desea que se comuniquen las herramientas remotas. Debe seleccionar al menos un tipo de red. Si los equipos están conectados a través de un dominio, debe elegir el primer elemento. Si los equipos están conectados a través de un grupo de trabajo o un grupo en el hogar, debe elegir el segundo o tercer elemento. Haga clic en **Siguiente**.

6. Si se puede iniciar el servicio, se mostrará el mensaje **Completó correctamente el Asistente para configuración de Visual Studio Remote Debugger**. Si no se puede iniciar el servicio, se mostrará el mensaje **Error al completar el Asistente para la configuración de Visual Studio Remote Debugger**. La página también proporciona algunas sugerencias para conseguir que se inicie el servicio.

7. Haga clic en **Finalizar**.

   En este momento, el depurador remoto se ejecuta como servicio. Puede comprobarlo en **Panel de Control > Servicios**, buscando **Depurador remoto de Visual Studio 2015**.

   Puede detener e iniciar el servicio del depurador remoto desde **Panel de Control > Servicios**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configuración de la depuración con símbolos remotos

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Vea también

- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
- [Configurar el Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Asignaciones de puertos del depurador remoto](../debugger/remote-debugger-port-assignments.md)
- [Depuración remota de ASP.NET Core en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)