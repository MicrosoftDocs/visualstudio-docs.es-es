---
title: Recopilación de datos detallados de control de tiempo de una aplicación web ASP.NET mediante el método de instrumentación del generador de perfiles desde la línea de comandos | Microsoft Docs
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
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eabd6d66079fc003bb87e867c0b5bb572c3bddc1
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "47592565"
---
# <a name="collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Recopilar datos detallados de tiempo para una aplicación web ASP.NET utilizando el método de instrumentación del generador de perfiles en la línea de comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [recopilación detallada datos de tiempo para una aplicación Web de ASP.NET mediante el método de instrumentación de Profiler desde la línea de comandos](https://docs.microsoft.com/visualstudio/profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line).  
  
En esta sección se describen los procedimientos y las opciones para recopilar datos de rendimiento detallados de una aplicación web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] mediante la herramienta de línea de comandos **VSPerfCmd** y el método de instrumentación.  
  
> [!NOTE]
>  La herramienta **VSPerfCmd** proporciona acceso completo a la funcionalidad de las herramientas de generación de perfiles, como la opción de poner en pausa y reanudar la generación de perfiles y recopilar datos adicionales del procesador y de los contadores de rendimiento de Windows. También puede utilizar la herramienta de línea de comandos **VSPerfASPNETCmd** cuando no necesite esta funcionalidad. En comparación con la herramienta de línea de comandos [VSPerfCmd](../profiling/vsperfcmd.md), no debe establecerse ninguna variable de entorno y no es necesario reiniciar el equipo. Para obtener más información, consulte [Generación rápida de perfiles de sitios web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Tareas comunes  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Generar perfiles de binarios compilados estáticamente**|-   [Cómo: Instrumentar una aplicación ASP.NET compilada estáticamente y recopilar datos de control de tiempo detallados](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
|**Generar perfiles de binarios compilados dinámicamente**|-   [Cómo: Instrumentar una aplicación ASP.NET compilada dinámicamente y recopilar datos de control de tiempo detallados](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Tareas relacionadas  
  
### <a name="profiling-aspnet-web-applications"></a>Generar perfiles de aplicaciones web ASP.NET  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Generar perfiles mediante el método de muestreo**|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Generar perfiles de recolección de elementos no utilizados y de asignación de memoria**|-   [Recopilar datos de memoria](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Generar perfiles de actividad de subprocesos y contención de recursos**|-   [Recopilar datos de simultaneidad](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-instrumentation-method"></a>Generar perfiles utilizando el método de instrumentación  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Generar perfiles de aplicaciones independientes (cliente)**|-   [Recopilar datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Generar perfiles para servicios**|-   [Recopilar datos de control de tiempo detallados utilizando la instrumentación](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
  
### <a name="analyzing-instrumentation-data-views-and-reports"></a>Analizar vistas e informes de datos de instrumentación  
 [Vistas de datos del método de instrumentación](../profiling/instrumentation-method-data-views.md)



