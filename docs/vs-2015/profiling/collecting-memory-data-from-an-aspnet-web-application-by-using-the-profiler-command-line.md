---
title: Recopilar datos de memoria de una aplicación web ASP.NET con la línea de comandos del generador de perfiles | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ce60ea0d4433253f118acaa38a36933bd2a6681
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290529"
---
# <a name="collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Recopilar datos de memoria de una aplicación web ASP.NET con la línea de comandos del generador de perfiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En esta sección se describen los procedimientos y las opciones para recopilar datos de asignación de memoria y de duración de objetos para una aplicación web ASP.NET mediante la herramienta de línea de comandos **VSPerfCmd**.  
  
> [!NOTE]
>  La herramienta **VSPerfCmd** proporciona acceso completo a la funcionalidad de las herramientas de generación de perfiles, como la opción de poner en pausa y reanudar la generación de perfiles y recopilar datos adicionales del procesador y de los contadores de rendimiento de Windows. También puede utilizar la herramienta de línea de comandos **VSPerfASPNETCmd** cuando no necesite esta funcionalidad. En comparación con la herramienta de línea de comandos [VSPerfCmd](../profiling/vsperfcmd.md), no es necesario establecer ninguna variable de entorno y tampoco reiniciar el equipo. Para obtener más información, consulte [Generación rápida de perfiles de sitios web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Tareas comunes  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Adjuntar el generador de perfiles a una aplicación ASP.NET en ejecución**|-   [Cómo: Adjuntar el generador de perfiles a una aplicación web ASP.NET para recopilar datos de memoria](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrumentar datos binarios compilados estáticamente**|-   [Cómo: Instrumentar una aplicación ASP.NET compilada estáticamente y recopilar datos de memoria](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**Instrumentar datos binarios compilados dinámicamente**|-   [Cómo: Instrumentar una aplicación ASP.NET compilada dinámicamente y recopilar datos de memoria](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## <a name="related-tasks"></a>Tareas relacionadas  
  
### <a name="profiling-aspnet-web-applications"></a>Generar perfiles de aplicaciones web ASP.NET  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Generar perfiles mediante el método de muestreo**|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Generar perfiles mediante el método de instrumentación**|-   [Recopilar datos de control de tiempo detallados utilizando la instrumentación](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Generar perfiles de actividad de subprocesos y contención de recursos**|-   [Recopilar datos de simultaneidad](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="profiling-net-framework-memory-data"></a>Generar perfiles de datos de memoria de .NET Framework  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Generar perfiles de aplicaciones independientes (cliente)**|-   [Recopilar datos de memoria de .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Generar perfiles para servicios**|-   [Recopilar datos de memoria de .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-net-memory-data-views-and-reports"></a>Analizar vistas e informes de datos de memoria de .NET  
 [Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md)  
  
## <a name="reference"></a>Referencia  
 [Referencia de las herramientas de generación de perfiles de la línea de comandos](../profiling/command-line-profiling-tools-reference.md)



