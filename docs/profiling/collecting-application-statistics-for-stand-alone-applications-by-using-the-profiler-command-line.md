---
title: Recopilar estadísticas de aplicación para aplicaciones independientes utilizando la línea de comandos del generador de perfiles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d1d102629c2a99c5ddf2e79809e58a76c96f1f79
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Recopilar estadísticas de aplicación para aplicaciones independientes utilizando la línea de comandos del generador de perfiles
En esta sección se describen los procedimientos y las opciones para recopilar estadísticas de rendimiento para una aplicación cliente (independiente) mediante el método de muestreo desde la línea de comandos.  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Tareas comunes  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Iniciar una aplicación mediante la generación de perfiles**|-   [Cómo: Iniciar una aplicación independiente y recopilar estadísticas de la aplicación](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Adjuntar el generador de perfiles a una aplicación de .NET Framework en ejecución**|-   [Cómo: Adjuntar el generador de perfiles a una aplicación de .NET Framework y recopilar estadísticas de la aplicación](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Adjuntar el generador de perfiles a una aplicación de C o C++ en ejecución**|-   [Cómo: Adjuntar el generador de perfiles a una aplicación nativa y recopilar estadísticas de la aplicación](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Agregar datos de interacción de capas**|-   [Recopilar datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Tareas relacionadas  
  
### <a name="profiling-stand-alone-applications"></a>Generar perfiles para aplicaciones independientes  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Instrumentar una aplicación**|-   [Recopilar datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Recopilar datos de recopilación de elementos no utilizados y de asignación de memoria de .NET**|-   [Recopilar datos de memoria de .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Recopilar datos de ejecución de subprocesos y contención de recursos**|-   [Recopilar datos de simultaneidad](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-sampling-method"></a>Generar perfiles utilizando el método de muestreo  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Generar perfiles de aplicaciones web ASP.NET**|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Generar perfiles para servicios**|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md). Describe cómo recopilar estadísticas de rendimiento de servicios de Windows mediante el método de muestreo.|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Analizar vistas e informes de datos de muestreo  
 [Vistas de datos del método de muestreo](../profiling/profiler-sampling-method-data-views.md)