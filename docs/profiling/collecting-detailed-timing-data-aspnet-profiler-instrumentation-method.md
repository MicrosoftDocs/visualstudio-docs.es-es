---
title: Recopilación de datos detallados de control de tiempo de una aplicación web ASP.NET mediante el método de instrumentación del generador de perfiles desde la línea de comandos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 79e8ad7842070d13941ad921ccb25ba502209eb0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63405954"
---
# <a name="collect-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Recopilación de datos detallados de tiempo para una aplicación web ASP.NET mediante el método de instrumentación del generador de perfiles en la línea de comandos
En esta sección se describen los procedimientos y las opciones para recopilar datos de rendimiento detallados de una aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] mediante la herramienta de línea de comandos **VSPerfCmd** y el método de instrumentación.

> [!NOTE]
> La herramienta **VSPerfCmd** proporciona acceso completo a la funcionalidad de las herramientas de generación de perfiles, como la opción de poner en pausa y reanudar la generación de perfiles y recopilar datos adicionales del procesador y de los contadores de rendimiento de Windows. También puede utilizar la herramienta de línea de comandos **VSPerfASPNETCmd** cuando no necesite esta funcionalidad. En comparación con la herramienta de línea de comandos [VSPerfCmd](../profiling/vsperfcmd.md), no debe establecerse ninguna variable de entorno y no es necesario reiniciar el equipo. Para más información, vea [Generación rápida de perfiles de sitios web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Tareas comunes

|Tarea|Contenido relacionado|
|----------|---------------------|
|**Generar perfiles de binarios compilados estáticamente**|-   [Cómo: Instrumentar una aplicación web ASP.NET compilada estáticamente y recopilar datos detallados de control de tiempo](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|
|**Generar perfiles de binarios compilados dinámicamente**|-   [Cómo: Instrumentar una aplicación web ASP.NET compilada dinámicamente y recopilar datos detallados de control de tiempo](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|

## <a name="related-tasks"></a>Tareas relacionadas

### <a name="profile-aspnet-web-applications"></a>Generación de perfiles de aplicaciones web ASP.NET

|Tarea|Contenido relacionado|
|----------|---------------------|
|**Generar perfiles mediante el método de muestreo**|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Generar perfiles de recolección de elementos no utilizados y de asignación de memoria**|-   [Recopilación de datos de memoria](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Generar perfiles de actividad de subprocesos y contención de recursos**|-   [Recopilación de datos de simultaneidad](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-by-using-the-instrumentation-method"></a>Generación de perfiles mediante el método de instrumentación

|Tarea|Contenido relacionado|
|----------|---------------------|
|**Generar perfiles de aplicaciones independientes (cliente)**|-   [Recopilación de datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Generar perfiles para servicios**|-   [Recopilación de datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|

### <a name="analyze-instrumentation-data-views-and-reports"></a>Análisis de vistas e informes de datos de instrumentación
- [Vistas de datos del método de instrumentación](../profiling/instrumentation-method-data-views.md)