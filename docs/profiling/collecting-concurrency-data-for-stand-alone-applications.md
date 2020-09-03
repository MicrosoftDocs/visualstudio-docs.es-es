---
title: Línea de comandos del generador de perfiles para obtener datos de simultaneidad de una aplicación independiente
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 15e8be092a8e1e065f2aa1a80be7447a370974b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331866"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Recopilar datos de simultaneidad para aplicaciones independientes mediante la línea de comandos del generador de perfiles
El método de simultaneidad de herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite recopilar datos de contención de recursos y de actividad de subprocesos que muestran el uso de CPU, la contención de subprocesos, la migración de subprocesos, los retrasos de sincronización, las áreas de E/S superpuesta y otros eventos del sistema.

## <a name="common-tasks"></a>Tareas comunes

|Tarea|Contenido relacionado|
|----------|---------------------|
|**Iniciar una aplicación de .NET Framework y generar perfiles de datos de simultaneidad**|-   [Cómo: Iniciar una aplicación de .NET Framework para recopilar datos de simultaneidad](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|
|**Iniciar una aplicación de C o C++ y generar perfiles de datos de simultaneidad**|-   [Cómo: Iniciar una aplicación nativa para recopilar datos de simultaneidad](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Adjuntar el generador de perfiles a una aplicación de .NET Framework en ejecución**|-   [Cómo: Adjuntar el generador de perfiles a una aplicación de .NET Framework para recopilar datos de simultaneidad](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|
|**Adjuntar el generador de perfiles a una aplicación de C o C++ en ejecución**|-   [Cómo: Adjuntar el generador de perfiles a una aplicación nativa y recopilar datos de simultaneidad](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)|

## <a name="related-tasks"></a>Tareas relacionadas

### <a name="profile-stand-alone-applications"></a>Generación de perfiles de aplicaciones independientes

|Tarea|Contenido relacionado|
|----------|---------------------|
|**Generar perfiles mediante el método de muestreo**|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Generar perfiles mediante el método de instrumentación**|-   [Recopilación de datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Generar perfiles de recolección de elementos no utilizados y de asignación de memoria de .NET**|-   [Recopilación de datos de memoria de .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Agregar datos de interacción de capas**|-   [Recopilación de datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

### <a name="profile-concurrency-issues"></a>Generación de perfiles de problemas de simultaneidad

|Tarea|Contenido relacionado|
|----------|---------------------|
|**Generar perfiles de aplicaciones de ASP.NET**|-   [Recopilación de datos de simultaneidad](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|
|**Generar perfiles para servicios**|-   [Recopilación de datos de simultaneidad](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Análisis de vistas e informes de datos de simultaneidad
- [Vistas de datos de contención de recursos](../profiling/resource-contention-data-views.md)

- [Visualizador de simultaneidad](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Referencia
- [Referencia de las herramientas de generación de perfiles de la línea de comandos](../profiling/command-line-profiling-tools-reference.md)
