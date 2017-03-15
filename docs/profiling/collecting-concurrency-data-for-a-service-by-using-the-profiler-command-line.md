---
title: "Recopilar datos de simultaneidad para un servicio utilizando la l&#237;nea de comandos del generador de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Recopilar datos de simultaneidad para un servicio utilizando la l&#237;nea de comandos del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El método de simultaneidad de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite recopilar datos de contención de recursos y datos de actividad de subprocesos que muestran la utilización de la CPU, la contención de subprocesos, la migración de subprocesos, los retrasos de sincronización, las áreas de E\/S superpuesta y otros eventos del sistema.  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas.  Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección.  Vea [Generar perfiles de aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Tareas comunes  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Adjuntar a un servicio .NET en ejecución**|-   [Cómo: Adjuntar el generador de perfiles a un servicio .NET y recopilar datos de simultaneidad](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Agregar los datos de interacción de capas**|-   [Recopilar datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Adjuntar a un servicio C\/C\+\+ en ejecución**|-   [Cómo: Adjuntar el generador de perfiles a un servicio nativo y recopilar datos de simultaneidad](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## Tareas relacionadas  
  
### Generar perfiles en servicios de Windows  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Generar perfiles utilizando el método de muestreo**|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Generar perfiles utilizando el método de instrumentación**|-   [Recopilar datos de control de tiempo detallados utilizando la instrumentación](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Generar perfiles de asignación de memoria de .NET y de recolección de elementos no utilizados**|-   [Recopilar datos de memoria de .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### Datos de simultaneidad de la generación de perfiles  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Generar perfiles para aplicaciones independientes**|-   [Recopilar datos de simultaneidad](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Generar perfiles de aplicaciones web ASP.NET**|-   [Recopilar datos de simultaneidad](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### Analizar vistas e informes de datos de simultaneidad  
 [Vistas de datos de contención de recursos](../profiling/resource-contention-data-views.md)  
  
 [Visualizador de simultaneidad](../profiling/concurrency-visualizer.md)  
  
## Reference  
 [Referencia de las herramientas de generación de perfiles de la línea de comandos](../profiling/command-line-profiling-tools-reference.md)