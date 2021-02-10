---
title: Marcadores de intervalo | Microsoft Docs
description: Obtenga más información sobre cómo un marcador de intervalo representa una fase significativa de una aplicación y consulte un ejemplo en el que se muestra un intervalo en el visualizador de simultaneidad.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 526d82194a4ed1463c802296cb97c95e0eb41d33
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960148"
---
# <a name="span-markers"></a>Marcadores de intervalo
Un marcador de intervalo representa una fase significativa de una aplicación. Por ejemplo, puede usar un intervalo para representar un intervalo de tiempo durante el cual se está procesando un elemento de trabajo determinado. Su longitud representa la duración de la fase de la aplicación correspondiente. Esta ilustración muestra un intervalo en el visualizador de simultaneidad:

 ![Marcador de intervalo en el visualizador de simultaneidad](../profiling/media/cvmarkerspan.png "CVMarkerSpan") Marcador de intervalo en el visualizador de simultaneidad

## <a name="span-category"></a>Categoría de intervalo
 Se muestra un marcador de intervalo en uno de los cinco colores diferentes, dependiendo de su categoría. Los colores se repiten si hay más de cinco categorías. La categoría puede ser cualquier número entero. Esta ilustración muestra los cinco colores posibles:

 ![Cinco intervalos en distintas categorías](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory") Colores de las cinco primeras categorías de intervalo

## <a name="span-aggregation-markers"></a>Marcadores de agregación de intervalo
 En ocasiones los marcadores de intervalo se producen tan cerca de otros en el visualizador de simultaneidad que no se pueden dibujar individualmente. Cuando esto ocurre, se muestra un *marcador de agregación de intervalo* gris que representa los intervalos subyacentes. Cuando coloca el puntero en uno de estos iconos, una información sobre herramientas muestra el número de intervalos subyacentes que se representan. Amplíe para ver los intervalos. Si amplía completamente y sigue recibiendo un marcador de agregación de intervalo, puede ver los marcadores de intervalo subyacentes en el [Informe de marcadores](../profiling/markers-report.md). Esta ilustración muestra un marcador de agregación de intervalo:

 ![Marcador de agregación de intervalo en el visualizador de simultaneidad](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate") Marcador de agregación de intervalo

## <a name="see-also"></a>Consulte también
- [Marcadores del Visualizador de simultaneidad](../profiling/concurrency-visualizer-markers.md)
- [SDK del visualizador de simultaneidad](../profiling/concurrency-visualizer-sdk.md)