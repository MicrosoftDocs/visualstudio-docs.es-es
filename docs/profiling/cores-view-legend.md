---
title: "Leyenda de la vista N&#250;cleos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.cores.legend"
helpviewer_keywords: 
  - "Visualizador de simultaneidad, leyenda de la vista de núcleos"
ms.assetid: e160384c-fcfe-49b3-86b7-229adb736c51
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Leyenda de la vista N&#250;cleos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La leyenda de la vista Núcleos identifica cada subproceso por color y nombre.  Incluye columnas que muestran recuentos para cambios de contexto entre núcleos, el total de cambios de contexto y el porcentaje de cambios de contexto entre núcleos.  Las filas de la leyenda se ordenan por el número de cambios de contexto entre núcleos, en orden descendente.  
  
 Puede seleccionar filas de la leyenda para filtrar los subprocesos que se muestran en la escala de tiempo.  Sólo los subprocesos seleccionados se muestran en la escala de tiempo.  Si no hay ninguna fila seleccionada, todas las filas se muestran en la escala de tiempo.  
  
 Los cambios de contexto entre núcleos son más costosos en cuanto a sobrecarga y rendimiento que los que permanecen en un mismo núcleo lógico.  Durante los cambios de contexto, se guardan y se restauran los registros del procesador, se ejecuta el código de kernel del sistema operativo, se recargan las entradas de búfer de almacenamiento de traducción y se vacía la canalización del procesador.  Los cambios de contexto entre núcleos pueden ser aún más costosos que otros cambios de contexto porque los datos de la memoria caché no son válidos para este subproceso en otro núcleo.  En cambio, si un subproceso se cambia de contexto basándose en el núcleo en el que se ejecutó previamente, es probable que los datos útiles todavía estén en la memoria caché.  Cuando los cambios de contexto entre núcleos han aumentado por los intentos de controlar la afinidad de subprocesos y el rendimiento ha empeorado, piense en arreglar el problema.  Inicie eliminando la afinidad de subprocesos y observe el comportamiento resultante en los núcleos.  
  
 En la tabla siguiente se describen los elementos de la leyenda.  
  
|Elemento|Definición|  
|--------------|----------------|  
|Nombre del subproceso|Muestra el color y el nombre del subproceso de la escala de tiempo de núcleos previa.|  
|Cambios de contexto entre núcleos|El número de cambios de contexto para un subproceso que también cambió de un núcleo lógico a otro.  No hay diferencia entre los cambios de contexto entre núcleos que atraviesan de un procesador a otro y los que permanecen en el mismo procesador.|  
|Total de cambios de contexto|El número total de cambios de contexto para un subproceso determinado durante el periodo de muestreo.  Cada vez que un subproceso cambia de contexto \(por ejemplo, de ejecución a sincronización\) se cuenta un cambio de contexto.|  
|Porcentaje de cambios de contexto que atraviesan núcleos|Se calcula como un porcentaje dividiendo el número de cambios de contexto que atraviesan núcleos por el número de cambios de contexto totales.  Cuanto mayor sea este porcentaje, mayor será el efecto total de la sobrecarga de los cambios de contexto que atraviesan núcleos sobre el rendimiento de este subproceso concreto.|  
  
## Vea también  
 [Vista de núcleos](../profiling/cores-view.md)