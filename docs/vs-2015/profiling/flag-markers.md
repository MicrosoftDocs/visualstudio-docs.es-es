---
title: Marcadores de marca | Microsoft Docs
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
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4d1e5c119c5402501efaafcdccd9c3d0885ce75
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803206"
---
# <a name="flag-markers"></a>Marcadores de marca
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un marcador de marca representa algo que se ha producido en un momento determinado en una aplicación. Una marca puede representar muchos tipos de eventos de aplicación. Por ejemplo, una marca puede mostrar cuándo se ha programado un elemento de trabajo determinado o cuándo se ha producido una excepción. Los runtimes, como la biblioteca TPL, también pueden generar marcas.  
  
## <a name="flag-importance"></a>Importancia de la marca  
 Las marcas se muestran en diferentes tamaños según su importancia. Al igual que cualquier marcador, la importancia puede ser baja, normal, alta o crítica.  En esta ilustración se muestra el aspecto de los marcadores por nivel de importancia:  
  
 ![Marcadores de importancia baja, normal, alta y crítica](../profiling/media/cvmarkerimportance.png "CVMarkerImportance")  
Marcadores que muestran la importancia de la marca  
  
## <a name="flag-category"></a>Categoría de la marca  
 Una marca se muestra en uno de cinco colores diferentes, según su categoría. Los colores se reutilizan si hay más de cinco categorías. No puede elegir el color. Al igual que cualquier marcador, la categoría puede ser cualquier número entero. En la ilustración siguiente se muestran los colores de las cinco primeras categorías.  
  
 ![Los cinco colores de los marcadores de categoría](../profiling/media/cvmarkercategory.png "CVMarkerCategory")  
Marcadores que muestran categorías  
  
## <a name="alerts"></a>Alertas  
 Una alerta es una marca de color rojo que representa un evento de aplicación crítico, como una excepción.  Esta es una alerta:  
  
 ![Marcador de alerta del visualizador de simultaneidad](../profiling/media/cvmarkeralert.png "CVMarkerAlert")  
Un marcador de alerta  
  
## <a name="aggregation-flags"></a>Marcas de agregación  
 En ocasiones, las marcas están tan cerca de otras en el visualizador de simultaneidad que no se pueden dibujar individualmente. Cuando esto ocurre, se muestra una *marca de agregación* gris que representa las marcas subyacentes. Cuando coloca el puntero en uno de estos iconos, una información sobre herramientas muestra el número de marcas subyacentes que se representan. Para ver las marcas, amplíe. Si amplía completamente y sigue recibiendo una marca de agregación, puede ver las marcas subyacentes en el [Informe de marcadores](../profiling/markers-report.md).  
  
 Las marcas de agregación se dibujan en diferentes tamaños. El tamaño depende del nivel de importancia de la marca más importante en la agregación. En la ilustración siguiente se muestran las marcas de agregación en orden creciente de importancia.  
  
 ![Agregar marcas que muestren cuatro niveles de importancia](../profiling/media/cvmarkeraggregate.png "CVMarkerAggregate")  
Marcas de agregación por nivel de importancia  
  
## <a name="see-also"></a>Vea también  
 [Marcadores del visualizador de simultaneidad](../profiling/concurrency-visualizer-markers.md)   
 [SDK del visualizador de simultaneidad](../profiling/concurrency-visualizer-sdk.md)



