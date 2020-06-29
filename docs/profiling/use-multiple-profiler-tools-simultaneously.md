---
title: Uso de varias herramientas de generación de perfiles de forma simultánea | Microsoft Docs
ms.date: 4/29/2020
ms.topic: conceptual
helpviewer_keywords:
- Profiler, multiple tools
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 7844d81af02211d1c9f4e444c6367152e73392e9
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85291050"
---
# <a name="using-multiple-profiler-tools-simultaneously"></a>Uso de varias herramientas de generación de perfiles de forma simultánea

El Generador de perfiles de rendimiento se diseñó con la idea de que se pueden usar varias herramientas en la misma sesión para ayudar a entender los problemas de rendimiento. La mayoría de las herramientas del Generador de perfiles de rendimiento se admiten en ejecución de forma simultánea, como las herramientas [Uso de CPU](../profiling/cpu-usage.md), [.NET Async](../profiling/analyze-async.md) y [Base de datos](../profiling/analyze-database.md). Para ejecutar herramientas simultáneamente en la misma sesión de diagnóstico, active la casilla que se encuentra junto a ellas y, a continuación, inicie la sesión de diagnóstico.

![Todas las herramientas del Concentrador de diagnóstico seleccionadas](../profiling/media/diaghuballtoolsselected.png "Todas las herramientas del Concentrador de diagnóstico seleccionadas")

>[!NOTE]
>Ciertas herramientas, como la herramienta [Asignación de objetos .NET](../profiling/dotnet-alloc-tool.md), no se pueden ejecutar con otras herramientas debido a su gran sobrecarga o por otras limitaciones técnicas.

## <a name="time-filtering"></a>Filtrado de tiempo 

Durante el análisis, las operaciones de filtrado de tiempo se aplican entre las herramientas, por lo que puede usar la información de una herramienta para reducir un intervalo de tiempo y filtrar los datos en otra herramienta. Esta característica ayuda a guiar el análisis a puntos específicos de un seguimiento y ayuda a entender el estado de la aplicación.

![Filtrado de tiempo del Concentrador de diagnóstico](../profiling/media/diaghubtimefiltering.png "Filtrado de tiempo del Concentrador de diagnóstico")

## <a name="see-also"></a>Vea también

- [Optimización de la configuración del generador de perfiles](../profiling/optimize-profiler-settings.md)
- [Ejecutar herramientas de generación de perfiles con o sin el depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Descripción de los métodos de colección de rendimiento](../profiling/understanding-performance-collection-methods-perf-profiler.md)
