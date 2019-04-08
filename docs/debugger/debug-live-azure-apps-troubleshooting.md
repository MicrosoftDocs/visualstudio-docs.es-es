---
title: Solución de problemas de depuración de instantáneas | Microsoft Docs
ms.custom: seodec18
ms.date: 11/07/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b7916cbd3a7faa633baf53a18686779dc2b386c
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857767"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Solución de problemas y problemas conocidos de depuración de instantáneas en Visual Studio

Si los pasos descritos en este artículo no resuelven el problema, póngase en contacto con snaphelp@microsoft.com.

## <a name="issue-snappoint-does-not-turn-on"></a>Problema: Punto de instantánea no activo

Si ve un icono de advertencia ![icono de advertencia de punto de instantánea](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "icono de advertencia de punto de instantánea") con el punto de instantánea en lugar del icono de punto de instantánea habitual, significa que el punto de instantánea no está activo.

![El punto de instantánea no está activo](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "El punto de instantánea no está activo")

Siga estos pasos:

1. Asegúrese de que tiene la misma versión de código fuente que se usó para crear e implementar su app.isua1. Asegúrese de que va a cargar los símbolos correctos para su implementación. Para ello, vea la ventana **Módulos** mientras se lleva a cabo la depuración de instantáneas y verifique si la columna Archivo de símbolo muestra un archivo .pdb cargado para el módulo que va a depurar. Snapshot Debugger intentará descargar automáticamente y usar los símbolos para la implementación.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problema: Los símbolos no se cargan al abrir una instantánea

Si ve la siguiente ventana, significa que los símbolos no se cargan.

![Los símbolos no se cargan](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Los símbolos no se cargan")

Siga estos pasos:

- Haga clic en el vínculo **Cambiar configuración de símbolos...** en esta página. En la configuración **Depuración > Símbolo**, agregue un directorio de caché de símbolos. Reinicie la depuración de instantáneas una vez establecida la ruta de acceso a los símbolos.

   Los símbolos o los archivos .pdb disponibles en el proyecto deben coincidir con la implementación de App Service. La mayoría de las implementaciones (implementación mediante Visual Studio, CI/CD con Azure Pipelines o Kudu, etc.) publicarán los archivos de símbolo en App Service. La configuración del directorio de caché de símbolos permite a Visual Studio usar estos símbolos.

   ![Configuración de símbolos](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Configuración de símbolos")

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

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problema: Solo veo instantáneas limitadas en las herramientas de diagnóstico

![Punto de instantánea limitado](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Punto de instantánea limitado")

Siga estos pasos:

- Las instantáneas ocupan poco memoria pero tienen una carga de confirmación. Si Snapshot Debugger detecta que el servidor soporta una carga de memoria pesada, no realizará instantáneas. Puede eliminar las instantáneas que ya están capturadas; para ello, detenga la sesión de Snapshot Debugger y vuelva a intentarlo.

## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problema: La depuración de instantáneas con varias versiones de Visual Studio genera errores

VS 2019 requiere una versión más reciente de la extensión de sitio de Snapshot Debugger en la instancia de Azure App Service.  Esta versión no es compatible con la versión anterior de la extensión de sitio de Snapshot Debugger que usa VS 2017.  Obtendrá el siguiente error si intenta adjuntar Snapshot Debugger en VS 2019 a una instancia de Azure App Service que se depuró anteriormente con Snapshot Debugger en VS 2017:

![Extensión de sitio de Snapshot Debugger incompatible con VS 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "Extensión de sitio de Snapshot Debugger incompatible con VS 2019")

Por el contrario, si usa VS 2017 para adjuntar Snapshot Debugger a una instancia de Azure App Service que se depuró anteriormente con Snapshot Debugger en VS 2019, obtendrá el siguiente error:

![Extensión de sitio de Snapshot Debugger incompatible con VS 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "Extensión de sitio de Snapshot Debugger incompatible con VS 2017")

Para solucionar este problema, elimine la siguiente configuración de la aplicación en Azure Portal y vuelva a adjuntar Snapshot Debugger:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problema: Tengo problemas con la depuración de instantáneas y necesito habilitar más registros

### <a name="enable-agent-logs"></a>Habilitar los registros del agente

Para habilitar y deshabilitar los registros del agente, abra Visual Studio y vaya a *Herramientas>Opciones>Snapshot Debugger>Habilitar el registro del agente*. Tenga en cuenta que, si la opción *Eliminar registros del agente anterior en el inicio de sesión* también está habilitada, cada vinculación correcta de Visual Studio eliminará los registros anteriores del agente.

Los registros del agente se pueden encontrar en las ubicaciones siguientes:

- App Services:
  - Vaya al sitio de Kudu en App Service, es decir, yourappservice.**scm**.azurewebsites.net, y acceda a la consola de depuración.
  - Los registros del agente se almacenan en el siguiente directorio: D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- VM/VMSS:
  - Inicie sesión en la máquina virtual; los registros del agente se almacenan en la siguiente ubicación: C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics\<Version>\SnapshotDebuggerAgent_*.txt
- AKS
  - Vaya al siguiente directorio: /tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>Habilitar los registros de instrumentación y del generador de perfiles

Los registros de instrumentación pueden encontrarse en las siguientes ubicaciones:

- App Services:
  - Los registros de errores se envían automáticamente a D:\Home\LogFiles\eventlog.xml, los eventos se marcan como <<Nombre de proveedor="Motor de instrumentación" //>> o "Puntos de interrupción de producción"
- VM/VMSS:
  - Inicie sesión en la máquina virtual y abra el Visor de eventos.
  - Abra la siguiente vista: *Registros de Windows>Aplicación*.
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
- [Depuración de aplicaciones ASP.NET en vivo con Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Depuración de aplicaciones ASP.NET en vivo en Azure Virtual Machines\Virtual Machines Scale Sets con Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Depuración de Azure Kubernetes de ASP.NET en vivo con Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Preguntas frecuentes sobre depuración de instantáneas](../debugger/debug-live-azure-apps-faq.md)