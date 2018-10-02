---
title: Marcadores de intervalo | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee6943210a4a333625e524afe020e9994824daee
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47565744"
---
# <a name="span-markers"></a>Marcadores de intervalo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [marcadores de intervalo](https://docs.microsoft.com/visualstudio/profiling/span-markers).  
  
Un marcador de intervalo representa una fase significativa de una aplicación. Por ejemplo, puede usar un intervalo para representar un intervalo de tiempo durante el cual se está procesando un elemento de trabajo determinado. Su longitud representa la duración de la fase de la aplicación correspondiente. Esta ilustración muestra un intervalo en el visualizador de simultaneidad:  
  
 ![Un marcador de intervalo en el visualizador de simultaneidad](../profiling/media/cvmarkerspan.png "CVMarkerSpan")  
Un marcador de intervalo en el visualizador de simultaneidad  
  
## <a name="span-category"></a>Categoría de intervalo  
 Se muestra un marcador de intervalo en uno de los cinco colores diferentes, dependiendo de su categoría. Los colores se repiten si hay más de cinco categorías. La categoría puede ser cualquier número entero. Esta ilustración muestra los cinco colores posibles:  
  
 ![Cinco intervalos en distintas categorías](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory")  
Los colores de las cinco primeras categorías de intervalo  
  
## <a name="span-aggregation-markers"></a>Marcadores de agregación de intervalo  
 En ocasiones los marcadores de intervalo se producen tan cerca de otros en el visualizador de simultaneidad que no se pueden dibujar individualmente. Cuando esto ocurre, se muestra un *marcador de agregación de intervalo* gris que representa los intervalos subyacentes. Cuando coloca el puntero en uno de estos iconos, una información sobre herramientas muestra el número de intervalos subyacentes que se representan. Amplíe para ver los intervalos. Si amplía completamente y sigue recibiendo un marcador de agregación de intervalo, puede ver los marcadores de intervalo subyacentes en el [Informe de marcadores](../profiling/markers-report.md). Esta ilustración muestra un marcador de agregación de intervalo:  
  
 ![Un marcador de agregación de intervalo en el visualizador de simultaneidad](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate")  
Un marcador de agregación de intervalo  
  
## <a name="see-also"></a>Vea también  
 [Marcadores del visualizador de simultaneidad](../profiling/concurrency-visualizer-markers.md)   
 [SDK del visualizador de simultaneidad](../profiling/concurrency-visualizer-sdk.md)



