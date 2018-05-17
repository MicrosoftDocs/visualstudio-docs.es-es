---
title: Usar métodos de generación de perfiles para recopilar datos de rendimiento desde la línea de comandos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6a9c87de9f5815496d29bfa212fbc5ee204b2c10
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="using-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Usar métodos de generación de perfiles para recopilar datos de rendimiento desde la línea de comandos
La elección de herramientas de línea de comandos y opciones de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] depende de factores como el tipo de aplicación de la que está generando perfiles, el método de generación de perfiles que desea utilizar y si se escribe la aplicación de destino en código nativo o de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 En este tema se organiza los temas de procedimientos de línea de comandos según el método de generación de perfiles que elija.  
  
## <a name="in-this-topic"></a>En este tema  
 [Usar el método de muestreo para recopilar estadísticas de rendimiento](#BKMK_Using_the_sampling_method_to_collect_performance_statistics)  
  
 [Usar el método de instrumentación para recopilar datos de tiempo detallados](#BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data)  
  
 [Usar métodos de memoria de .NET para recopilar datos de asignación de memoria y de duración de objetos](#BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data)  
  
 [Usar el método de simultaneidad para recopilar datos de contención de recursos y de actividad de subprocesos](#BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data)  
  
 [Agregar datos de interacción de capas a una ejecución de generación de perfiles](#BKMK_Adding_tier_interaction_data_to_a_profiling_run)  
  
##  <a name="BKMK_Using_the_sampling_method_to_collect_performance_statistics"></a> Usar el método de muestreo para recopilar estadísticas de rendimiento  
 El método de muestreo de las herramientas de generación de perfiles recopila datos de rendimiento a intervalos especificados en un proceso de generación de perfiles. Los datos de muestreo pueden proporcionar información sobre los problemas de rendimiento relacionadas con la CPU y pueden ser una buena forma de empezar a explorar el rendimiento de una aplicación.  
  
 Puede iniciar el generador de perfiles y la aplicación al mismo tiempo, o puede adjuntar el generador de perfiles a una instancia en ejecución de una aplicación.  
  
|Tarea|Tipo de aplicación de destino|  
|----------|-----------------------------|  
|**Ejecutar una aplicación**|-   [Aplicaciones independientes](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Adjuntar a un proceso en ejecución**|-   [Aplicaciones independientes de .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)<br />-   [Aplicaciones independientes nativas](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Aplicaciones web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [.NET Services](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Servicios nativos](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data"></a> Usar el método de instrumentación para recopilar datos de tiempo detallados  
 El método de instrumentación de las herramientas de generación de perfiles recopila datos de rendimiento de copias de binarios de aplicación que contienen sondeos de software para registrar información de rendimiento. Los datos de instrumentación se recopilan al comienzo y al final de cada función instrumentada y en cada llamada a otras funciones desde la función instrumentada. El método de instrumentación es útil para detectar problemas de rendimiento con problemas de E/S como el uso de disco.  
  
 El binario instrumentado se crea con la herramienta [VInstr.exe](../profiling/vsinstr.md). Después de inicializar el generador de perfiles, los datos se recopilan automáticamente desde los binarios instrumentados al ejecutar la aplicación de destino.  
  
 **Tipo de aplicación de destino**  
  
-   [Componentes independientes de .NET Framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Componentes independientes nativos](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Aplicaciones web ASP.NET compiladas estáticamente](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)  
  
-   [Aplicaciones web ASP.NET compiladas dinámicamente](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)  
  
-   [.NET Services](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
-   [Servicios nativos](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
##  <a name="BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data"></a> Usar métodos de memoria de .NET para recopilar datos de asignación de memoria y de duración de objetos  
 El método de memoria de .NET de herramientas de generación de perfiles permite recopilar datos de asignación de memoria de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] e información sobre la duración de objetos en el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Puede iniciar la aplicación de destino mediante el generador de perfiles, adjuntar el generador de perfiles a una instancia en ejecución de una aplicación y crear versiones instrumentadas de la aplicación para recopilar información de tiempo detallada junto con los datos de memoria de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
|Tarea|Tipo de aplicación de destino|  
|----------|-----------------------------|  
|**Ejecutar una aplicación**|-   [Aplicaciones de .NET Framework independiente](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line.md)|  
|**Adjuntar a un proceso en ejecución**|-   [Aplicaciones independientes de .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Aplicaciones web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [.NET Services](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrumentar módulos**|-   [Componentes independientes de .NET Framework](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-memory-data.md)<br />-   [Aplicaciones web ASP.NET compiladas estáticamente](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Aplicaciones web ASP.NET compiladas dinámicamente](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [.NET Services](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
##  <a name="BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data"></a> Usar el método de simultaneidad para recopilar datos de contención de recursos y de actividad de subprocesos  
 El método de simultaneidad de las herramientas de generación de perfiles permite recopilar la contención de recursos y datos de actividad de procesos y subprocesos de aplicaciones multiproceso.  
  
 Puede iniciar la aplicación mediante el generador de perfiles, o puede adjuntar el generador de perfiles a una instancia en ejecución de una aplicación.  
  
|Tarea|Tipo de aplicación de destino|  
|----------|-----------------------------|  
|**Ejecutar una aplicación**|-   [Aplicación de .NET Framework independiente](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)<br />-   [Aplicación de .NET Framework nativa](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Adjuntar a un proceso en ejecución**|-   [Aplicación independiente de .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)<br />-   [Aplicación independiente nativa](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Aplicación web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [.NET Service](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Servicio nativo](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Adding_tier_interaction_data_to_a_profiling_run"></a> Agregar datos de interacción de capas a una ejecución de generación de perfiles  
 Agregar datos de interacción de capas a una ejecución de generación de perfiles requiere procedimientos concretos con las Herramientas de generación de perfiles de la línea de comandos. Consulte [Recopilar datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md)  
  
## <a name="see-also"></a>Vea también  
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)