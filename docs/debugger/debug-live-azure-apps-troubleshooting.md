---
title: Solución de problemas de depuración de instantáneas | Microsoft Docs
ms.custom: seodec18
ms.date: 11/07/2017
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 817e6f31d9282caf77c9f403c7e5555075726d2d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54943804"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Solución de problemas y problemas conocidos para la instantánea de depuración en Visual Studio

Si los pasos descritos en este artículo no resuelve el problema, póngase en contacto con snaphelp@microsoft.com.

## <a name="issue-snappoint-does-not-turn-on"></a>Problema: Punto de acoplamiento no activa

Si ve un icono de advertencia ![icono de advertencia de punto de acoplamiento](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "icono de advertencia de punto de acoplamiento") con el punto de acoplamiento en lugar del icono de punto de acoplamiento regular, a continuación, el punto de acoplamiento no está activado.

![Punto de acoplamiento no activar](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "no activar el punto de acoplamiento")

Siga estos pasos:

1. Asegúrese de que tiene la misma versión de código fuente que se usó para crear e implementar su app.isua1. Asegúrese de que va a cargar los símbolos correctos para su implementación. Para ello, vea el **módulos** ventana mientras la depuración de instantáneas y compruebe que la columna del archivo de símbolos muestra un archivo .pdb cargado para el módulo que está depurando. El depurador de instantáneas intentará descargar automáticamente y usar los símbolos para la implementación.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problema: No se cargan los símbolos al abrir una instantánea

Si ve la siguiente ventana, los símbolos no se cargó.

![No se cargan los símbolos](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "no cargar símbolos")

Siga estos pasos:

- Haga clic en el **cambiar la configuración de símbolos...** vínculo de esta página. En el **depuración > símbolos** configuración, agregue un directorio de caché de símbolos. Reiniciar después de que se ha establecido la ruta de acceso de símbolos de depuración de instantáneas.

   Los símbolos o los archivos .pdb, disponibles en el proyecto deben coincidir con la implementación de App Service. La mayoría de las implementaciones (implementación a través de Visual Studio, CI/CD con canalizaciones de Azure o Kudu, etc.) se publicará a lo largo de los archivos de símbolos a App Service. Configuración del directorio de caché de símbolos permite que Visual Studio usar estos símbolos.

   ![Configuración de símbolos](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Lores")

- Como alternativa, si su organización usa un servidor de símbolos o quita los símbolos en una ruta de acceso diferente, utilice los valores de símbolos para cargar los símbolos para la implementación correctos.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problema: No puedo ver la opción de "Adjuntar depurador de instantáneas" en el explorador en la nube

Siga estos pasos:

- Asegúrese de que está instalado el componente del depurador de instantáneas. Abra el instalador de Visual Studio y compruebe el **Snapshot Debugger** componente en la carga de trabajo de Azure.
- Asegúrese de que se admite la aplicación. Actualmente, solo ASP.NET (4.6.1+) y son compatibles con las aplicaciones de ASP.NET Core (2.0 +) implementadas en Azure App Services.

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problema: Sólo se ve limitado instantáneas en las herramientas de diagnóstico

![Punto de acoplamiento limitado](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "limita el punto de acoplamiento")

Siga estos pasos:

- Las instantáneas ocupan poco memoria pero tienen un cargo de confirmación. Si el depurador de instantáneas detecta que el servidor está bajo carga pesada de memoria, no tomará instantáneas. Puede eliminar las instantáneas ya capturadas deteniendo la sesión del depurador de instantáneas y volver a intentarlo.

## <a name="known-issues"></a>Problemas conocidos

- No se admite actualmente la depuración de instantáneas con varios clientes de Visual Studio en el mismo App Service.
- Optimizaciones de IL Roslyn no son totalmente compatibles en proyectos de ASP.NET Core. Para algunos proyectos de ASP.NET Core, es posible que no podrá ver algunas de las variables o usar algunas de las variables en instrucciones condicionales. 
- Variables especiales, como *$FUNCTION* o *$CALLER*, no se puede evaluar en instrucciones condicionales o puntos de registro para los proyectos de ASP.NET Core.
- Depuración de instantáneas no funciona en los servicios de aplicaciones que tienen [almacenamiento en caché Local](/azure/app-service/app-service-local-cache) activado.
- Las aplicaciones de API de depuración de instantáneas no se admiten actualmente.

## <a name="site-extension-upgrade"></a>Actualización de la extensión de sitio

Depuración de instantáneas y Application Insights dependen de un ICorProfiler, que se carga en el proceso del sitio y hace que los problemas de bloqueo de archivos durante la actualización. Se recomienda este proceso para asegurarse de que no hay ningún tiempo de inactividad para el sitio de producción.

- Crear un [ranura de implementación](/azure/app-service/web-sites-staged-publishing) dentro del servicio de aplicación e implementar su sitio en la ranura.
- Intercambiar la ranura de producción desde el Explorador de nube en Visual Studio o desde el portal de Azure.
- Detener el sitio de la ranura. Esto le llevará unos segundos para terminar el proceso w3wp.exe de sitio de todas las instancias.
- Actualizar la extensión de sitio de la ranura desde el sitio de Kudu o el portal de Azure (*hoja de App Service > herramientas de desarrollo > Extensiones > actualizaciones*).
- Iniciar el sitio de la ranura. Se recomienda visitar el sitio para preparar a intentarlo.
- Intercambiar la ranura de producción.

## <a name="see-also"></a>Vea también

[Depurar en Visual Studio](../debugger/index.md)  
[Depurar aplicaciones ASP.NET activas con el depurador de instantáneas](../debugger/debug-live-azure-applications.md)  
[P+F sobre depuración de instantáneas](../debugger/debug-live-azure-apps-faq.md)  
