---
title: Administrar canales | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.managechannels
helpviewer_keywords:
- Concurrency Visualizer, Manage Channels
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b1480bab2f52383a8ca3a5b0ac22fd56acb5e01
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "64779242"
---
# <a name="manage-channels"></a>Administrar canales
En la **vista Subprocesos** del visualizador de simultaneidad, puede organizar los canales de su proceso para así poder examinar modelos concretos. Para ordenar los canales, desplácelos hacia arriba o abajo y ocúltelos o muéstrelos.

## <a name="sort-by"></a>Ordenar por
 Puede utilizar el control de ordenación para ordenar los subprocesos según criterios diferentes, según el nivel de zoom actual. Esto es especialmente útil cuando se busca un patrón determinado. Puede ordenar por estos criterios:

|Criterios|de esquema JSON|
|--------------|----------------|
|Hora de inicio|Ordena los subprocesos por sus horas de inicio. Este es el orden predeterminado.|
|Hora de finalización|Ordena los subprocesos por sus horas de finalización.|
|Execution|Ordena los subprocesos por el porcentaje de tiempo que ha pasado ejecutándose.|
|Sincronización|Ordena los subprocesos por el porcentaje de tiempo que ha pasado sincronizándose.|
|E/S|Ordena los subprocesos por el porcentaje de tiempo que invertido en E/S (lectura y escritura de datos).|
|Sleep|Ordena los subprocesos por el porcentaje de tiempo que ha pasado en reposo.|
|Paginación|Ordena los subprocesos por el porcentaje de tiempo que ha pasado paginando.|
|Adelantamiento|Ordena los subprocesos por el porcentaje de tiempo que ha pasado adelantando.|
|Procesamiento de IU|Ordena los subprocesos por el porcentaje de tiempo que ha pasado procesando la interfaz de usuario.|

## <a name="move-selected-channel-up-or-down"></a>Mover el canal seleccionado hacia arriba o abajo
 Puede utilizar estos controles para desplazar un canal hacia arriba o abajo en la lista. Por ejemplo, podría colocar canales relacionados juntos para ayudarle a examinar un patrón determinado o una relación entre subprocesos.

## <a name="move-selected-channel-to-top-or-bottom"></a>Mover el canal seleccionado a la parte superior o inferior
 Puede mover los canales seleccionados al principio o al final de la lista para poder examinar un modelo determinado, o bien apartar algunos canales cuando examina otros.

## <a name="hide-selected-channels"></a>Ocultar los canales seleccionados
 Elija este control cuando desee ocultar canales. Por ejemplo, si un subproceso está al cien por ciento de sincronización durante la vida de su proceso administrado, puede ocultarlo mientras analiza otros subprocesos.

> [!NOTE]
> Ocultar un subproceso también lo quita de la hora de cálculo, que se muestra en la leyenda activa y en los informes de perfil.

## <a name="show-all-channels"></a>Mostrar todos los canales
 Este control está activado cuando se ocultan uno o más canales. Si lo elige, todos los elementos ocultos se muestran y se devuelven a los cálculos de tiempo.

## <a name="move-markers-to-top"></a>Mover marcadores arriba
 Si un seguimiento contiene eventos de marcador, puede usar este comando para mover los canales de marcador a la parte superior de la escala de tiempo. Se conserva su orden relativo.

## <a name="group-markers-by-thread"></a>Agrupar marcadores por subproceso
 Si un seguimiento contiene eventos de marcador, puede usar este comando para agrupar canales de marcador en el subproceso que generó los eventos de marcador.  Los canales de disco se mueven a la parte superior de la lista de canales y los canales GPU se mueven a la parte inferior.

## <a name="see-also"></a>Vea también
- [Control de zoom (vista Subprocesos)](../profiling/zoom-control-threads-view.md)
- [Modo de medida activado/desactivado](../profiling/measure-mode-on-off.md)
- [Vista Subprocesos](../profiling/threads-view-parallel-performance.md)