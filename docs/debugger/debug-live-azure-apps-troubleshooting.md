---
title: "Solución de problemas y problemas conocidos para la depuración instantánea | Documentos de Microsoft"
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d007bdf5d2029e896167a2fd7b32359c661aa7fa
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2018
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Problemas conocidos y solución de problemas de instantáneas de depuración en Visual Studio

Si los pasos descritos en este tema no resuelven el problema, póngase en contacto con snaphelp@microsoft.com.

## <a name="issue-snappoint-does-not-turn-on"></a>Problema: Snappoint no activar

Si aparece un icono de advertencia ![icono de advertencia de Snappoint](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "icono de advertencia Snappoint") con su snappoint en lugar del icono normal snappoint, a continuación, el snappoint no está activado.

![No activar Snappoint](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Snappoint no activar")

Siga estos pasos:

1. Asegúrese de que tiene la misma versión de código fuente que se usó para generar e implementar su app.isua1. Asegúrese de que va a cargar los símbolos correctos para su implementación. Para ello, vea la **módulos** ventana al depurar de instantánea y compruebe que la columna del archivo de símbolos muestra un archivo .pdb cargados para el módulo que se está depurando. Tenga en cuenta que el depurador de instantánea intentará descargar automáticamente y usar símbolos para la implementación.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problema: Símbolos no se cargan cuando se abre una instantánea

Si ve la siguiente ventana, no se cargó símbolos.

![No cargar símbolos](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "no cargar símbolos")

Siga estos pasos:

- Haga clic en el **cambiar la configuración de símbolos...** crear vínculos en esta página. En el **depuración > símbolo** configuración, agregue un directorio de caché de símbolos. Reinicie la depuración de instantánea después de que se ha establecido la ruta de acceso de símbolos.

   Los símbolos o .pdb (archivos), disponibles en el proyecto deben coincidir con la implementación del servicio de aplicación. Mayoría de las implementaciones (implementación a través de Visual Studio, CI/CD con VSTS o Kudu, etc.) se publicarán los archivos de símbolos a lo largo de su servicio en la aplicación. Establecer el directorio de caché de símbolos permite que Visual Studio usar estos símbolos.

   ![Configuración de símbolos](../debugger/media/snapshot-troubleshooting-symbol-settings.png "configuración de símbolos")

- O bien, si su organización usa un servidor de símbolos o quita los símbolos en una ruta de acceso diferente, utilice la configuración de símbolos para cargar los símbolos correctos para su implementación.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problema: no puedo ver la opción de "Adjuntar depurador de instantánea" en el Explorador de la nube

Siga estos pasos:

- Asegúrese de que está instalado el componente del depurador de instantánea. Abra el instalador de Visual Studio y compruebe el **depurador instantánea** componente en la carga de trabajo de Azure.
- Asegúrese de que se admite la aplicación. Actualmente, solo ASP.NET (4.6.1+) y se admiten aplicaciones de ASP.NET Core (2.0 +) implementadas en los servicios de aplicación de Azure.

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problema: sólo se ve limitado instantáneas en las herramientas de diagnóstico

![Throttled snappoint](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "limitadas snappoint")

Siga estos pasos:

- Las instantáneas ocupan muy poca memoria, pero con un cargo de confirmación. Si el depurador de instantánea detecta que el servidor está bajo carga de mucha memoria, no tomará instantáneas. Puede eliminar las instantáneas ya capturadas deteniendo la sesión del depurador de instantánea y volver a intentarlo.

## <a name="known-issues"></a>Problemas conocidos

- No se admite actualmente la depuración instantánea con varios clientes de Visual Studio en el mismo servicio de aplicación.
- Optimizaciones de IL Roslyn no se admiten totalmente en los proyectos de ASP.NET Core. Para algunos proyectos de ASP.NET Core, no puede ver algunas de las variables o usar algunas de las variables en instrucciones condicionales. 
- Variables especiales, como *$FUNCTION* o *$CALLER*, no se puede evaluar en instrucciones condicionales o logpoints para los proyectos de ASP.NET Core.
- Depuración instantánea no funciona en los servicios de aplicaciones que tienen [almacenamiento en caché Local](/azure/app-service/app-service-local-cache) activado.
- Depurar aplicaciones de la API de instantánea no se admite actualmente.

## <a name="see-also"></a>Vea también

[Depurar en Visual Studio](../debugger/index.md)  
[Depurar aplicaciones ASP.NET en directo con el depurador de instantánea](../debugger/debug-live-azure-applications.md)  
[P+F sobre depuración de instantáneas](../debugger/debug-live-azure-apps-faq.md)  
