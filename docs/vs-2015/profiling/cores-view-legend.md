---
title: Leyenda de la vista Núcleos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.legend
helpviewer_keywords:
- Concurrency Visualizer, Cores View Legend
ms.assetid: e160384c-fcfe-49b3-86b7-229adb736c51
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 05f768f6ff928ab00ebbd503c1ae9826dab8cd38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161299"
---
# <a name="cores-view-legend"></a>Leyenda de la vista Núcleos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La leyenda de la vista Núcleos identifica cada subproceso por color y nombre. Incluye columnas que muestran recuentos para los cambios de contexto entre núcleos, el total de cambios de contexto y el porcentaje de cambios de contexto que atraviesan núcleos. Las filas de la leyenda se ordenan por el número de cambios de contexto entre núcleos, en orden decreciente.  
  
 Puede seleccionar filas de la leyenda para filtrar los subprocesos que se muestran en la escala de tiempo. En la escala de tiempo solo se muestran los subprocesos seleccionados. Si no se selecciona ninguna fila, todas las filas se muestran en la escala de tiempo.  
  
 Los cambios de contexto entre núcleos tienen un mayor coste de rendimiento y sobrecarga que los cambios que permanecen en el mismo núcleo lógico. Durante los cambios de contexto, se guardan y se restauran los registros del procesador, se ejecuta el código de kernel del sistema operativo, se recargan las entradas de búfer de traducción de direcciones y se vacía la canalización del procesador. Los cambios de contexto entre núcleos pueden ser incluso más costosos que otros cambios de contexto porque los datos de la memoria caché no son válidos para este subproceso en otro núcleo. En cambio, si un subproceso se cambia de contexto en el núcleo en que se ejecutó previamente, es probable que los datos útiles estén todavía en la memoria caché. Cuando los cambios de contexto entre núcleos han aumentado a causa de intentos de administrar la afinidad de subprocesos y el rendimiento se degrada, considere la posibilidad de abordar este problema. Comience por eliminar la afinidad de subprocesos y, a continuación, observe el comportamiento entre núcleos resultante.  
  
 En la siguiente tabla se describen los elementos de la leyenda.  
  
|Elemento|de esquema JSON|  
|-------------|----------------|  
|Nombre del subproceso|Muestra el color del subproceso en la escala de tiempo de núcleos anterior y el nombre del subproceso.|  
|Cambios de contexto entre núcleos|El número de cambios de contexto para un subproceso que también cambió de un núcleo lógico a otro. No distingue los cambios de contexto entre núcleos que pasan de una matriz de procesadores a otra de los que permanecen en la misma matriz.|  
|Total de cambios de contexto|El número total de cambios de contexto para un subproceso determinado durante el periodo de muestreo. Cada vez que un subproceso cambia de contexto (por ejemplo, de ejecución a sincronización), se cuenta un cambio de contexto.|  
|Porcentaje de cambios de contexto que atraviesan núcleos|Se calcula como un porcentaje obtenido de la división del número de cambios de contexto entre núcleos entre el número total de cambios de contexto. Cuanto mayor sea este porcentaje, mayor será el efecto general de la sobrecarga de cambios de contexto entre núcleos en el rendimiento de este subproceso concreto.|  
  
## <a name="see-also"></a>Consulte también  
 [Vista Núcleos](../profiling/cores-view.md)
