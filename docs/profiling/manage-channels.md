---
title: "Administrar canales | Microsoft Docs"
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
  - "vs.cv.threads.tools.managechannels"
helpviewer_keywords: 
  - "Visualizador de simultaneidad, administrar canales"
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Administrar canales
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En la **Vista de subprocesos** en el Visualizador de simultaneidad, se pueden organizar los canales para el proceso para poder examinar determinados patrones.  Se pueden ordenar los canales, moverlos arriba y abajo, y ocultarlos o mostrarlos.  
  
## Ordenar por  
 Se puede utilizar la ordenación por control para ordenar los subprocesos usando diversos criterios, según el nivel de zoom actual.  Esto puede resultar especialmente útil cuando se busca un patrón determinado.  Se pueden ordenar por estos criterios:  
  
|Criterios|Definición|  
|---------------|----------------|  
|Hora de inicio|Ordena los subprocesos por su hora de inicio.  Es el criterio de ordenación predeterminado.|  
|Hora de finalización|Ordena subprocesos por sus tiempos finales.|  
|Execution|Ordena los temas por el porcentaje de tiempo que ha pasado en la ejecución.|  
|Sincronización|Ordena los subprocesos por el porcentaje de tiempo que ha pasado en la sincronización.|  
|E\/S|Ordena los temas por el porcentaje de tiempo que ha pasado en E\/S \(lectura y escritura de datos\).|  
|Sleep|Ordena los temas por el porcentaje de tiempo que ha pasado dormido.|  
|Paginación|Ordena los temas por el porcentaje de tiempo que ha pasado paginando.|  
|Adelantamiento|Ordena los temas por el porcentaje de tiempo que ha pasado en estado preferente.|  
|Procesamiento de interfaz de usuario|Ordena los subprocesos por el porcentaje de tiempo que ha pasado en el procesamiento de la interfaz de usuario.|  
  
## Mueve el canal seleccionado arriba o abajo  
 Se pueden utilizar estos controles para mover un canal hacia arriba o hacia abajo en la lista.  Por ejemplo, se podrían colocar los canales relacionados uno junto a otro para ayudarle a examinar un modelo determinado o una relación entre subprocesos.  
  
## Mover el canal seleccionado a la parte superior o inferior  
 Se pueden mover los canales seleccionados al principio o final de la lista para poder examinar un modelo determinado, o mover algunos canales apartados cuando se examinen otros.  
  
## Ocultar canales seleccionados  
 Elija este control cuando desee ocultar canales.  Por ejemplo, si ve un subproceso que tiene una sincronización del 100% para el transcurso de su proceso administrado, probablemente pueda ocultarlos para analizar otros subprocesos.  
  
> [!NOTE]
>  Ocultar un subproceso también lo elimina a partir del momento de cálculo, que se muestra en la leyenda activa y en los informes de perfil.  
  
## Mostrar todos los canales  
 Este control está activo cuando se ocultan uno o más canales.  Si lo elige, todos los elementos ocultos se muestran y se devuelven a los cálculos de tiempo.  
  
## Mover marcadores al principio  
 Si un seguimiento contiene eventos de marcador, se puede utilizar este comando para mover los canales de marcador a la parte superior de la escala de tiempo.  Se conserva el orden relativo.  
  
## Agrupar marcadores por subprocesos  
 Si un seguimiento contiene eventos de marcador, se puede utilizar este comando para agrupar los canales del marcador en el subproceso que generó los eventos del marcador.  Los canales de disco se mueven a la parte superior de la lista del canal y los canales de GPU se mueven a la parte inferior.  
  
## Vea también  
 [Zoom \(control\) \(Vista de subprocesos\)](../profiling/zoom-control-threads-view.md)   
 [Modo de medida Activado\/desactivado](../profiling/measure-mode-on-off.md)   
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)