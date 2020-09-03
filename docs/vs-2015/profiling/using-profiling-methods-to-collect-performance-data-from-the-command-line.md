---
title: Usar métodos de generación de perfiles para recopilar datos de rendimiento desde la línea de comandos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fe9e8d3dbd1e7395287cd7241f1e6145dffca7e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145393"
---
# <a name="using-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Usar métodos de generación de perfiles para recopilar datos de rendimiento desde la línea de comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La elección de herramientas de línea de comandos y opciones de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] depende de factores como el tipo de aplicación de la que está generando perfiles, el método de generación de perfiles que desea utilizar y si se escribe la aplicación de destino en código nativo o de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
 En este tema se organiza los temas de procedimientos de línea de comandos según el método de generación de perfiles que elija.  
  
## <a name="in-this-topic"></a>En este tema  
 [Usar el método de muestreo para recopilar estadísticas de rendimiento](#BKMK_Using_the_sampling_method_to_collect_performance_statistics)  
  
 [Usar el método de instrumentación para recopilar datos detallados de control de tiempo](#BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data)  
  
 [Usar métodos de memoria de .NET para recopilar datos de asignación de memoria y de duración de objetos](#BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data)  
  
 [Usar el método de simultaneidad para recopilar datos de contención de recursos y de actividad de subprocesos](#BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data)  
  
 [Agregar datos de interacción de capas a una ejecución de generación de perfiles](#BKMK_Adding_tier_interaction_data_to_a_profiling_run)  
  
## <a name="using-the-sampling-method-to-collect-performance-statistics"></a><a name="BKMK_Using_the_sampling_method_to_collect_performance_statistics"></a> Usar el método de muestreo para recopilar estadísticas de rendimiento  
 El método de muestreo de las herramientas de generación de perfiles recopila datos de rendimiento a intervalos especificados en un proceso de generación de perfiles. Los datos de muestreo pueden proporcionar información sobre los problemas de rendimiento relacionadas con la CPU y pueden ser una buena forma de empezar a explorar el rendimiento de una aplicación.  
  
 Puede iniciar el generador de perfiles y la aplicación al mismo tiempo, o puede adjuntar el generador de perfiles a una instancia en ejecución de una aplicación.  
  
|Tarea|Tipo de aplicación de destino|  
|----------|-----------------------------|  
|**Inicio de una aplicación**|-   [Aplicaciones independientes](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Adjuntar a un proceso en ejecución**|-   [Aplicaciones independientes de .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Aplicaciones independientes nativas](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Aplicaciones Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [.NET Services](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Servicios nativos](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="using-the-instrumentation-method-to-collect-detailed-timing-data"></a><a name="BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data"></a> Usar el método de instrumentación para recopilar datos de tiempo detallados  
 El método de instrumentación de las herramientas de generación de perfiles recopila datos de rendimiento de copias de binarios de aplicación que contienen sondeos de software para registrar información de rendimiento. Los datos de instrumentación se recopilan al comienzo y al final de cada función instrumentada y en cada llamada a otras funciones desde la función instrumentada. El método de instrumentación es útil para detectar problemas de rendimiento con problemas de E/S como el uso de disco.  
  
 El binario instrumentado se crea con la herramienta [VInstr.exe](../profiling/vsinstr.md). Después de inicializar el generador de perfiles, los datos se recopilan automáticamente desde los binarios instrumentados al ejecutar la aplicación de destino.  
  
 **Tipo de aplicación de destino**  
  
- [Componentes independientes de .NET Framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
- [Componentes independientes nativos](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
- [Aplicaciones web ASP.NET compiladas estáticamente](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
- [Aplicaciones web ASP.NET compiladas dinámicamente](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
- [.NET Services](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
- [Servicios nativos](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
## <a name="using-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a><a name="BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data"></a> Usar métodos de memoria de .NET para recopilar datos de asignación de memoria y de duración de objetos  
 El método de memoria de .NET de herramientas de generación de perfiles permite recopilar datos de asignación de memoria de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] e información sobre la duración de objetos en el [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
 Puede iniciar la aplicación de destino mediante el generador de perfiles, adjuntar el generador de perfiles a una instancia en ejecución de una aplicación y crear versiones instrumentadas de la aplicación para recopilar información de tiempo detallada junto con los datos de memoria de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
|Tarea|Tipo de aplicación de destino|  
|----------|-----------------------------|  
|**Inicio de una aplicación**|-   [Aplicaciones de .NET Framework independiente](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line.md)|  
|**Adjuntar a un proceso en ejecución**|-   [Aplicaciones independientes de .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Aplicaciones Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [.NET Services](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrumentar módulos**|-   [.NET Framework componentes independientes](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line.md)<br />-   [Aplicaciones web ASP.NET compiladas estáticamente](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Aplicaciones web ASP.NET compiladas dinámicamente](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [.NET Services](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## <a name="using-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a><a name="BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data"></a> Usar el método de simultaneidad para recopilar datos de contención de recursos y de actividad de subprocesos  
 El método de simultaneidad de las herramientas de generación de perfiles permite recopilar la contención de recursos y datos de actividad de procesos y subprocesos de aplicaciones multiproceso.  
  
 Puede iniciar la aplicación mediante el generador de perfiles, o puede adjuntar el generador de perfiles a una instancia en ejecución de una aplicación.  
  
|Tarea|Tipo de aplicación de destino|  
|----------|-----------------------------|  
|**Inicio de una aplicación**|-   [Aplicación de .NET Framework independiente](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Aplicación de .NET Framework nativa](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Adjuntar a un proceso en ejecución**|-   [Aplicación independiente de .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Aplicación independiente nativa](/visualstudio/profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data?view=vs-2015)<br />-   [Aplicación Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Servicio .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Servicio nativo](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="adding-tier-interaction-data-to-a-profiling-run"></a><a name="BKMK_Adding_tier_interaction_data_to_a_profiling_run"></a> Agregar datos de interacción de capas a una ejecución de generación de perfiles  
 Agregar datos de interacción de capas a una ejecución de generación de perfiles requiere procedimientos concretos con las Herramientas de generación de perfiles de la línea de comandos. Vea [recopilar datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md)  
  
## <a name="see-also"></a>Consulte también  
 [Generar perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generación de perfiles de servicios](../profiling/command-line-profiling-of-services.md)
