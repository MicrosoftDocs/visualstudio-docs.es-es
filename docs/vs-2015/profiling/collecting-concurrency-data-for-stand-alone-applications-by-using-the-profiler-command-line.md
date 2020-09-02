---
title: Recopilar datos de simultaneidad para aplicaciones independientes mediante la línea de comandos del generador de perfiles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7fac1c840d93c03b659e7934a82eb53895b60ede
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68141937"
---
# <a name="collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Recopilar datos de simultaneidad para aplicaciones independientes mediante la línea de comandos del generador de perfiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El método de simultaneidad de herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] permite recopilar datos de contención de recursos y de actividad de subprocesos que muestran el uso de CPU, la contención de subprocesos, la migración de subprocesos, los retrasos de sincronización, las áreas de E/S superpuesta y otros eventos del sistema.  
  
## <a name="common-tasks"></a>Tareas comunes  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Iniciar una aplicación de .NET Framework y generar perfiles de datos de simultaneidad**|-   [Cómo: Iniciar una aplicación de .NET Framework para recopilar datos de simultaneidad](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Iniciar una aplicación de C o C++ y generar perfiles de datos de simultaneidad**|-   [Cómo: Iniciar una aplicación nativa para recopilar datos de simultaneidad](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Adjuntar el generador de perfiles a una aplicación de .NET Framework en ejecución**|-   [Cómo: Adjuntar el generador de perfiles a una aplicación de .NET Framework para recopilar datos de simultaneidad](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Adjuntar el generador de perfiles a una aplicación de C o C++ en ejecución**|-   [Cómo: Adjuntar el generador de perfiles a una aplicación nativa y recopilar datos de simultaneidad](/visualstudio/profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data?view=vs-2015)|  
  
## <a name="related-tasks"></a>Related Tasks  
  
### <a name="profiling-stand-alone-applications"></a>Generar perfiles para aplicaciones independientes  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Generar perfiles mediante el método de muestreo**|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Generar perfiles mediante el método de instrumentación**|-   [Recopilar datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Generar perfiles de recolección de elementos no utilizados y de asignación de memoria de .NET**|-   [Recopilación de datos de memoria de .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Agregar datos de interacción de capas**|-   [Recopilar datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
### <a name="profiling-concurrency-issues"></a>Generar perfiles de problemas de simultaneidad  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Generar perfiles de aplicaciones ASP.NET**|-   [Recopilación de datos de simultaneidad](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Generar perfiles para servicios**|-   [Recopilación de datos de simultaneidad](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>Analizar vistas e informes de datos de simultaneidad  
 [Vistas de datos de contención de recursos](../profiling/resource-contention-data-views.md)  
  
 [Visualizador de simultaneidad](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Referencia  
 [Referencia de Herramientas de generación de perfiles de línea de comandos](../profiling/command-line-profiling-tools-reference.md)
