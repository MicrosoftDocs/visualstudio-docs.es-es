---
title: "Recopilar datos de memoria de una aplicaci&#243;n web ASP.NET con la l&#237;nea de comandos del generador de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "método de generación de perfiles de memoria de .NET"
  - "herramientas de generación de perfiles, método de memoria de .NET"
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Recopilar datos de memoria de una aplicaci&#243;n web ASP.NET con la l&#237;nea de comandos del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En esta sección se describen los procedimientos y las opciones para recopilar datos de asignación de memoria y de duración de los objetos para una aplicación web ASP.NET utilizando la herramienta de línea de comandos **VSPerfCmd**.  
  
> [!NOTE]
>  La herramienta **VSPerfCmd** proporciona acceso completo a la funcionalidad de las herramientas de generación de perfiles, incluso pausar y reanudar la generación de perfiles, y recopilar datos adicionales del procesador y de los contadores de rendimiento de Windows.  También puede utilizar la herramienta de línea de comandos **VSPerfASPNETCmd** cuando no necesite esta funcionalidad.  En comparación con la herramienta de línea de comandos [VSPerfCmd](../profiling/vsperfcmd.md), no es necesario establecer ninguna variable de entorno y no es necesario reiniciar el equipo.  Para obtener más información, vea [Generación rápida de perfiles de sitio web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## Tareas comunes  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Adjuntar el generador de perfiles a una aplicación ASP.NET en ejecución**|-   [Cómo: Adjuntar el generador de perfiles a una aplicación web ASP.NET para recopilar datos de memoria](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrumentar binarios compilados estáticamente**|-   [Cómo: Instrumentar una aplicación ASP.NET compilada estáticamente y recopilar datos de memoria](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**Instrumentar binarios compilados dinámicamente**|-   [Cómo: Instrumentar una aplicación ASP.NET compilada dinámicamente y recopilar datos de memoria](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## Tareas relacionadas  
  
### Generar perfiles de aplicaciones web ASP.NET  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Generar perfiles utilizando el método de muestreo**|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Generar perfiles utilizando el método de instrumentación**|-   [Recopilar datos de control de tiempo detallados utilizando la instrumentación](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Generar perfiles de contención de recursos y de actividad de subprocesos**|-   [Recopilar datos de simultaneidad](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### Generar perfiles de datos de memoria de .NET Framework  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Generar perfiles de aplicaciones independientes \(cliente\)**|-   [Recopilar datos de memoria de .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Generar perfiles de servicios**|-   [Recopilar datos de memoria de .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### Analizar vistas e informes de datos de memoria de .NET  
 [Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md)  
  
## Reference  
 [Referencia de las herramientas de generación de perfiles de la línea de comandos](../profiling/command-line-profiling-tools-reference.md)