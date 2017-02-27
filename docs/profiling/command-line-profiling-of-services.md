---
title: "Generaci&#243;n de perfiles de servicio desde la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "herramientas de generación de perfiles, servicios"
  - "generar perfiles de servicios"
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Generaci&#243;n de perfiles de servicio desde la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En esta sección se describen los procedimientos y opciones para recopilar datos de rendimiento para servicios de Windows utilizando las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde la línea de comandos.  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas.  Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección.  Vea [Generar perfiles de aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Tareas comunes  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Recopilar estadísticas de aplicación:** utilice el método de muestreo para recopilar estadísticas de rendimiento.  El muestreo de datos es útil para analizar problemas de utilización de la CPU y para entender las características de rendimiento generales de una aplicación.|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Recolección de datos detallados de control de tiempo:** utilice el método de instrumentación para recopilar información detallada de control de tiempo.  Los datos de instrumentación son útiles para analizar problemas de E\/S y para el análisis detallado de escenarios de aplicación.|-   [Recopilar datos de control de tiempo detallados utilizando la instrumentación](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Recolección de datos de memoria de .NET:** utilice muestreo o instrumentación para recopilar datos de asignación de memoria de .NET que muestren el tamaño y el número de los objetos asignados.  También puede recopilar datos de duración de los objetos que muestren el tamaño y número de objetos reclamados en cada generación de la recolección de elementos no utilizados.|-   [Recopilar datos de memoria de .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**Recolección de datos de simultaneidad:** utilice el método de simultaneidad para recopilar datos de contención de recursos y datos de actividad de subprocesos que muestren la utilización de la CPU, la contención de subprocesos, la migración de subprocesos, los retrasos de sincronización, las áreas de E\/S superpuesta y otros eventos del sistema.|-   [Recopilar datos de simultaneidad](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
|**Agregar datos de interacción de capas:** puede agregar los datos de rendimiento de las llamadas de ADO.NET sincrónicas que el servicio realizó a una base de datos de Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].|-   [Recopilar datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## Tareas relacionadas  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Generar perfiles de aplicaciones independientes \(cliente\)**|-   [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Generar perfiles de aplicaciones ASP.NET**|-   [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|