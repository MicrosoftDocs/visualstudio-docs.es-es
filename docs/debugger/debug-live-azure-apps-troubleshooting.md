---
title: Solución de problemas de depuración de instantáneas | Microsoft Docs
ms.custom: ''
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
ms.openlocfilehash: 27df4c097d829a4d28a77b9b1ad96eb389f4096c
ms.sourcegitcommit: dc12a7cb66124596089f01d3e939027ae562ede9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71962940"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Solución de problemas y problemas conocidos de depuración de instantáneas en Visual Studio

Si los pasos descritos en este artículo no resuelven el problema, busque el problema en [la comunidad de desarrolladores](https://developercommunity.visualstudio.com/spaces/8/index.html) o informe de un problema nuevo; para ello, elija **ayuda** > **Enviar comentarios** > **notificar un problema** en Visual Studio.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Problema: "Attach Snapshot Debugger" detecta un error de código de Estado HTTP

Si ve el siguiente error en la ventana de **salida** durante el intento de adjuntar, puede ser un problema conocido que se muestra a continuación. Pruebe las soluciones propuestas y, si el problema continúa, póngase en contacto con el alias anterior.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) no autorizado

Este error indica que la llamada de REST que emite Visual Studio a Azure usa una credencial no válida. Un error conocido con el módulo de OAuth de Azure Active Directory Easy puede producir este error.

Siga estos pasos:

* Asegúrese de que la cuenta de personalización de Visual Studio tiene permisos para la suscripción y el recurso de Azure a los que está asociando. Una manera rápida de determinarlo es comprobar si el recurso está disponible en el cuadro de diálogo de **Depuración** > **adjuntar Snapshot Debugger..** .  > **recurso de Azure** > **Seleccione existente**o en Cloud Explorer.
* Si el error persiste, use uno de los canales de comentarios descritos en el principio de este artículo.

### <a name="403-forbidden"></a>(403) prohibido

Este error indica que se ha denegado el permiso. Esto puede deberse a muchos problemas diferentes.

Siga estos pasos:

* Compruebe que la cuenta de Visual Studio tiene una suscripción de Azure válida con los permisos de Access Control basado en roles (RBAC) necesarios para el recurso. En el caso de AppService, compruebe si tiene permisos para [consultar](https://docs.microsoft.com/rest/api/appservice/appserviceplans/get) el Plan de App Service que hospeda la aplicación.
* Compruebe que la marca de tiempo de su equipo cliente es correcta y actualizada. Los servidores con marcas de tiempo desactivadas en más de 15 minutos de la marca de tiempo de la solicitud suelen producir este error.
* Si el error persiste, use uno de los canales de comentarios descritos en el principio de este artículo.

### <a name="404-not-found"></a>(404) no encontrado

Este error indica que el sitio web no se pudo encontrar en el servidor.

Siga estos pasos:

* Compruebe que tiene un sitio Web implementado y en ejecución en el App Service recurso al que está asociando.
* Compruebe que el sitio está disponible en https://@no__t -0resource\>.azurewebsites.net
* Compruebe que la aplicación web personalizada que se está ejecutando correctamente no devuelve un código de estado 404 cuando se accede a él en https://@no__t -0resource\>.azurewebsites.net
* Si el error persiste, use uno de los canales de comentarios descritos en el principio de este artículo.

### <a name="406-not-acceptable"></a>(406) no aceptable

Este error indica que el servidor no puede responder al tipo establecido en el encabezado Accept de la solicitud.

Siga estos pasos:

* Compruebe que el sitio está disponible en https://@no__t -0resource\>.azurewebsites.net
* Compruebe que el sitio no se ha migrado a nuevas instancias. Snapshot Debugger usa la noción de ARRAffinity para enrutar las solicitudes a instancias específicas que pueden producir este error de forma intermitente.
* Si el error persiste, use uno de los canales de comentarios descritos en el principio de este artículo.

### <a name="409-conflict"></a>(409) conflicto

Este error indica que la solicitud entra en conflicto con el estado actual del servidor.

Se trata de un problema conocido que se produce cuando un usuario intenta asociar Snapshot Debugger a un AppService que tiene habilitado ApplicationInsights. ApplicationInsights establece el AppSettings con una grafía diferente a la de Visual Studio, lo que produce este problema.

::: moniker range=">= vs-2019"
Hemos resuelto esto en Visual Studio 2019.
::: moniker-end

Siga estos pasos:

::: moniker range="vs-2017"

* Compruebe en el Azure Portal que el AppSettings para SnapshotDebugger (SNAPSHOTDEBUGGER_EXTENSION_VERSION) y InstrumentationEngine (INSTRUMENTATIONENGINE_EXTENSION_VERSION) estén en mayúsculas. Si no es así, actualice la configuración manualmente, lo que obliga a que se reinicie el sitio.
::: moniker-end
* Si el error persiste, use uno de los canales de comentarios descritos en el principio de este artículo.

### <a name="500-internal-server-error"></a>(500) error interno del servidor

Este error indica que el sitio está completamente inactivo o el servidor no puede controlar la solicitud. Snapshot Debugger solo funciones de las aplicaciones en ejecución. [Application Insights Snapshot Debugger](https://docs.microsoft.com/azure/azure-monitor/app/snapshot-debugger) proporciona la instantánea de las excepciones y puede ser la mejor herramienta para sus necesidades.

### <a name="502-bad-gateway"></a>(502) puerta de enlace incorrecta

Este error indica un problema de red del lado servidor y puede ser temporal.

Siga estos pasos:

* Intente esperar unos minutos antes de volver a adjuntar el Snapshot Debugger.
* Si el error persiste, use uno de los canales de comentarios descritos en el principio de este artículo.

## <a name="issue-snappoint-does-not-turn-on"></a>Problema: Acoplamiento no se activa

Si ve un icono de advertencia ![icono de advertencia de punto de instantánea](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "icono de advertencia de punto de instantánea") con el punto de instantánea en lugar del icono de punto de instantánea habitual, significa que el punto de instantánea no está activo.

![El punto de instantánea no está activo](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "El punto de instantánea no está activo")

Siga estos pasos:

1. Asegúrese de que tiene la misma versión del código fuente que se usó para compilar e implementar la aplicación. Asegúrese de que va a cargar los símbolos correctos para su implementación. Para ello, vea la ventana **Módulos** mientras se lleva a cabo la depuración de instantáneas y verifique si la columna Archivo de símbolo muestra un archivo .pdb cargado para el módulo que va a depurar. Snapshot Debugger intentará descargar automáticamente y usar los símbolos para la implementación.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problema: Los símbolos no se cargan cuando abro una instantánea

Si ve la siguiente ventana, significa que los símbolos no se cargan.

![Los símbolos no se cargan](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Los símbolos no se cargan")

Siga estos pasos:

- Haga clic en el vínculo **Cambiar configuración de símbolos...** en esta página. En la configuración **Depuración > Símbolo**, agregue un directorio de caché de símbolos. Reinicie la depuración de instantáneas una vez establecida la ruta de acceso a los símbolos.

   Los símbolos o los archivos .pdb disponibles en el proyecto deben coincidir con la implementación de App Service. La mayoría de las implementaciones (implementación mediante Visual Studio, CI/CD con Azure Pipelines o Kudu, etc.) publicarán los archivos de símbolo en App Service. La configuración del directorio de caché de símbolos permite a Visual Studio usar estos símbolos.

   ![Configuración de símbolos](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Configuración de símbolos")

- Como alternativa, si la organización usa un servidor de símbolos o cambia los símbolos a una ruta de acceso distinta, use la configuración de símbolos para cargar los símbolos correctos para su implementación.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problema: No veo la opción "adjuntar Snapshot Debugger" en el Cloud Explorer

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

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problema: Solo veo instantáneas limitadas en el Herramientas de diagnóstico

![Punto de instantánea limitado](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Punto de instantánea limitado")

Siga estos pasos:

- Las instantáneas ocupan poco memoria pero tienen una carga de confirmación. Si Snapshot Debugger detecta que el servidor soporta una carga de memoria pesada, no realizará instantáneas. Puede eliminar las instantáneas que ya están capturadas; para ello, detenga la sesión de Snapshot Debugger y vuelva a intentarlo.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problema: La depuración de instantáneas con varias versiones de Visual Studio me proporciona errores

Visual Studio 2019 requiere una versión más reciente de la extensión de sitio Snapshot Debugger en el Azure App Service.  Esta versión no es compatible con la versión anterior de la extensión de sitio Snapshot Debugger utilizada por Visual Studio 2017.  Recibirá el siguiente error si intenta adjuntar el Snapshot Debugger en Visual Studio 2019 a una Azure App Service que se haya depurado previamente mediante el Snapshot Debugger en Visual Studio 2017:

![Extensión de sitio Snapshot Debugger incompatible visual studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "incompatible Snapshot Debugger extensión de sitio Visual Studio 2019")

Por el contrario, si usa Visual Studio 2017 para adjuntar el Snapshot Debugger a un Azure App Service que se ha depurado previamente mediante el Snapshot Debugger en Visual Studio 2019, obtendrá el siguiente error:

![Extensión de sitio Snapshot Debugger incompatible visual studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "incompatible Snapshot Debugger extensión de sitio Visual Studio 2017")

Para solucionar este problema, elimine la siguiente configuración de la aplicación en Azure Portal y vuelva a adjuntar Snapshot Debugger:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problema: Tengo problemas de depuración de instantáneas y necesito habilitar más registro

### <a name="enable-agent-logs"></a>Habilitar los registros del agente

Para habilitar y deshabilitar los registros del agente, abra Visual Studio y vaya a *Herramientas>Opciones>Snapshot Debugger>Habilitar el registro del agente*. Tenga en cuenta que, si la opción *Eliminar registros del agente anterior en el inicio de sesión* también está habilitada, cada vinculación correcta de Visual Studio eliminará los registros anteriores del agente.

Los registros del agente se pueden encontrar en las ubicaciones siguientes:

- App Services:
  - Vaya al sitio de Kudu en App Service, es decir, yourappservice.**scm**.azurewebsites.net, y acceda a la consola de depuración.
  - Los registros del agente se almacenan en el siguiente directorio:  D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- VM/VMSS:
  - Inicie sesión en la máquina virtual, los registros del agente se almacenan de la siguiente manera:  C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics\<Version>\SnapshotDebuggerAgent_*.txt
- AKS
  - Vaya al siguiente directorio: /tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>Habilitar los registros de instrumentación y del generador de perfiles

Los registros de instrumentación pueden encontrarse en las siguientes ubicaciones:

- App Services:
  - El registro de errores se envía automáticamente a D:\Home\LogFiles\eventlog.xml, los eventos se marcan con `<Provider Name="Instrumentation Engine" />` o "puntos de interrupción de producción".
- VM/VMSS:
  - Inicie sesión en la máquina virtual y abra el Visor de eventos.
  - Abra la vista siguiente: *Registros de Windows > aplicación*.
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
- [Depure aplicaciones de ASP.NET dinámicas con el Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Depure conjuntos de escalado de máquinas virtuales de Azure virtual Machines\Virtual ASP.NET con el Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Depure Live ASP.NET Azure Kubernetes mediante el Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [P+F sobre depuración de instantáneas](../debugger/debug-live-azure-apps-faq.md)
