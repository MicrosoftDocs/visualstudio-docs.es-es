---
title: Generación de perfiles de aplicaciones independientes en la línea de comandos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3f80f3e65969973202af08299b07ebfa420f3bd2
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557854"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Generación de perfiles de aplicaciones independientes en la línea de comandos
En esta sección se describen los procedimientos y las opciones para recopilar datos de rendimiento de aplicaciones independientes (cliente) mediante las herramientas de generación de perfiles [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde la línea de comandos.

## <a name="common-tasks"></a>Tareas comunes

| Tarea | Contenido relacionado |
| - | - |
| **Recopilar estadísticas de aplicación**: Use el método de muestreo para recopilar estadísticas de rendimiento. Los datos de muestreo son útiles para analizar problemas de uso de CPU y para entender las características de rendimiento generales de una aplicación. | -   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-stand-alone-applications.md) |
| **Recopilar datos detallados de tiempo**: Use el método de instrumentación para recopilar información de tiempo detallada. Los datos de instrumentación son útiles para analizar problemas de E/S y para el análisis detallado de escenarios de aplicación. | -   [Recopilación de datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) |
| **Recopilar datos de memoria de .NET**: Use el muestreo o la instrumentación para recopilar datos de asignación de memoria de .NET que muestran el tamaño y el número de objetos asignados. También puede recopilar datos de duración de objetos que muestran el tamaño y el número de los objetos reclamados en cada generación de recolección de elementos no utilizados. | -   [Recopilación de datos de memoria de .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) |
| **Recopilar datos de simultaneidad**: Use el método de simultaneidad para recopilar datos de contención de recursos y de actividad de subprocesos que muestran el uso de CPU, la contención de subprocesos, la migración de subprocesos, los retrasos de sincronización, las áreas de E/S superpuesta y otros eventos del sistema. | -   [Recopilación de datos de simultaneidad](../profiling/collecting-concurrency-data-for-stand-alone-applications.md) |
| **Agregar datos de interacción de capas:** Puede agregar datos de rendimiento de las llamadas de ADO.NET sincrónicas que la aplicación ha realizado a una base de datos de Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]. Agregar datos de interacción de capas a una ejecución de generación de perfiles requiere procedimientos concretos con las Herramientas de generación de perfiles de la línea de comandos. | -   [Recopilación de datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Tareas relacionadas

|Tarea|Contenido relacionado|
|----------|---------------------|
|**Generar perfiles de aplicaciones ASP.NET**|-   [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
|**Generar perfiles para servicios**|-   [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)|
