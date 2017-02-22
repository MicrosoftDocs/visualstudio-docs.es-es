---
title: "Generaci&#243;n de perfiles de aplicaciones independientes en la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "herramientas de generación de perfiles, aplicaciones independientes"
  - "generar perfiles para aplicaciones independientes"
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Generaci&#243;n de perfiles de aplicaciones independientes en la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En esta sección se describen los procedimientos y las opciones para recopilar datos de rendimiento de las aplicaciones independientes \(cliente\) mediante las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde la línea de comandos.  
  
## Tareas comunes  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Recopilar estadísticas de aplicación:** utilice el método de muestreo para recopilar estadísticas de rendimiento.  El muestreo de datos es útil para analizar problemas de utilización de la CPU y para entender las características de rendimiento generales de una aplicación.|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Recolección de datos detallados de control de tiempo:** utilice el método de instrumentación para recopilar información detallada de control de tiempo.  Los datos de instrumentación son útiles para analizar problemas de E\/S y para el análisis detallado de escenarios de aplicación.|-   [Recopilar datos de control de tiempo detallados utilizando la instrumentación](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Recolección de datos de memoria de .NET:** utilice muestreo o instrumentación para recopilar datos de asignación de memoria de .NET que muestren el tamaño y el número de los objetos asignados.  También puede recopilar datos de duración de los objetos que muestren el tamaño y número de objetos reclamados en cada generación de la recolección de elementos no utilizados.|-   [Recopilar datos de memoria de .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Recolección de datos de simultaneidad:** utilice el método de simultaneidad para recopilar datos de contención de recursos y datos de actividad de subprocesos que muestren la utilización de la CPU, la contención de subprocesos, la migración de subprocesos, los retrasos de sincronización, las áreas de E\/S superpuesta y otros eventos del sistema.|-   [Recopilar datos de simultaneidad](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Agregar datos de interacción de capas:** puede agregar los datos de rendimiento de las llamadas de ADO.NET sincrónicas que la aplicación web realizó a una base de datos de Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].  Agregar datos de interacción de capas a una ejecución de generación de perfiles requiere procedimientos concretos con las Herramientas de generación de perfiles de la línea de comandos.|-   [Recopilar datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Realizar pruebas**: utilice los procedimientos paso a paso para generar perfiles de una aplicación cliente de ejemplo utilizando el método de muestreo o de instrumentación.|-   [Tutorial: Generar perfiles utilizando el método de muestreo en la línea de comandos](../Topic/Walkthrough:%20Command-Line%20Profiling%20Using%20Sampling.md)<br />-   [Tutorial: Generar perfiles utilizando la instrumentación en la línea de comandos](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)|  
  
## Tareas relacionadas  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Generar perfiles de aplicaciones ASP.NET**|-   [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|  
|**Generar perfiles de servicios**|-   [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)|