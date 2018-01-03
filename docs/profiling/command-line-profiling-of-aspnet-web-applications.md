---
title: "Generar perfiles mediante la línea de comandos de aplicaciones web ASP.NET | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: aspnet
ms.openlocfilehash: 9c96d83a278f7a82c56a58e4db7ec96cbe426bea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Generar perfiles mediante línea de comandos de aplicaciones web ASP.NET
En esta sección se describen los procedimientos y las opciones para recopilar datos de rendimiento de aplicaciones web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] mediante el uso de herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde la línea de comandos.  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Tareas comunes  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Recopilar fácilmente datos de generación de perfiles de ASP.NET básicos:** utilice la herramienta **VSPerfASPNETCmd** para recopilar datos de muestreo, instrumentación, memoria de. NET, contención o interacción de capas sin los requisitos de configuración ni los reinicios de Internet Information Services (IIS) necesarios para **VSPerfCmd**. **VSPerfASPNETCmd** no permite recopilar datos adicionales ni controlar la colección de datos. **Nota:** **VSPerfASPNETCmd** es la herramienta preferida para usar el generador de perfiles independiente a fin de generar perfiles de sitios web de ASP.NET.|-   [Generación rápida de perfiles de sitios web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)|  
|**Recopilar estadísticas de aplicación:** utilice el método de muestreo para recopilar estadísticas de rendimiento. Los datos de muestreo son útiles para analizar problemas de uso de CPU y para entender las características de rendimiento generales de una aplicación.|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Recopilar datos de control de tiempo detallados:** utilice el método de instrumentación para recopilar información de control de tiempo detallada. Los datos de instrumentación son útiles para analizar problemas de E/S y para el análisis detallado de escenarios de aplicación.|-   [Recopilar datos de control de tiempo detallados utilizando la instrumentación](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Recopilar datos de memoria de .NET:** utilice el muestreo o la instrumentación para recopilar datos de asignación de memoria de .NET que muestran el tamaño y el número de los objetos asignados. También puede recopilar datos de duración de objetos que muestran el tamaño y el número de los objetos reclamados en cada generación de recolección de elementos no utilizados.|-   [Recopilar datos de memoria](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Recopilar datos de simultaneidad:** utilice el método de simultaneidad para recopilar datos de contención de recursos. **Nota:** No se admite la recopilación de datos de actividad y visualización de subprocesos para aplicaciones web.|-   [Recopilar datos de simultaneidad](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Agregar datos de interacción de capas:** puede agregar datos de rendimiento de las llamadas [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] sincrónicas que la aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] realiza a una base de datos de Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].|-   [Recopilar datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Tareas relacionadas  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Generar perfiles de aplicaciones independientes (cliente)**|-   [Generar perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Generar perfiles para servicios**|-   [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)|