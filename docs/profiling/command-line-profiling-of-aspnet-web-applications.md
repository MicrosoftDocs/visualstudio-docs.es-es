---
title: "Generar perfiles mediante l&#237;nea de comandos de aplicaciones web ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "generar perfiles de aplicaciones ASP.NET"
  - "herramientas de generación de perfiles, aplicaciones de ASP.NET"
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Generar perfiles mediante l&#237;nea de comandos de aplicaciones web ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En esta sección se describen los procedimientos y opciones para recopilar datos de rendimiento de aplicaciones web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] utilizando las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde la línea de comandos.  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas.  Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección.  Vea [Generar perfiles de aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Tareas comunes  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Recopile datos de generación de perfiles de ASP.NET básicos con facilidad:** utilice la herramienta **VSPerfASPNETCmd** para recopilar datos de muestreo, instrumentación, memoria de .NET, contención o de interacción de capas sin los requisitos de configuración y los reinicios de Internet Information Services \(IIS\) que son necesarios para **VSPerfCmd**.  **VSPerfASPNETCmd** no permite recopilar datos adicionales ni controlar la recolección de datos. **Note:**  **VSPerfASPNETCmd** es la herramienta preferida para utilizar el generador de perfiles independiente para generar perfiles de sitios web ASP.NET.|-   [Generación rápida de perfiles de sitio web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)|  
|**Recopilar estadísticas de aplicación:** utilice el método de muestreo para recopilar estadísticas de rendimiento.  El muestreo de datos es útil para analizar el problemas de uso de la CPU y para entender las características de rendimiento generales de una aplicación.|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Recolección de datos detallados de control de tiempo:** utilice el método de instrumentación para recopilar información detallada de control de tiempo.  Los datos de instrumentación son útiles para analizar problemas de E\/S y para el análisis detallado de escenarios de aplicación.|-   [Recopilar datos de control de tiempo detallados utilizando la instrumentación](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Recolección de datos de memoria de .NET:** utilice muestreo o instrumentación para recopilar datos de asignación de memoria de .NET que muestren el tamaño y el número de los objetos asignados.  También puede recopilar datos de duración de los objetos que muestren el tamaño y número de objetos reclamados en cada generación de la recolección de elementos no utilizados.|-   [Recopilar datos de memoria](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Recopilar datos de simultaneidad:** utilice el método de simultaneidad para recopilar datos de contención de recursos. **Note:**  Las aplicaciones web no admiten la recolección de datos de actividad de subprocesos ni datos de visualización.|-   [Recopilar datos de simultaneidad](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Agregar datos de interacción de capas:** puede agregar los datos de rendimiento de las llamadas de [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] sincrónicas que la aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] realiza a una base de datos de Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].|-   [Recopilar datos de interacción de capas](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## Tareas relacionadas  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Generar perfiles de aplicaciones independientes \(cliente\)**|-   [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Generar perfiles de servicios**|-   [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)|