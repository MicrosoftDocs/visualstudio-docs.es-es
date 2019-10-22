---
title: Marcadores de marca | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ccc0c7aa3386e906ad13331a596953db70240701
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969984"
---
# <a name="flag-markers"></a>Marcadores de marca
Un marcador de marca representa algo que se ha producido en un momento determinado en una aplicación. Una marca puede representar muchos tipos de eventos de aplicación. Por ejemplo, una marca puede mostrar cuándo se ha programado un elemento de trabajo determinado o cuándo se ha producido una excepción. Los runtimes, como la biblioteca TPL, también pueden generar marcas.

## <a name="flag-importance"></a>Importancia de la marca
 Las marcas se muestran en diferentes tamaños según su importancia. Al igual que cualquier marcador, la importancia puede ser baja, normal, alta o crítica.  En esta ilustración se muestra el aspecto de los marcadores por nivel de importancia:

 ![Marcadores de importancia baja, normal, alta y crítica](../profiling/media/cvmarkerimportance.png "CVMarkerImportance") Marcadores que muestran la importancia de la marca

## <a name="flag-category"></a>Categoría de la marca
 Una marca se muestra en uno de cinco colores diferentes, según su categoría. Los colores se reutilizan si hay más de cinco categorías. No puede elegir el color. Al igual que cualquier marcador, la categoría puede ser cualquier número entero. En la ilustración siguiente se muestran los colores de las cinco primeras categorías.

 ![Los cinco colores de los marcadores de categoría](../profiling/media/cvmarkercategory.png "CVMarkerCategory") Marcadores que muestran categorías

## <a name="alerts"></a>Alertas
 Una alerta es una marca de color rojo que representa un evento de aplicación crítico, como una excepción.  Esta es una alerta:

 ![Marcador de alerta del visualizador de simultaneidad](../profiling/media/cvmarkeralert.png "CVMarkerAlert") Un marcador de alerta

## <a name="aggregation-flags"></a>Marcas de agregación
 En ocasiones, las marcas están tan cerca de otras en el visualizador de simultaneidad que no se pueden dibujar individualmente. Cuando esto ocurre, se muestra una *marca de agregación* gris que representa las marcas subyacentes. Cuando coloca el puntero en uno de estos iconos, una información sobre herramientas muestra el número de marcas subyacentes que se representan. Para ver las marcas, amplíe. Si amplía completamente y sigue recibiendo una marca de agregación, puede ver las marcas subyacentes en el [Informe de marcadores](../profiling/markers-report.md).

 Las marcas de agregación se dibujan en diferentes tamaños. El tamaño depende del nivel de importancia de la marca más importante en la agregación. En la ilustración siguiente se muestran las marcas de agregación en orden creciente de importancia.

 ![Agregar marcas que muestren cuatro niveles de importancia](../profiling/media/cvmarkeraggregate.png "CVMarkerAggregate") Marcas de agregación por nivel de importancia

## <a name="see-also"></a>Vea también
- [Marcadores del Visualizador de simultaneidad](../profiling/concurrency-visualizer-markers.md)
- [SDK del visualizador de simultaneidad](../profiling/concurrency-visualizer-sdk.md)