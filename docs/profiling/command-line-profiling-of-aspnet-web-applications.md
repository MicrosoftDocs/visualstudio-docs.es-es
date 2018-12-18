---
title: Generar perfiles mediante la línea de comandos de aplicaciones web ASP.NET | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 03cb8a6b28ed5f5fece49644d9b1df2608f3e36d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895670"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Generación de perfiles mediante línea de comandos de aplicaciones web ASP.NET
En esta sección se describen los procedimientos y las opciones para recopilar datos de rendimiento de aplicaciones web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] mediante el uso de herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde la línea de comandos.  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Vea [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Tareas comunes
  
| Tarea | Contenido relacionado |
| - | - |
| **Recopilar fácilmente datos de generación de perfiles de ASP.NET básicos:** utilice la herramienta **VSPerfASPNETCmd** para recopilar datos de muestreo, instrumentación, memoria de. NET, contención o interacción de capas sin los requisitos de configuración ni los reinicios de Internet Information Services (IIS) necesarios para **VSPerfCmd**. **VSPerfASPNETCmd** no permite recopilar datos adicionales ni controlar la colección de datos. **Nota:** **VSPerfASPNETCmd** es la herramienta preferida para usar el generador de perfiles independiente a fin de generar perfiles de sitios web de ASP.NET. | -   [Generación rápida de perfiles de sitio web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) |
| **Recopilar estadísticas de aplicación:** utilice el método de muestreo para recopilar estadísticas de rendimiento. Los datos de muestreo son útiles para analizar problemas de uso de CPU y para entender las características de rendimiento generales de una aplicación. | -   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) |
| **Recopilar datos de control de tiempo detallados:** utilice el método de instrumentación para recopilar información de control de tiempo detallada. Los datos de instrumentación son útiles para analizar problemas de E/S y para el análisis detallado de escenarios de aplicación. | -   [Recopilación de datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md) |
| **Recopilar datos de memoria de .NET:** utilice el muestreo o la instrumentación para recopilar datos de asignación de memoria de .NET que muestran el tamaño y el número de los objetos asignados. También puede recopilar datos de duración de objetos que muestran el tamaño y el número de los objetos reclamados en cada generación de recolección de elementos no utilizados. | -   [Recopilación de datos de memoria](../profiling/collecting-memory-data-from-an-aspnet-web-application.md) |
| **Recopilar datos de simultaneidad:** utilice el método de simultaneidad para recopilar datos de contención de recursos. **Nota:** No se admite la recopilación de datos de actividad y visualización de subprocesos para aplicaciones web. | -   [Recopilación de datos de simultaneidad](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md) |
| **Agregar datos de interacción de capas:** puede agregar datos de rendimiento de las llamadas [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] sincrónicas que la aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] realiza a una base de datos de Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]. | -   [Recopilación de datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md) |
  
## <a name="related-tasks"></a>Tareas relacionadas

  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Generar perfiles de aplicaciones independientes (cliente)**|-   [Generación de perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Generar perfiles para servicios**|-   [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)|