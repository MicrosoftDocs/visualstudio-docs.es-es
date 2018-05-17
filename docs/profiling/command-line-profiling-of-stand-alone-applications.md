---
title: Generación de perfiles de aplicaciones independientes en la línea de comandos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3ef57d2fb81ef88d15c3ad0fa3ebfc6f520fc674
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Generación de perfiles de aplicaciones independientes en la línea de comandos
En esta sección se describen los procedimientos y las opciones para recopilar datos de rendimiento de aplicaciones independientes (cliente) mediante las herramientas de generación de perfiles [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde la línea de comandos.  
  
## <a name="common-tasks"></a>Tareas comunes  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Recopilar estadísticas de aplicación:** utilice el método de muestreo para recopilar estadísticas de rendimiento. Los datos de muestreo son útiles para analizar problemas de uso de CPU y para entender las características de rendimiento generales de una aplicación.|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|  
|**Recopilar datos de control de tiempo detallados:** utilice el método de instrumentación para recopilar información de control de tiempo detallada. Los datos de instrumentación son útiles para analizar problemas de E/S y para el análisis detallado de escenarios de aplicación.|-   [Recopilar datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|  
|**Recopilar datos de memoria de .NET:** utilice el muestreo o la instrumentación para recopilar datos de asignación de memoria de .NET que muestran el tamaño y el número de los objetos asignados. También puede recopilar datos de duración de objetos que muestran el tamaño y el número de los objetos reclamados en cada generación de recolección de elementos no utilizados.|-   [Recopilar datos de memoria de .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|  
|**Recopilar datos de simultaneidad:** utilice el método de simultaneidad para recopilar datos de contención de recursos y de actividad de subprocesos que muestran el uso de CPU, la contención de subprocesos, la migración de subprocesos, los retrasos de sincronización, las áreas de E/S superpuesta y otros eventos del sistema.|-   [Recopilar datos de simultaneidad](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|  
|**Agregar datos de interacción de capas:** puede agregar datos de rendimiento de las llamadas de ADO.NET sincrónicas que la aplicación realizó a una base de datos [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] de Microsoft. Agregar datos de interacción de capas a una ejecución de generación de perfiles requiere procedimientos concretos con las Herramientas de generación de perfiles de la línea de comandos.|-   [Recopilar datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Pruébelo:** utilice procedimientos detallados para generar perfiles de una aplicación cliente de ejemplo mediante el método de muestreo o instrumentación.|-   [Tutorial: Generar perfiles mediante muestreo desde la línea de comandos](../profiling/walkthrough-command-line-profiling-using-sampling.md)<br />-   [Tutorial: Generar perfiles mediante la instrumentación desde la línea de comandos](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)|  
  
## <a name="related-tasks"></a>Tareas relacionadas  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Generar perfiles de aplicaciones ASP.NET**|-   [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|  
|**Generar perfiles para servicios**|-   [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)|