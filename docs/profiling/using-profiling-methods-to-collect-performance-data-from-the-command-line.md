---
title: "Usar m&#233;todos de generaci&#243;n de perfiles para recopilar datos de rendimiento desde la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Usar m&#233;todos de generaci&#243;n de perfiles para recopilar datos de rendimiento desde la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La elección de opciones y herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] depende de factores como el tipo de aplicación para la que se generan perfiles, del método de generación de perfiles que desea usar y de si la aplicación de destino está escrita en código nativo o de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 En este tema se organizan los temas de procedimientos de línea de comandos en función del método de generación de perfiles que se elige.  
  
## En este tema  
 [Usar el método de muestreo para recopilar estadísticas de rendimiento](#BKMK_Using_the_sampling_method_to_collect_performance_statistics)  
  
 [Usar el método de instrumentación para recopilar datos de tiempo detallados](#BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data)  
  
 [Usar métodos de memoria de .NET para recopilar datos de asignación de memoria y de duración de objetos](#BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data)  
  
 [Usar el método de simultaneidad para recopilar datos de contención de recursos y de actividad de subprocesos](#BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data)  
  
 [Agregar datos de interacción de capas a una ejecución de generación de perfiles](#BKMK_Adding_tier_interaction_data_to_a_profiling_run)  
  
##  <a name="BKMK_Using_the_sampling_method_to_collect_performance_statistics"></a> Usar el método de muestreo para recopilar estadísticas de rendimiento  
 El método de muestreo de las herramientas de generación de perfiles recopila datos de rendimiento a intervalos especificados en una ejecución de generación de perfiles.  Los datos de muestreo pueden proporcionar información detallada sobre problemas de rendimiento relacionados con CPU y constituyen un método adecuado para comenzar a explorar el rendimiento de una aplicación.  
  
 Puede iniciar el generador de perfiles y la aplicación al mismo tiempo o bien puede adjuntar el generador de perfiles a una instancia en ejecución de una aplicación.  
  
|Tarea|Tipo de aplicación de destino|  
|-----------|-----------------------------------|  
|**Iniciar una aplicación**|-   [Aplicaciones independientes](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Adjuntar a un proceso en ejecución**|-   [Aplicaciones independientes de .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Aplicaciones independientes nativas](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20Native%20Stand-Alone%20Application%20and%20Collect%20Application%20Statistics%20by%20Using%20the%20Command%20Line.md)<br />-   [Aplicaciones Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Servicios de .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Servicios nativos](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data"></a> Usar el método de instrumentación para recopilar datos de tiempo detallados  
 El método de instrumentación de las herramientas de generación de perfiles recopila datos de rendimiento de las copias de los archivos binarios de la aplicación que contienen sondeos de software para grabar información sobre el rendimiento.  Los datos de instrumentación se recopilan al comienzo y al final de cada función instrumentada y en cada llamada a otras funciones desde la función instrumentada.  El método de instrumentación es útil para detectar problemas de rendimiento debidos a problemas de E\/S como el uso del disco.  
  
 El archivo binario instrumentado se crea con la herramienta [VInstr.exe](../profiling/vsinstr.md).  Después de inicializar el generador de perfiles, los datos se recopilan automáticamente de los archivos binarios instrumentados al ejecutar la aplicación de destino.  
  
 **Tipo de aplicación de destino**  
  
-   [Componentes independientes de .NET Framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Componentes independientes nativos](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Aplicaciones web ASP.NET compiladas estáticamente](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
-   [Aplicaciones web ASP.NET compiladas dinámicamente](../Topic/How%20to:%20Instrument%20a%20Dynamically%20Compiled%20ASP.NET%20Web%20Application%20and%20Collect%20Detailed%20Timing%20Data%20with%20the%20Profiler%20by%20Using%20the%20Command%20Line.md)  
  
-   [Servicios de .NET](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
-   [Servicios nativos](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
##  <a name="BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data"></a> Usar métodos de memoria de .NET para recopilar datos de asignación de memoria y de duración de objetos  
 El método de memoria de .NET de las herramientas de generación de perfiles permite recopilar datos de asignación de memoria de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] e información sobre la duración de los objetos en [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Puede iniciar la aplicación de destino con el generador de perfiles, puede adjuntar el generador de perfiles a una instancia en ejecución de una aplicación y puede crear versiones instrumentadas de la aplicación para recopilar información de tiempos junto con los datos de memoria de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
|Tarea|Tipo de aplicación de destino|  
|-----------|-----------------------------------|  
|**Iniciar una aplicación**|-   [Aplicaciones de .NET Framework independientes](../Topic/How%20to:%20Launch%20a%20Stand-Alone%20.NET%20Framework%20Application%20with%20the%20Profiler%20to%20Collect%20Memory%20Data%20by%20Using%20the%20Command%20Line.md)|  
|**Adjuntar a un proceso en ejecución**|-   [Aplicaciones independientes de .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Aplicaciones Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Servicios de .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrumentar módulos**|-   [Componentes independientes de .NET Framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line.md)<br />-   [Aplicaciones web ASP.NET compiladas estáticamente](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Aplicaciones web ASP.NET compiladas dinámicamente](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Servicios de .NET](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
##  <a name="BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data"></a> Usar el método de simultaneidad para recopilar datos de contención de recursos y de actividad de subprocesos  
 El método de simultaneidad de las herramientas de generación de perfiles permite recopilar datos de contención de recursos y de actividad de procesos y subprocesos de aplicaciones multiproceso.  
  
 Puede iniciar la aplicación mediante el generador de perfiles o bien puede adjuntar el generador de perfiles a una instancia en ejecución de una aplicación.  
  
|Tarea|Tipo de aplicación de destino|  
|-----------|-----------------------------------|  
|**Iniciar una aplicación**|-   [Aplicación de .NET Framework independiente](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Aplicación nativa independiente](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Adjuntar a un proceso en ejecución**|-   [Aplicación independiente de .NET Framework](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20.NET%20Framework%20Stand-Alone%20Application%20to%20Collect%20Concurrency%20Data%20by%20Using%20the%20Command%20Line.md)<br />-   [Aplicación independiente nativa](../Topic/How%20to:%20Attach%20the%20Profiler%20to%20a%20Native%20Stand-Alone%20Application%20and%20Collect%20Concurrency%20Data%20by%20Using%20the%20Command%20Line.md)<br />-   [Aplicación Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Servicio de .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Servicio nativo](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Adding_tier_interaction_data_to_a_profiling_run"></a> Agregar datos de interacción de capas a una ejecución de generación de perfiles  
 Agregar datos de interacción de capas a una ejecución de generación de perfiles requiere procedimientos concretos con las Herramientas de generación de perfiles de la línea de comandos.  Vea [Recopilar datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
## Vea también  
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)