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
ms.openlocfilehash: e3c66ba4a5031326ec288d3a5f2f3c4851d17ca6
ms.sourcegitcommit: 74c5360186731de07828764eb32ea1033a8c2275
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2019
ms.locfileid: "67559747"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Solución de problemas y problemas conocidos de depuración de instantáneas en Visual Studio

Si los pasos descritos en este artículo no resuelve el problema, busque el problema en [Comunidad de desarrolladores](https://developercommunity.visualstudio.com/spaces/8/index.html) o notificar un problema nuevo eligiendo **ayuda** > **enviar comentarios**   >  **Notificar un problema** en Visual Studio.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Problema: "Asociar a Snapshot Debugger" detecta un error de código de estado HTTP

Si ve el siguiente error en la **salida** ventana durante el intento de adjuntar, puede ser un problema conocido que se enumeran a continuación. Pruebe las soluciones propuestas y si el problema persiste en contacto con el alias de anterior.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>No autorizado (401)

Este error indica que la llamada REST emitido por Visual Studio para Azure usa una credencial no válida. Un problema conocido con el módulo de Azure Active Directory OAuth fácil puede producir este error.

Siga estos pasos:

* Asegúrese de que su cuenta de personalización de Visual Studio tiene permisos para la suscripción de Azure y recursos que va a adjuntar. Una forma rápida para determinar esto es comprobar si el recurso está disponible en el cuadro de diálogo de **depurar** > **asociar Snapshot Debugger...**   >  **Recursos de azure** > **seleccionar existente**, o en el explorador en la nube.
* Si este error persiste, utilice uno de los canales de comentarios que se describe al principio de este artículo.

### <a name="403-forbidden"></a>(403) prohibido

Este error indica que se deniega el permiso. Esto puede deberse a muchos motivos diferentes.

Siga estos pasos:

* Compruebe que la cuenta de Visual Studio tiene una suscripción válida a Azure con los permisos de Control de acceso basado en roles (RBAC) necesarios para el recurso. Para el servicio de aplicaciones, compruebe si tiene permisos para [consulta](https://docs.microsoft.com/rest/api/appservice/appserviceplans/get) el Plan de App Service hospeda la aplicación.
* Compruebe que la marca de tiempo de su equipo cliente es correcta y actualizada. Servidores con marcas de tiempo desactivado por más de 15 minutos de la marca de tiempo de solicitud normalmente producen este error.
* Si este error persiste, utilice uno de los canales de comentarios que se describe al principio de este artículo.

### <a name="404-not-found"></a>(404) no encontrado

Este error indica que no se encontró el sitio Web en el servidor.

Siga estos pasos:

* Compruebe que dispone de un sitio Web implementado y que se ejecutan en el que se está asociando al recurso de App Service.
* Compruebe que el sitio está disponible en https://\<recursos\>. azurewebsites.net
* Si este error persiste, utilice uno de los canales de comentarios que se describe al principio de este artículo.

### <a name="406-not-acceptable"></a>(406) no es aceptable

Este error indica que el servidor no puede responder en el tipo establecido en el encabezado Accept de la solicitud.

Siga estos pasos:

* Compruebe que el sitio está disponible en https://\<recursos\>. azurewebsites.net
* Compruebe que el sitio no ha migrado a las nuevas instancias. Depurador de instantáneas usa la noción de ARRAffinity para enrutar las solicitudes a instancias específicas que pueden producir este error de forma intermitente.
* Si este error persiste, utilice uno de los canales de comentarios que se describe al principio de este artículo.

### <a name="409-conflict"></a>Conflicto (409)

Este error indica que la solicitud entra en conflicto con el estado actual del servidor.

Se trata de un problema conocido que se produce cuando un usuario intenta asociar a Snapshot Debugger contra una instancia de App Service que ha habilitado Application Insights. Application Insights establece AppSettings con un uso de mayúsculas y minúsculas diferente de Visual Studio, el causante del problema.

::: moniker range=">= vs-2019"
Nos hemos resuelto en Visual Studio de 2019.
::: moniker-end

Siga estos pasos:

::: moniker range="vs-2017"

* Compruebe en el portal de Azure que están en mayúscula AppSettings para Snapshot Debugger (SNAPSHOTDEBUGGER_EXTENSION_VERSION) y InstrumentationEngine (INSTRUMENTATIONENGINE_EXTENSION_VERSION). Si no, actualice la configuración manualmente, lo que fuerza un reinicio del sitio.
::: moniker-end
* Si este error persiste, utilice uno de los canales de comentarios que se describe al principio de este artículo.

### <a name="500-internal-server-error"></a>Error interno del servidor (500)

Este error indica que el sitio está totalmente fuera de servicio o el servidor no puede atender la solicitud. Instantánea depurador sólo funciona en la ejecución de aplicaciones. [Application Insights Snapshot Debugger](https://docs.microsoft.com/azure/azure-monitor/app/snapshot-debugger) proporciona la toma de instantáneas en las excepciones y puede ser la mejor herramienta para sus necesidades.

### <a name="502-bad-gateway"></a>Puerta de enlace incorrecta (502)

Este error indica un problema de red de servidor y puede ser temporal.

Siga estos pasos:

* Intente esperar unos minutos antes de adjuntar al depurador de instantáneas de nuevo.
* Si este error persiste, utilice uno de los canales de comentarios que se describe al principio de este artículo.

## <a name="issue-snappoint-does-not-turn-on"></a>Problema: Punto de acoplamiento no activa

Si ve un icono de advertencia ![icono de advertencia de punto de instantánea](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "icono de advertencia de punto de instantánea") con el punto de instantánea en lugar del icono de punto de instantánea habitual, significa que el punto de instantánea no está activo.

![El punto de instantánea no está activo](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "El punto de instantánea no está activo")

Siga estos pasos:

1. Asegúrese de que tiene la misma versión de código fuente que se usó para crear e implementar la aplicación. Asegúrese de que va a cargar los símbolos correctos para su implementación. Para ello, vea la ventana **Módulos** mientras se lleva a cabo la depuración de instantáneas y verifique si la columna Archivo de símbolo muestra un archivo .pdb cargado para el módulo que va a depurar. Snapshot Debugger intentará descargar automáticamente y usar los símbolos para la implementación.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problema: No se cargan los símbolos al abrir una instantánea

Si ve la siguiente ventana, significa que los símbolos no se cargan.

![Los símbolos no se cargan](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Los símbolos no se cargan")

Siga estos pasos:

- Haga clic en el vínculo **Cambiar configuración de símbolos...** en esta página. En la configuración **Depuración > Símbolo**, agregue un directorio de caché de símbolos. Reinicie la depuración de instantáneas una vez establecida la ruta de acceso a los símbolos.

   Los símbolos o los archivos .pdb disponibles en el proyecto deben coincidir con la implementación de App Service. La mayoría de las implementaciones (implementación mediante Visual Studio, CI/CD con Azure Pipelines o Kudu, etc.) publicarán los archivos de símbolo en App Service. La configuración del directorio de caché de símbolos permite a Visual Studio usar estos símbolos.

   ![Configuración de símbolos](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Configuración de símbolos")

- Como alternativa, si la organización usa un servidor de símbolos o cambia los símbolos a una ruta de acceso distinta, use la configuración de símbolos para cargar los símbolos correctos para su implementación.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problema: No puedo ver la opción de "Adjuntar depurador de instantáneas" en el explorador en la nube

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

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problema: Sólo se ve limitado instantáneas en las herramientas de diagnóstico

![Punto de instantánea limitado](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Punto de instantánea limitado")

Siga estos pasos:

- Las instantáneas ocupan poco memoria pero tienen una carga de confirmación. Si Snapshot Debugger detecta que el servidor soporta una carga de memoria pesada, no realizará instantáneas. Puede eliminar las instantáneas que ya están capturadas; para ello, detenga la sesión de Snapshot Debugger y vuelva a intentarlo.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problema: Depuración de instantáneas con varias versiones de Visual Studio genera errores

2019 de Visual Studio requiere una versión más reciente de la extensión del sitio Snapshot Debugger en Azure App Service.  Esta versión no es compatible con la versión anterior de la extensión del sitio Snapshot Debugger usa Visual Studio 2017.  Si intenta asociar al depurador de instantáneas de 2019 de Visual Studio a Azure App Service que se ha depurado anteriormente por el depurador de instantáneas en Visual Studio 2017, obtendrá el siguiente error:

![Extensión del sitio Snapshot Debugger incompatible 2019 de Visual Studio](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "extensión del sitio Incompatible Snapshot Debugger 2019 de Visual Studio")

Por el contrario, si usa Visual Studio 2017 para adjuntar al depurador de instantáneas a Azure App Service que se han depurado anteriormente por el depurador de instantáneas en Visual Studio de 2019, obtendrá el siguiente error:

![Extensión del sitio Snapshot Debugger no compatible de Visual Studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "extensión del sitio Incompatible Snapshot Debugger Visual Studio 2017")

Para solucionar este problema, elimine la siguiente configuración de la aplicación en Azure Portal y vuelva a adjuntar Snapshot Debugger:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problema: Tengo problemas de depuración de instantáneas y tengo que habilitar el registro más

### <a name="enable-agent-logs"></a>Habilitar los registros del agente

Para habilitar y deshabilitar los registros del agente, abra Visual Studio y vaya a *Herramientas>Opciones>Snapshot Debugger>Habilitar el registro del agente*. Tenga en cuenta que, si la opción *Eliminar registros del agente anterior en el inicio de sesión* también está habilitada, cada vinculación correcta de Visual Studio eliminará los registros anteriores del agente.

Los registros del agente se pueden encontrar en las ubicaciones siguientes:

- App Services:
  - Vaya al sitio de Kudu en App Service, es decir, yourappservice.**scm**.azurewebsites.net, y acceda a la consola de depuración.
  - Registros del agente se almacenan en el directorio siguiente:  D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- VM/VMSS:
  - Inicie sesión en la máquina virtual, el agente de los registros se almacenan como sigue:  C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics\<Version>\SnapshotDebuggerAgent_*.txt
- AKS
  - Vaya al siguiente directorio: /tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>Habilitar los registros de instrumentación y del generador de perfiles

Los registros de instrumentación pueden encontrarse en las siguientes ubicaciones:

- App Services:
  - Registro de errores se envía automáticamente a D:\Home\LogFiles\eventlog.xml, los eventos se marcan con `<Provider Name="Instrumentation Engine" />` o "Puntos de interrupción de producción"
- VM/VMSS:
  - Inicie sesión en la máquina virtual y abra el Visor de eventos.
  - Abra la vista siguiente: *Los registros de Windows > aplicación*.
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

- [Depurar en Visual Studio](../debugger/index.md)
- [Depurar aplicaciones ASP.NET activas con el depurador de instantáneas](../debugger/debug-live-azure-applications.md)
- [Depuración en directo ASP.NET Azure Virtual Machines\Virtual máquinas conjuntos de escalado mediante el depurador de instantáneas](../debugger/debug-live-azure-virtual-machines.md)
- [Depuración en directo ASP.NET Azure Kubernetes con el depurador de instantáneas](../debugger/debug-live-azure-kubernetes.md)
- [P+F sobre depuración de instantáneas](../debugger/debug-live-azure-apps-faq.md)
