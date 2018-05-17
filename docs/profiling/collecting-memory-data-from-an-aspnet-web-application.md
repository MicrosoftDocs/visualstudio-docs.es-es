---
title: Recopilar datos de memoria de una aplicación web ASP.NET con la línea de comandos del generador de perfiles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 161f96c38a12de1f29a0f4ebd5d3779f31cf8f23
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Recopilar datos de memoria de una aplicación web ASP.NET con la línea de comandos del generador de perfiles
En esta sección se describen los procedimientos y las opciones para recopilar datos de asignación de memoria y de duración de objetos para una aplicación web ASP.NET mediante la herramienta de línea de comandos **VSPerfCmd**.  
  
> [!NOTE]
>  La herramienta **VSPerfCmd** proporciona acceso completo a la funcionalidad de las herramientas de generación de perfiles, como la opción de poner en pausa y reanudar la generación de perfiles y recopilar datos adicionales del procesador y de los contadores de rendimiento de Windows. También puede utilizar la herramienta de línea de comandos **VSPerfASPNETCmd** cuando no necesite esta funcionalidad. En comparación con la herramienta de línea de comandos [VSPerfCmd](../profiling/vsperfcmd.md), no es necesario establecer ninguna variable de entorno y tampoco reiniciar el equipo. Para obtener más información, consulte [Generación rápida de perfiles de sitios web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Tareas comunes  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Adjuntar el generador de perfiles a una aplicación ASP.NET en ejecución**|-   [Cómo: Adjuntar el generador de perfiles a una aplicación web ASP.NET para recopilar datos de memoria](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrumentar datos binarios compilados estáticamente**|-   [Cómo: Instrumentar una aplicación ASP.NET compilada estáticamente y recopilar datos de memoria](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**Instrumentar datos binarios compilados dinámicamente**|-   [Cómo: Instrumentar una aplicación ASP.NET compilada dinámicamente y recopilar datos de memoria](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)|  
  
## <a name="related-tasks"></a>Tareas relacionadas  
  
### <a name="profiling-aspnet-web-applications"></a>Generar perfiles de aplicaciones web ASP.NET  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Generar perfiles mediante el método de muestreo**|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|  
|**Generar perfiles mediante el método de instrumentación**|-   [Recopilar datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|  
|**Generar perfiles de actividad de subprocesos y contención de recursos**|-   [Recopilar datos de simultaneidad](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|  
  
### <a name="profiling-net-framework-memory-data"></a>Generar perfiles de datos de memoria de .NET Framework  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Generar perfiles de aplicaciones independientes (cliente)**|-   [Recopilar datos de memoria de .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|  
|**Generar perfiles para servicios**|-   [Recopilar datos de memoria de .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-net-memory-data-views-and-reports"></a>Analizar vistas e informes de datos de memoria de .NET  
 [Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md)  
  
## <a name="reference"></a>Referencia  
 [Referencia de las herramientas de generación de perfiles de la línea de comandos](../profiling/command-line-profiling-tools-reference.md)