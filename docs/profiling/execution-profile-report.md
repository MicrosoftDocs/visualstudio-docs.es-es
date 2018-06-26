---
title: Informe del perfil de ejecución | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Profile Report
ms.assetid: c8128472-a8ed-46f4-b1c8-a25358d6f2c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 92f053cbf6f85edbe79f0b108093410502f39a9f
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764519"
---
# <a name="execution-profile-report"></a>Informe del perfil de ejecución
El informe del perfil de ejecución es un perfil de muestreo tradicional. Se toman muestras aproximadamente cada milisegundo durante los períodos cuando un subproceso se está ejecutando en un núcleo lógico, y el visualizador de simultaneidad intercala el conjunto acumulado de pilas de muestras para generar un árbol de llamadas típico. Los datos de esta tabla pueden verse afectados por el intervalo de tiempo actual y los subprocesos ocultos, así como por estos filtros que se pueden aplicar:  
  
-   Si se selecciona Solo mi código, solo se muestran los marcos de pila que tienen código del usuario, más un nivel por debajo del código del usuario.  
  
-   Si se establece el valor Reducción de nodos irrelevantes, las pilas recopiladas cuya frecuencia es menor que la especificada se filtran del informe  
  
 En la tabla siguiente se muestran las columnas del informe.  
  
|Columna|Description|  
|------------|-----------------|  
|nombre|El nombre de la función para cada nivel de la pila de llamadas.|  
|Muestras inclusivas|Número total de muestras recopiladas para todas las pilas que se acumulan en este nivel del árbol de pila de llamadas. El número inclusivo es la suma de muestras exclusivas de esta función y de contadores inclusivos para todos sus nodos secundarios.|  
|Muestras exclusivas|Número total de muestras recopiladas para las que esta función es el nivel más bajo de la pila de llamadas.|  
|% de inclusivas|El porcentaje de muestras totales que se muestra en la columna de muestras inclusivas. Los porcentajes se redondean a dos posiciones decimales.|  
|% de exclusivas|El porcentaje de muestras totales que se muestra en la columna de muestras exclusivas. Los porcentajes se redondean a dos posiciones decimales.|  
|Detalles|Nombre completo de la función. Esto incluye el recuento de líneas cuando está disponible.|  
  
 Esta tabla de informe se puede ver en la vista [Tiempo de ejecución (vista de subprocesos)](../profiling/execution-time-threads-view.md).  
  
## <a name="see-also"></a>Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)