---
title: Uso de la línea de comandos del generador de perfiles para obtener datos de simultaneidad del servicio
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4b7b60ad871f40e06e2a8fbf6782773ce6596f31
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779680"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Recopilar datos de simultaneidad para un servicio utilizando la línea de comandos del generador de perfiles
El método de simultaneidad de herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite recopilar datos de contención de recursos y de actividad de subprocesos que muestran el uso de CPU, la contención de subprocesos, la migración de subprocesos, los retrasos de sincronización, las áreas de E/S superpuesta y otros eventos del sistema.

> [!NOTE]
> Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Vea [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Tareas comunes

|Tarea|Contenido relacionado|
|----------|---------------------|
|**Adjuntar a un servicio .NET en ejecución**|-   [Cómo: Asociar el generador de perfiles a un servicio .NET para recopilar datos de simultaneidad](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**Agregar datos de interacción de capas**|-   [Recopilación de datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Adjuntar a un servicio C o C++ en ejecución**|-   [Cómo: Asociar el generador de perfiles a un servicio nativo para recopilar datos de simultaneidad](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Tareas relacionadas

### <a name="profile-windows-services"></a>Generación de perfiles de servicios de Windows

|Tarea|Contenido relacionado|
|----------|---------------------|
|**Generar perfiles mediante el método de muestreo**|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|
|**Generar perfiles mediante el método de instrumentación**|-   [Recopilación de datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Generar perfiles de recolección de elementos no utilizados y de asignación de memoria de .NET**|-   [Recopilación de datos de memoria de .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="profile-concurrency-data"></a>Generación de perfiles de problemas de simultaneidad

|Tarea|Contenido relacionado|
|----------|---------------------|
|**Generar perfiles de aplicaciones independientes**|-   [Recopilación de datos de simultaneidad](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**Generar perfiles de aplicaciones web ASP.NET**|-   [Recopilación de datos de simultaneidad](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Análisis de vistas e informes de datos de simultaneidad
- [Vistas de datos de contención de recursos](../profiling/resource-contention-data-views.md)

- [Visualizador de simultaneidad](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Referencia
- [Referencia de las herramientas de generación de perfiles de la línea de comandos](../profiling/command-line-profiling-tools-reference.md)
