---
title: Recopilar estadísticas de aplicación para aplicaciones web ASP.NET utilizando el método de muestreo del generador de perfiles desde la línea de comandos | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6573084e1db304438dd2bda1815605f36eecd691
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574779"
---
# <a name="collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line"></a>Recopilar estadísticas de aplicación para aplicaciones web ASP.NET utilizando el método de muestreo del generador de perfiles desde la línea de comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [recopilar estadísticas de aplicación para aplicaciones Web ASP.NET mediante el método de muestreo Profiler desde la línea de comandos](https://docs.microsoft.com/visualstudio/profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line).  
  
En esta sección se describen los procedimientos y las opciones para recopilar estadísticas de rendimiento de una aplicación web ASP.NET mediante las herramientas de línea de comandos **VSPerfASPNETCmd** y **VSPerfCmd** y el método de generación de perfiles de muestreo.  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Aunque la herramienta **VSPerfCmd** proporciona acceso completo a la funcionalidad de las herramientas de generación de perfiles, incluido pausar y reanudar la generación de perfiles y recopilar datos adicionales del procesador y los contadores de rendimiento de Windows, debe utilizar la herramienta de línea de comandos **VSPerfASPNETCmd** cuando no necesite esta funcionalidad. La herramienta de línea de comandos **VSPerfASPNETCmd** es el método preferido para generar perfiles de sitios web de ASP.NET mediante el generador de perfiles independiente. En comparación con la herramienta de línea de comandos [VSPerfCmd](../profiling/vsperfcmd.md), no es necesario establecer ninguna variable de entorno y tampoco reiniciar el equipo. Para obtener más información, consulte [Generación rápida de perfiles de sitios web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Tareas comunes  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Adjuntar el generador de perfiles a una aplicación de ASP.NET**|-   [Cómo: Adjuntar el generador de perfiles a una aplicación web ASP.NET para recopilar estadísticas de la aplicación](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Tareas relacionadas  
  
### <a name="profiling-aspnet-web-applications"></a>Generar perfiles de aplicaciones web ASP.NET  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Generar perfiles mediante el método de instrumentación**|-   [Recopilar datos de control de tiempo detallados utilizando la instrumentación](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Generar perfiles de recolección de elementos no utilizados y de asignación de memoria**|-   [Recopilar datos de memoria](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Generar perfiles de actividad de subprocesos y contención de recursos**|-   [Recopilar datos de simultaneidad](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="sampling-method"></a>Método de muestreo  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Generar perfiles de aplicaciones independientes (cliente)**|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|-   **Servicios de generación de perfiles**|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Analizar vistas e informes de datos de muestreo  
 [Vistas de datos del método de muestreo](../profiling/profiler-sampling-method-data-views.md)



