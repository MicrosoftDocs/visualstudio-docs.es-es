---
title: Herramientas de generación de perfiles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.diagnosticshub.overview
ms.assetid: 0fb6cd5d-e16a-4526-84a5-19e63c625bc5
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bcb230532da4a0b84ea0102d86534c28afe35558
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686220"
---
# <a name="profiling-tools"></a>Herramientas de generación de perfiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La generación de perfiles y las herramientas de diagnóstico le ayudan a diagnosticar el uso de CPU y memoria, y otros problemas de nivel de aplicación. Con estas herramientas, puede acumular datos (como valores de variables, llamadas a funciones y eventos) durante el tiempo que se ejecute la aplicación en el depurador. Puede ver el estado de su aplicación en distintos momentos de la ejecución del código.  
  
 Revise el resumen en la parte inferior para ver qué herramientas están disponibles para su tipo de proyecto (por ejemplo, escritorio, UWP, ASP.NET).  
  
 Puede obtener acceso a las herramientas de generación de perfiles mediante **Depurar/Windows/Mostrar herramientas de diagnóstico** para usar las herramientas durante la sesión de depuración, o mediante **Depurar/Generador de perfiles de rendimiento...** para realizar un análisis de rendimiento preciso.  Consulte [Running Profiling Tools With or Without the Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md) (Ejecución de herramientas de ejecución de perfiles con o sin el depurador) para obtener más información sobre los diferentes enfoques.  
  
 ![DebugDiagnosticsToolsMenu](../profiling/media/debugdiagnosticstoolsmenu.png "DebugDiagnosticsToolsMenu")  
  
 Consulte [What's New in Profiling Tools](../profiling/what-s-new-in-profiling-tools.md) (Novedades en las herramientas de generación de perfiles) para obtener información acerca de nuevas características de esta versión.  
  
 En las secciones siguientes se describen las diferentes herramientas de rendimiento que están disponibles en Visual Studio.  
  
## <a name="memory-usage"></a>Uso de memoria  
 ![DiagMemorySmall](../profiling/media/diagmemorysmall.png "DiagMemorySmall")  
  
 Busque pérdidas de memoria y memoria ineficaz durante la depuración con la herramienta **uso de memoria** . La herramienta le permite realizar instantáneas del montón de memoria nativo y administrado. Puede usar esta herramienta con aplicaciones de escritorio, aplicaciones universales de Windows y aplicaciones ASP.NET. La **herramienta uso de memoria** se puede ejecutar desde la ventana herramientas de **diagnóstico** durante la depuración (depurar **/ventanas/Mostrar herramientas de diagnóstico**) o fuera del depurador (**depurar/generador de perfiles de rendimiento...**). Vea  [uso de memoria y](../profiling/memory-usage.md) [uso de memoria sin depuración](https://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0) para obtener más información.  
  
## <a name="cpu-usage"></a>Uso de CPU  
 ![DiagCPUSmall](../profiling/media/diagcpusmall.png "DiagCPUSmall")  
  
 La herramienta **Uso de CPU** muestra que la CPU dedica tiempo a ejecutar el código C++, C#/VB y JavaScript.  Puede usar esta herramienta con aplicaciones de escritorio y aplicaciones universales de Windows, así como con aplicaciones de Azure App Services. La **herramienta uso de CPU** se puede ejecutar desde la ventana herramientas de **diagnóstico** durante la depuración (depurar **/ventanas/Mostrar herramientas de diagnóstico**) o fuera del depurador (**depurar/generador de perfiles de rendimiento...**). Consulte [uso de CPU](../profiling/cpu-usage.md) para obtener más información.  
  
## <a name="performance-explorer"></a>Explorador de rendimiento  
 ![PerfTools](../profiling/media/perftools.png "PerfTools")  
  
 El **Explorador de rendimiento** (**Depurar/Generador de perfiles/Explorador de rendimiento**) le permite usar muchas herramientas diferentes, incluidas **Muestreo de la CPU**,  **Instrumentación**, **Asignación de memoria de .NET**, y **Contención de recursos**. Puede usar las herramientas del Explorador de rendimiento con aplicaciones de escritorio y aplicaciones ASP.NET, pero no aplicaciones universales de Windows. Para obtener más información, consulte [Performance Explorer](../profiling/performance-explorer.md) (Explorador de rendimiento).  
  
## <a name="gpu-usage"></a>Uso de GPU  
 ![DiagGPUUsage](../profiling/media/diaggpuusage.png "DiagGPUUsage")  
  
 Use la herramienta [GPU Usage](../debugger/gpu-usage.md) para comprender mejor el uso de hardware de alto nivel de la aplicación Direct3D. Puede usar esta herramienta con aplicaciones de escritorio y aplicaciones universales de Windows, pero no con aplicaciones ASP.NET. La herramienta **Uso de GPU** se puede ejecutar desde la ventana **Herramientas de diagnóstico** durante la depuración (**Depurar/Mostrar herramientas de diagnóstico**) o fuera del depurador (**Depurar/Generador de perfiles de rendimiento...**).  
  
## <a name="application-timeline"></a>Escala de tiempo de la aplicación  
 ![DiagAppTimeline](../profiling/media/diagapptimeline.png "DiagAppTimeline")  
  
 La herramienta [Application Timeline](../profiling/application-timeline.md) le ayuda a mejorar el rendimiento de las aplicaciones XAML proporcionando una vista detallada del consumo de recursos. Puede usar la **Escala de tiempo de la aplicación** con aplicaciones de escritorio y aplicaciones universales de Windows, pero no con aplicaciones ASP.NET. La herramienta **Escala de tiempo de la aplicación** se puede ejecutar desde la ventana **Herramientas de diagnóstico** (**Depurar/Generador de perfiles de rendimiento...**).  
  
## <a name="perftips"></a>Sugerencias de rendimiento  
 ![DiagPerfTips](../profiling/media/diagperftips.png "DiagPerfTips")  
  
 Cuando el depurador detiene la ejecución en un punto de interrupción o en una operación de ejecución paso a paso, el tiempo transcurrido entre la interrupción y el punto de interrupción anterior aparece como una sugerencia en la ventana del editor. Estas [PerfTips](../profiling/perftips.md) le ayudan a supervisar y analizar el rendimiento de la aplicación durante la depuración. Puede ver **Sugerencias de rendimiento** en aplicaciones de escritorio, aplicaciones universales de Windows y aplicaciones ASP.NET.  
  
## <a name="javascript-memory"></a>Memoria de JavaScript  
 ![DiagJSMemory](../profiling/media/diagjsmemory.png "DiagJSMemory")  
  
 La herramienta [JavaScript Memory](../profiling/javascript-memory.md) le permite medir, evaluar y detectar problemas relacionados con el rendimiento en el código de destino mediante la recopilación de información de tiempos en la entrada y salida de cada función de la aplicación. Puede usar esta herramienta con aplicaciones HTML universales de Windows. El **Control de tiempo de función de JavaScript** se puede ejecutar desde la ventana **Herramientas de diagnóstico** (**Depurar/Generador de perfiles de rendimiento...**).  
  
## <a name="html-ui-responsiveness"></a>Capacidad de respuesta de IU HTML  
 ![DiagHTMLResp](../profiling/media/diaghtmlresp.png "DiagHTMLResp")  
  
 La herramienta [HTML UI responsiveness](../profiling/html-ui-responsiveness.md) le ayuda a aislar problemas de rendimiento de las aplicaciones, incluida la falta de capacidad de respuesta, tiempos de carga lentos y actualizaciones visuales menos frecuentes de lo esperado. Puede usar esta herramienta con aplicaciones HTML universales de Windows. La herramienta **Respuesta de IU de HTML** se puede ejecutar desde la ventana **Herramientas de diagnóstico** (**Depurar/Generador de perfiles de rendimiento...**).  
  
## <a name="intellitrace"></a>IntelliTrace  
 ![DiagIntelliTrace](../profiling/media/diagintellitrace.png "DiagIntelliTrace")  
  
 [IntelliTrace](../debugger/intellitrace.md) le permite registrar eventos específicos, examinar los datos en la ventana **Locales** durante los eventos de depurador y llamadas a funciones, y depurar errores que son difíciles de reproducir.  IntelliTrace es principalmente una herramienta de depuración, pero también proporciona información que puede usar para investigaciones de rendimiento. Solo puede usar esta herramienta en Visual Studio Enterprise, con aplicaciones de escritorio, aplicaciones universales de Windows y aplicaciones en C# de ASP.NET. Puede encontrar IntelliTrace en la ventana **Herramientas de diagnóstico** durante la depuración (**Depuración/Windows/Mostrar herramientas de diagnóstico**).  
  
## <a name="profiling-in-production"></a>Generación de perfiles en producción  
 El método recomendado para la generación de perfiles en producción es generar el perfil desde la [línea de comandos mediante vsperf.exe](../profiling/using-the-profiling-tools-from-the-command-line.md) para recopilar un perfil de la CPU. Para la compatibilidad con la generación de perfiles remota en Azure App Service, puede generar perfiles a través del [Explorador de servidores o el Portal de Kudu](https://azure.microsoft.com/blog/remote-profiling-support-in-azure-app-service/).  
  
## <a name="which-tool-should-i-use"></a>¿Qué herramienta debo usar?  
 En esta tabla se muestra una lista de las distintas herramientas que ofrece Visual Studio y los tipos de proyecto con los que las puede usar:  
  
|Herramienta de rendimiento|Escritorio de Windows|Universales de Windows o de la Tienda|ASP.NET|  
|----------------------|---------------------|------------------------------|-------------|  
|[Uso de memoria](../profiling/memory-usage.md)|sí|sí|No|  
|[Uso de CPU](../profiling/cpu-usage.md)|sí|sí|Solo Azure App Service|  
|[Uso de GPU](../debugger/gpu-usage.md)|sí|sí|no|  
|[Escala de tiempo de la aplicación](../profiling/application-timeline.md)|sí|sí|No|  
|[Sugerencias de rendimiento](../profiling/perftips.md)|sí|sí para XAML, no para HTML|No|  
|[Explorador de rendimiento](../profiling/performance-explorer.md)|sí|No|sí|  
|[IntelliTrace](../debugger/intellitrace.md)|Solo .NET Enterprise|Solo .NET Enterprise|Solo .NET Enterprise|  
|[HTML UI responsiveness](../profiling/html-ui-responsiveness.md)|No|sí para HTML, no para XAML|No|  
|[Memoria de JavaScript](../profiling/javascript-memory.md)|No|sí para HTML, no para XAML|No|  
  
## <a name="see-also"></a>Consulte también  
 [IDE de Visual Studio](../ide/visual-studio-ide.md)
