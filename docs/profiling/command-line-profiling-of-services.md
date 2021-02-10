---
title: Generación de perfiles de servicios desde la línea de comandos | Microsoft Docs
description: Obtenga información sobre cómo usar las Herramientas de generación de perfiles desde la línea de comandos para recopilar datos de rendimiento sobre servicios de Windows.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dd77161184c5cb8be89ed522bbf06b6d80ca4bee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969508"
---
# <a name="command-line-profiling-of-services"></a>Generación de perfiles de servicio desde la línea de comandos
En esta sección se describen los procedimientos y las opciones para recopilar datos de rendimiento de servicios de Windows mediante las herramientas de generación de perfiles [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde la línea de comandos.

> [!NOTE]
> Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Vea [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Tareas comunes

| Tarea | Contenido relacionado |
| - | - |
| **Recopilar estadísticas de aplicación:** utilice el método de muestreo para recopilar estadísticas de rendimiento. Los datos de muestreo son útiles para analizar problemas de uso de CPU y para entender las características de rendimiento generales de una aplicación. | -   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) |
| **Recopilar datos de control de tiempo detallados:** utilice el método de instrumentación para recopilar información de control de tiempo detallada. Los datos de instrumentación son útiles para analizar problemas de E/S y para el análisis detallado de escenarios de aplicación. | -   [Recopilación de datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) |
| **Recopilar datos de memoria de .NET:** utilice el muestreo o la instrumentación para recopilar datos de asignación de memoria de .NET que muestran el tamaño y el número de los objetos asignados. También puede recopilar datos de duración de objetos que muestran el tamaño y el número de los objetos reclamados en cada generación de recolección de elementos no utilizados. | -   [Recopilación de datos de memoria de .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) |
| **Recopilar datos de simultaneidad**: Use el método de simultaneidad para recopilar datos de contención de recursos y de actividad de subprocesos que muestran el uso de CPU, la contención de subprocesos, la migración de subprocesos, los retrasos de sincronización, las áreas de E/S superpuesta y otros eventos del sistema. | -   [Recopilación de datos de simultaneidad](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md) |
| **Agregar datos de interacción de capas:** puede agregar datos de rendimiento de las llamadas de ADO.NET sincrónicas que el servicio realizó a una base de datos [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] de Microsoft. | -   [Recopilación de datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Tareas relacionadas

|Tarea|Contenido relacionado|
|----------|---------------------|
|**Generar perfiles de aplicaciones independientes (cliente)**|-   [Generación de perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Generar perfiles de aplicaciones de ASP.NET**|-   [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
