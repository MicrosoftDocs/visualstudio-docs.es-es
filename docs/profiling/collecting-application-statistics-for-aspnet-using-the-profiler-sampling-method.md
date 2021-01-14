---
title: Recopilar estadísticas para aplicaciones web ASP.NET
description: Revise los procedimientos y las opciones para recopilar estadísticas de rendimiento de aplicaciones web de ASP.NET mediante las herramientas VSPerfASPNETCmd y VSPerfCmd, y el método de generación de perfiles de muestreo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: ef1f4ef1c50db1234425ab164f377dab5ff12ea6
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149539"
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>Recopilar estadísticas para aplicaciones web ASP.NET

En esta sección se describen los procedimientos y las opciones para recopilar estadísticas de rendimiento de una aplicación web ASP.NET mediante las herramientas de línea de comandos **VSPerfASPNETCmd** y **VSPerfCmd** y el método de generación de perfiles de muestreo.

> [!NOTE]
> Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

> [!NOTE]
> Aunque la herramienta **VSPerfCmd** proporciona acceso completo a la funcionalidad de las herramientas de generación de perfiles, incluido pausar y reanudar la generación de perfiles y recopilar datos adicionales del procesador y los contadores de rendimiento de Windows, debe utilizar la herramienta de línea de comandos **VSPerfASPNETCmd** cuando no necesite esta funcionalidad. La herramienta de línea de comandos **VSPerfASPNETCmd** es el método preferido para generar perfiles de sitios web de ASP.NET mediante el generador de perfiles independiente. En comparación con la herramienta de línea de comandos [VSPerfCmd](../profiling/vsperfcmd.md), no es necesario establecer ninguna variable de entorno y tampoco reiniciar el equipo. Para más información, vea [Generación rápida de perfiles de sitios web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Tareas comunes

|Tarea|Contenido relacionado|
|----------|---------------------|
|**Adjuntar el generador de perfiles a una aplicación de ASP.NET**|-   [Cómo: Asociar el generador de perfiles a una aplicación web ASP.NET para recopilar estadísticas de aplicación](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Tareas relacionadas

### <a name="profile-aspnet-web-applications"></a>Generación de perfiles de aplicaciones web ASP.NET

|Tarea|Contenido relacionado|
|----------|---------------------|
|**Generar perfiles mediante el método de instrumentación**|-   [Recopilación de datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Generar perfiles de recolección de elementos no utilizados y de asignación de memoria**|-   [Recopilación de datos de memoria](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Generar perfiles de actividad de subprocesos y contención de recursos**|-   [Recopilación de datos de simultaneidad](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="sample-method"></a>Método de muestreo

|Tarea|Contenido relacionado|
|----------|---------------------|
|**Generar perfiles de aplicaciones independientes (cliente)**|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|-   **Servicios de generación de perfiles**|-   [Recopilar estadísticas de aplicación mediante muestreo](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Análisis de vistas e informes de datos de muestreo
- [Vistas de datos del método de muestreo](../profiling/profiler-sampling-method-data-views.md)
