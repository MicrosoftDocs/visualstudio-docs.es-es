---
title: Solución de problemas de depuración de instantáneas | Microsoft Docs
description: Obtenga información sobre la solución de problemas y los problemas conocidos de depuración de instantáneas en Visual Studio. Cargue ICorProfiler sin provocar tiempo de inactividad en el sitio de producción.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5a76c1cae508acd08e5f077d466facf02e0211a
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728649"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Solución de problemas y problemas conocidos de depuración de instantáneas en Visual Studio

Si los pasos que se describen en este artículo no resuelven el problema, busque el problema en [Developer Community](https://aka.ms/feedback/suggest?space=8) o notifique un problema nuevo mediante la selección de **Ayuda** > **Enviar comentarios** > **Notificar un problema** en Visual Studio.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Problema: "Asociar Snapshot Debugger" detecta un error de código de estado HTTP

Si ve el error siguiente en la ventana de **salida** durante el intento de asociación, puede ser un problema conocido que se muestra a continuación. Pruebe las soluciones propuestas y, si el problema continúa, póngase en contacto con el alias anterior.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) No autorizado

Este error indica que la llamada de REST que Visual Studio emite a Azure usa una credencial no válida. 

Siga estos pasos:

* Asegúrese de que la cuenta de personalización de Visual Studio tiene permisos para la suscripción y el recurso de Azure a los que se está asociando. Una manera rápida de determinar esto es comprobar si el recurso está disponible en el cuadro de diálogo de **Depurar** > **Asociar Snapshot Debugger…**  > **Recurso de Azure** > **Seleccionar existente** o en Cloud Explorer.
* Si este error continúa, use uno de los canales de comentarios descritos al comienzo de este artículo.

Si ha habilitado Autenticación y autorización (EasyAuth) en App Service, es posible que encuentre un error 401 con LaunchAgentAsync en el mensaje de error de la pila de llamadas. Asegúrese de que **Acción necesaria cuando la solicitud no está autenticada** se ha establecido en **Permitir solicitudes anónimas (ninguna acción)** en Azure Portal y proporcione un archivo autorización.json en D:\Home\wwwwroot con el siguiente contenido en su lugar. 

```
{
  "routes": [
    {
      "path_prefix": "/",
      "policies": {
        "unauthenticated_action": "RedirectToLoginPage"
      }
    },
    {
      "http_methods": [ "POST" ],
      "path_prefix": "/41C07CED-2E08-4609-9D9F-882468261608/api/agent",
      "policies": {
        "unauthenticated_action": "AllowAnonymous"
      }
    }
  ]
}
```

La primera ruta protege eficazmente el dominio de la aplicación de forma similar a **Inicio de sesión con [IdentityProvider]** . La segunda ruta expone el punto de conexión AgentLaunch de SnapshotDebugger fuera de la autenticación, que solo realiza la acción predefinida de iniciar el *agente de diagnóstico de SnapshotDebugger* si la extensión de sitio preinstalado SnapshotDebugger está habilitada para el servicio de aplicaciones. Para más información sobre la configuración de Authorization.json, consulte el artículo sobre [reglas de autorización para direcciones URL](https://azure.github.io/AppService/2016/11/17/URL-Authorization-Rules.html).

### <a name="403-forbidden"></a>(403) Prohibido

Este error indica que se denegó el permiso. Puede deberse a muchos problemas distintos.

Siga estos pasos:

* Compruebe que la cuenta de Visual Studio tiene una suscripción a Azure válida con los permisos de control de acceso basado en rol (RBAC) del recurso. En el caso de AppService, compruebe si tiene permisos para [consultar](/rest/api/appservice/appserviceplans/get) el plan de App Service que hospeda la aplicación.
* Compruebe que la marca de tiempo de la máquina cliente sea correcta y esté actualizada. Los servidores con marcas de tiempo con una diferencia de más de 15 minutos con respecto la marca de tiempo de la solicitud suelen generar este error.
* Si este error continúa, use uno de los canales de comentarios descritos al comienzo de este artículo.

### <a name="404-not-found"></a>(404) No encontrado

Este error indica que el sitio web no se pudo encontrar en el servidor.

Siga estos pasos:

* Compruebe que tiene un sitio web implementado y en ejecución en el recurso de App Service al que se está asociando.
* Compruebe que el sitio está disponible en https://\<resource\>.azurewebsites.net
* Compruebe que la aplicación web personalizada que se ejecuta correctamente no devuelve un código de estado 404 cuando se accede a ella en https://\<resource\>.azurewebsites.net
* Si este error continúa, use uno de los canales de comentarios descritos al comienzo de este artículo.

### <a name="406-not-acceptable"></a>(406) No aceptable

Este error indica que el servidor no puede responder el tipo establecido en el encabezado Accept de la solicitud.

Siga estos pasos:

* Compruebe que el sitio está disponible en https://\<resource\>.azurewebsites.net
* Compruebe que el sitio no se migró a instancias nuevas. Snapshot Debugger usa la noción de ARRAffinity para enrutar las solicitudes a instancias específicas que pueden generar este error de forma intermitente.
* Si este error continúa, use uno de los canales de comentarios descritos al comienzo de este artículo.

### <a name="409-conflict"></a>(409) Conflicto

Este error indica que la solicitud está en conflicto con el estado actual del servidor.

Este es un problema conocido que se produce cuando un usuario intenta asociar Snapshot Debugger a una instancia de AppService que tiene habilitado ApplicationInsights. ApplicationInsights establece AppSettings con una grafía distinta de Visual Studio, lo que provoca este problema.

::: moniker range=">= vs-2019"
Esto se resolvió en Visual Studio 2019.
::: moniker-end

Siga estos pasos:

::: moniker range="vs-2017"

* En Azure Portal, compruebe que AppSettings para SnapshotDebugger (SNAPSHOTDEBUGGER_EXTENSION_VERSION) e InstrumentationEngine (INSTRUMENTATIONENGINE_EXTENSION_VERSION) están en mayúsculas. Si no es así, actualice manualmente la configuración, lo que obliga a un reinicio del sitio.
::: moniker-end
* Si este error continúa, use uno de los canales de comentarios descritos al comienzo de este artículo.

### <a name="500-internal-server-error"></a>(500) Error interno del servidor

Este error indica que el sitio está totalmente fuera de servicio o que el servidor no puede administrar la solicitud. Snapshot Debugger funciona solo en aplicaciones en ejecución. [Application Insights Snapshot Debugger](/azure/azure-monitor/app/snapshot-debugger) permite tomar instantáneas de las excepciones y puede ser la mejor herramienta para sus necesidades.

### <a name="502-bad-gateway"></a>(502) Puerta de enlace incorrecta

Este error indica un problema de red del lado servidor y puede ser temporal.

Siga estos pasos:

* Intente esperar unos minutos antes de volver a adjuntar Snapshot Debugger.
* Si este error continúa, use uno de los canales de comentarios descritos al comienzo de este artículo.

## <a name="issue-snappoint-does-not-turn-on"></a>Problema: Punto de instantánea no activo

Si ve un icono de advertencia ![icono de advertencia de punto de instantánea](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Icono de advertencia de punto de instantánea") con el punto de instantánea en lugar del icono de punto de instantánea habitual, significa que el punto de instantánea no está activo.

![Punto de instantánea no activo](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Punto de instantánea no activo")

Siga estos pasos:

1. Asegúrese de que tiene la misma versión de código fuente que se usó para compilar e implementar la aplicación. Asegúrese de que va a cargar los símbolos correctos para su implementación. Para ello, vea la ventana **Módulos** mientras se lleva a cabo la depuración de instantáneas y verifique si la columna Archivo de símbolo muestra un archivo .pdb cargado para el módulo que va a depurar. Snapshot Debugger intentará descargar automáticamente y usar los símbolos para la implementación.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problema: Los símbolos no se cargan al abrir una instantánea

Si ve la siguiente ventana, significa que los símbolos no se cargan.

![Los símbolos no se cargan](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Los símbolos no se cargan")

Siga estos pasos:

- Haga clic en el vínculo **Cambiar configuración de símbolos...** en esta página. En la configuración **Depuración > Símbolo**, agregue un directorio de caché de símbolos. Reinicie la depuración de instantáneas una vez establecida la ruta de acceso a los símbolos.

   Los símbolos o los archivos .pdb disponibles en el proyecto deben coincidir con la implementación de App Service. La mayoría de las implementaciones (implementación mediante Visual Studio, CI/CD con Azure Pipelines o Kudu, etc.) publicarán los archivos de símbolo en App Service. La configuración del directorio de caché de símbolos permite a Visual Studio usar estos símbolos.

   ![Valores de los símbolos](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Valores de los símbolos")

- Como alternativa, si la organización usa un servidor de símbolos o cambia los símbolos a una ruta de acceso distinta, use la configuración de símbolos para cargar los símbolos correctos para su implementación.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problema: No puedo ver la opción "Asociar Snapshot Debugger" en Cloud Explorer

Siga estos pasos:

- Asegúrese de que el componente de Snapshot Debugger está instalado. Abra el Instalador de Visual Studio y compruebe el componente de **Snapshot Debugger** en la carga de trabajo de Azure.
::: moniker range="< vs-2019"
- Asegúrese de que la aplicación es compatible. Actualmente, solo son compatibles las aplicaciones ASP.NET (4.6.1+) y ASP.NET Core (2.0+) implementadas en Azure App Service.
::: moniker-end
::: moniker range=">= vs-2019"
- Asegúrese de que su aplicación es compatible:
  - Azure App Service: aplicaciones ASP.NET que se ejecutan en .NET Framework 4.6.1 o versiones posteriores.
  - Azure App Service: aplicaciones ASP.NET Core que se ejecutan en .NET Core 2.0 o posteriores en Windows.
  - Azure Virtual Machines y Virtual Machine Scale Sets: aplicaciones ASP.NET que se ejecutan en .NET Framework 4.6.1 o versiones posteriores.
  - Azure Virtual Machines y Virtual Machine Scale Sets: aplicaciones ASP.NET Core que se ejecutan en .NET Core 2.0 o versiones posteriores en Windows.
  - Azure Kubernetes Service: aplicaciones ASP.NET Core que se ejecutan en .NET Core 2.2 o posteriores en Debian 9.
  - Azure Kubernetes Service: aplicaciones ASP.NET Core que se ejecutan en .NET Core 2.2 o posteriores en Alpine 3.8.
  - Azure Kubernetes Service: aplicaciones ASP.NET Core que se ejecutan en .NET Core 2.2 o posteriores en Ubuntu 18.04.
::: moniker-end

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problema: Solo veo instantáneas limitadas en las Herramientas de diagnóstico

![Punto de instantánea limitado](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Punto de instantánea limitado")

Siga estos pasos:

- Las instantáneas ocupan poco memoria pero tienen una carga de confirmación. Si Snapshot Debugger detecta que el servidor soporta una carga de memoria pesada, no realizará instantáneas. Puede eliminar las instantáneas que ya están capturadas; para ello, detenga la sesión de Snapshot Debugger y vuelva a intentarlo.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problema: La depuración de instantáneas con varias versiones de Visual Studio genera errores

Visual Studio 2019 requiere una versión más reciente de la extensión de sitio de Snapshot Debugger en la instancia de Azure App Service.  Esta versión no es compatible con la versión anterior de la extensión de sitio de Snapshot Debugger que usa Visual Studio 2017.  Obtendrá el siguiente error si intenta adjuntar Snapshot Debugger en Visual Studio 2019 a una instancia de Azure App Service que se depuró anteriormente con Snapshot Debugger en Visual Studio 2017:

![Extensión de sitio de Snapshot Debugger no compatible con Visual Studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "Extensión de sitio de Snapshot Debugger no compatible con Visual Studio 2019")

Por el contrario, si usa Visual Studio 2017 para adjuntar Snapshot Debugger a una instancia de Azure App Service que se depuró anteriormente con Snapshot Debugger en Visual Studio 2019, obtendrá el error siguiente:

![Extensión de sitio de Snapshot Debugger no compatible con Visual Studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "Extensión de sitio de Snapshot Debugger no compatible con Visual Studio 2017")

Para solucionar este problema, elimine la siguiente configuración de la aplicación en Azure Portal y vuelva a adjuntar Snapshot Debugger:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problema: Tengo problemas con la depuración de instantáneas y necesito habilitar más registros

### <a name="enable-agent-logs"></a>Habilitar los registros del agente

Para habilitar y deshabilitar los registros del agente, abra Visual Studio y vaya a *Herramientas>Opciones>Snapshot Debugger>Habilitar el registro del agente*. Tenga en cuenta que, si la opción *Eliminar registros del agente anterior en el inicio de sesión* también está habilitada, cada vinculación correcta de Visual Studio eliminará los registros anteriores del agente.

Los registros del agente se pueden encontrar en las ubicaciones siguientes:

- App Services:
  - Vaya al sitio de Kudu en App Service, es decir, yourappservice.**scm**.azurewebsites.net, y acceda a la consola de depuración.
  - Los registros del agente se almacenan en el directorio siguiente:  D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- VM/VMSS:
  - Inicie sesión en la máquina virtual, los registros del agente se almacenan de la siguiente manera:  C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics\<Version>\SnapshotDebuggerAgent_*.txt
- AKS
  - Vaya al siguiente directorio: /tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>Habilitar los registros de instrumentación y del generador de perfiles

Los registros de instrumentación pueden encontrarse en las siguientes ubicaciones:

- App Services:
  - Los registros de errores se envían automáticamente a D:\Home\LogFiles\eventlog.xml. Los eventos se marcan con `<Provider Name="Instrumentation Engine" />` o "Puntos de interrupción de producción"
- VM/VMSS:
  - Inicie sesión en la máquina virtual y abra el Visor de eventos.
  - Abra la vista siguiente: *Registros de Windows>Aplicación*.
  - *Filtre el registro actual* por *Origen del evento* con las opciones *Puntos de interrupción de producción* o *Motor de instrumentación*.
- AKS
  - Registros del motor de instrumentación en /tmp/diag/log.txt (defina MicrosoftInstrumentationEngine_FileLogPath en DockerFile)
  - Registros del punto de interrupción de producción en /tmp/diag/shLog.txt

## <a name="known-issues"></a>Problemas conocidos

- Actualmente no se admite al depuración con varios clientes de Visual Studio en la misma instancia de App Service.
- Las optimizaciones de Roslyn IL no son totalmente compatibles en los proyectos de ASP.NET Core. Para algunos proyectos de ASP.NET Core, es posible que no pueda ver más variables o usar algunas variables en instrucciones condicionales.
- Las variables especiales, como *$FUNCTION* o *$CALLER*, no pueden evaluarse en instrucciones condicionales o puntos de registro para los proyectos de ASP.NET Core.
- La depuración de instantáneas no funciona en las instancias de App Services que tienen activada la opción [Almacenamiento en caché local](/azure/app-service/app-service-local-cache).
- La depuración de instantáneas en las aplicaciones de API no es compatible actualmente.

## <a name="site-extension-upgrade"></a>Actualización de la extensión de sitio

La depuración de instantáneas y Application Insights dependen de ICorProfiler, que se carga en el proceso del sitio y causa problemas de bloqueo de archivos durante la actualización. Se recomienda este proceso para asegurarse de que no se produzca ningún tiempo de inactividad en el sitio de producción.

- Cree una [ranura de implementación](/azure/app-service/web-sites-staged-publishing) en la instancia de App Service e implemente el sitio en la ranura.
- Intercambie la ranura con producción desde Cloud Explorer en Visual Studio o desde Azure Portal.
- Detenga el sitio de la ranura. Llevará algunos segundos terminar el proceso w3wp.exe del sitio en todas las instancias.
- Actualice la extensión de sitio de la ranura desde el sitio de Kudu o Azure Portal (*hoja App Service > Herramientas de desarrollo > Extensiones > Actualizar*).
- Inicie el sitio de la ranura. Se recomienda visitar el sitio para volver a intentarlo.
- Intercambie la ranura con producción.

## <a name="see-also"></a>Vea también

- [Depurar en Visual Studio](../debugger/index.yml)
- [Depuración de aplicaciones ASP.NET en vivo con Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Depuración de aplicaciones ASP.NET en vivo en Azure Virtual Machines\Virtual Machines Scale Sets con Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Depuración de Azure Kubernetes de ASP.NET en vivo con Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [P+F sobre depuración de instantáneas](../debugger/debug-live-azure-apps-faq.md)
