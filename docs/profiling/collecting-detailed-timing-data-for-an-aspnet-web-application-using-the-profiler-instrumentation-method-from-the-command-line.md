---
title: "Recopilar datos detallados de tiempo para una aplicaci&#243;n web ASP.NET utilizando el m&#233;todo de instrumentaci&#243;n del generador de perfiles en la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "método de generación de perfiles de instrumentación"
  - "herramientas de generación de perfiles, método de instrumentación"
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Recopilar datos detallados de tiempo para una aplicaci&#243;n web ASP.NET utilizando el m&#233;todo de instrumentaci&#243;n del generador de perfiles en la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En esta sección se describen los procedimientos y las opciones para recopilar datos de rendimiento detallados para una aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] con la herramienta de línea de comandos y el método de instrumentación de **VSPerfCmd**.  
  
> [!NOTE]
>  La herramienta **VSPerfCmd** proporciona acceso completo a la funcionalidad de las herramientas de generación de perfiles, incluso pausar y reanudar la generación de perfiles, y recopilar datos adicionales del procesador y de los contadores de rendimiento de Windows.  También puede utilizar la herramienta de línea de comandos **VSPerfASPNETCmd** cuando no necesite esta funcionalidad.  En comparación con la herramienta de línea de comandos [VSPerfCmd](../profiling/vsperfcmd.md), no es necesario establecer ninguna variable de entorno y no es necesario reiniciar el equipo.  Para obtener más información, vea [Generación rápida de perfiles de sitio web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## Tareas comunes  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Generar perfiles de binarios compilados estáticamente**|-   [Cómo: Instrumentar una aplicación ASP.NET compilada estáticamente y recopilar datos de control de tiempo detallados](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
|**Generar perfiles de binarios compilados dinámicamente**|-   [Cómo: Instrumentar una aplicación ASP.NET compilada dinámicamente y recopilar datos de control de tiempo detallados](../Topic/How%20to:%20Instrument%20a%20Dynamically%20Compiled%20ASP.NET%20Web%20Application%20and%20Collect%20Detailed%20Timing%20Data%20with%20the%20Profiler%20by%20Using%20the%20Command%20Line.md)|  
  
## Tareas relacionadas  
  
### Generar perfiles de aplicaciones web ASP.NET  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Generar perfiles utilizando el método de muestreo**|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Generar perfiles de asignación de memoria y de recolección de elementos no utilizados**|-   [Recopilar datos de memoria](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Generar perfiles de contención de recursos y de actividad de subprocesos**|-   [Recopilar datos de simultaneidad](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### Generar perfiles utilizando el método de instrumentación  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Generar perfiles de aplicaciones independientes \(cliente\)**|-   [Recopilar datos de control de tiempo detallados utilizando la instrumentación](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Generar perfiles de servicios**|-   [Recopilar datos de control de tiempo detallados utilizando la instrumentación](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
  
### Analizar vistas e informes de datos de instrumentación  
 [Vistas de datos del método de instrumentación](../profiling/instrumentation-method-data-views.md)