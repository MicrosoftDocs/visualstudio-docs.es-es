---
title: Visualizador de simultaneidad | Microsoft Docs
description: Use el visualizador de simultaneidad para ver los gráficos que muestran el tiempo del subproceso en su aplicación multiproceso con el fin de ayudarle a resolver los problemas de rendimiento.
ms.custom: SEO-VS-2020
ms.date: 07/11/2017
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e6f36568568a59980316f3070f902027898e39e
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720961"
---
# <a name="concurrency-visualizer"></a>Visualizador de simultaneidad

> [!NOTE]
> El Visualizador de simultaneidad es una extensión opcional de Visual Studio. Descargue el Visualizador de simultaneidad y las Herramientas de recolección del visualizador de simultaneidad desde los siguientes vínculos:
>
> - Descargue la extensión [Visualizador de simultaneidad para Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=Diagnostics.DiagnosticsConcurrencyVisualizer2019#overview).
> - Descargue la extensión [Visualizador de simultaneidad para Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ConcurrencyVisualizer2017#overview).
> - Descargue la extensión [Visualizador de simultaneidad para Visual Studio 2015](https://marketplace.visualstudio.com/items?itemName=Diagnostics.ConcurrencyVisualizerforVisualStudio2015).
> - Descargue las [Herramientas de recolección del Visualizador de simultaneidad para Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103).
>
> La [utilidad de la línea de comandos del visualizador de simultaneidad (CVCollectionCmd.exe)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) le permite recopilar seguimientos de la línea de comandos que puede ver en el visualizador de simultaneidad para Visual Studio 2015. La herramienta se puede usar en equipos que no tengan instalado Visual Studio.

Puede usar el Visualizador de simultaneidad para ver cómo funciona la aplicación multiproceso. Las vistas del Visualizador de simultaneidad proporcionan datos gráficos, tabulares y textuales que muestran las relaciones temporales entre los subprocesos del programa y el sistema desde un punto de vista global. Se puede utilizar el Visualizador de simultaneidad para buscar cuellos de botella de rendimiento, infrautilización de la CPU, contención de subprocesos, migración de subprocesos entre núcleos, retrasos de sincronización, actividad de DirectX, áreas de E/S superpuestas y otra información. Las vistas proporcionan datos procesables sobre los que se puede actuar vinculando su salida gráfica a pilas de llamadas y al código fuente.

> [!NOTE]
> El Visualizador de simultaneidad no admite proyectos web.

El Visualizador de simultaneidad se basa en la funcionalidad [Seguimiento de eventos para Windows](/windows/win32/etw/event-tracing-portal) .

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Vista de utilización](../profiling/utilization-view.md)|Describe cómo ver y analizar la actividad del sistema en todos los procesadores.|
|[Vista de subprocesos](../profiling/threads-view-parallel-performance.md)|Describe cómo analizar las interacciones entre los subprocesos del programa.|
|[Vista de núcleos](../profiling/cores-view.md)|Describe cómo analizar la migración de subprocesos por los núcleos.|
|[Modelos comunes para aplicaciones multiproceso con comportamiento deficiente](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Describe varios patrones comunes y muestra cómo aparecen en el Visualizador de simultaneidad.|
|[Blog Parallel Development in Visual Studio](/archive/blogs/visualizeparallel/)|Proporciona sugerencias y prácticas recomendadas para el Visualizador de simultaneidad.|
|[Vistas de informes de rendimiento](../profiling/performance-report-views.md)|Proporciona información de referencia para los informes y vistas de las Herramientas de generación de perfiles de Visual Studio.|
|[SDK del visualizador de simultaneidad](../profiling/concurrency-visualizer-sdk.md)|Describe cómo instrumentar el código fuente para mostrar información adicional en el Visualizador de simultaneidad.|
|[Utilidad de la línea de comandos del visualizador de simultaneidad (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Describe cómo utilizar el servicio de línea de comandos del Visualizador de simultaneidad (CVCollectionCmd.exe) para recopilar y procesar los seguimientos en los equipos que no tengan Visual Studio.|

## <a name="see-also"></a>Vea también

- [Generación de perfiles en Visual Studio](../profiling/index.yml)
- [Primer vistazo a la generación de perfiles](../profiling/profiling-feature-tour.md)