---
title: Visualizador de simultaneidad | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91fd9e0872529c61ffbfee42d1f3517c106340e0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733820"
---
# <a name="concurrency-visualizer"></a>Visualizador de simultaneidad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
>  El Visualizador de simultaneidad es una extensión opcional de Visual Studio. Descargue el Visualizador de simultaneidad y las Herramientas de recolección del visualizador de simultaneidad desde los siguientes vínculos:  
> 
> - Descargue la extensión              [Visualizador de simultaneidad](https://visualstudiogallery.msdn.microsoft.com/a6c24ce9-beec-4545-9261-293061436ee9) .  
>   -   Descargue las              [Herramientas de recolección del Visualizador de simultaneidad para Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=49103).  
> 
>   La [utilidad de la línea de comandos del visualizador de simultaneidad (CVCollectionCmd.exe)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) le permite recopilar seguimientos de la línea de comandos que puede ver en el visualizador de simultaneidad para Visual Studio 2015. La herramienta se puede usar en equipos que no tengan instalado Visual Studio.  
  
 Puede usar el Visualizador de simultaneidad para ver cómo funciona la aplicación multiproceso. Las vistas del Visualizador de simultaneidad proporcionan datos gráficos, tabulares y textuales que muestran las relaciones temporales entre los subprocesos del programa y el sistema desde un punto de vista global. Se puede utilizar el Visualizador de simultaneidad para buscar cuellos de botella de rendimiento, infrautilización de la CPU, contención de subprocesos, migración de subprocesos entre núcleos, retrasos de sincronización, actividad de DirectX, áreas de E/S superpuestas y otra información. Las vistas proporcionan datos procesables sobre los que se puede actuar vinculando su salida gráfica a pilas de llamadas y al código fuente.  
  
 El Visualizador de simultaneidad se basa en la funcionalidad [Seguimiento de eventos para Windows](http://go.microsoft.com/fwlink/?LinkId=234579) .  
  
> [!NOTE]
>  El Visualizador de simultaneidad no admite proyectos web.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Vista Utilización](../profiling/utilization-view.md)|Describe cómo ver y analizar la actividad del sistema en todos los procesadores.|  
|[Vista de subprocesos](../profiling/threads-view-parallel-performance.md)|Describe cómo analizar las interacciones entre los subprocesos del programa.|  
|[Vista Núcleos](../profiling/cores-view.md)|Describe cómo analizar la migración de subprocesos por los núcleos.|  
|[Modelos comunes para aplicaciones multiproceso con comportamiento deficiente](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Describe varios patrones comunes y muestra cómo aparecen en el Visualizador de simultaneidad.|  
|[Blog Parallel Development in Visual Studio](http://go.microsoft.com/fwlink/?LinkId=235385)|Proporciona sugerencias y prácticas recomendadas para el Visualizador de simultaneidad.|  
|[Vistas de informes de rendimiento](../profiling/performance-report-views.md)|Proporciona información de referencia para los informes y vistas de las Herramientas de generación de perfiles de Visual Studio.|  
|[SDK del visualizador de simultaneidad](../profiling/concurrency-visualizer-sdk.md)|Describe cómo instrumentar el código fuente para mostrar información adicional en el Visualizador de simultaneidad.|  
|[Utilidad de la línea de comandos del visualizador de simultaneidad (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Describe cómo utilizar el servicio de línea de comandos del Visualizador de simultaneidad (CVCollectionCmd.exe) para recopilar y procesar los seguimientos en los equipos que no tengan Visual Studio.|  
  
## <a name="see-also"></a>Vea también  
 [Herramientas de generación de perfiles](../profiling/profiling-tools.md)



