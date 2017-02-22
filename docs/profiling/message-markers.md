---
title: "Marcadores de mensaje | Microsoft Docs"
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
  - "vs.cv.markers.message"
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Marcadores de mensaje
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un marcador de mensaje representa la salida del registro.  Un mensaje es una cadena que es emitida por un subproceso concreto en un momento concreto.  Se pueden exportar mensajes a un archivo de texto con otras herramientas.  Se puede hacer descansar el puntero de un mensaje en el Visualizador de simultaneidad para ver la cadena del mensaje.  Y se pueden ver todos los marcadores del mensaje en [Informe de marcadores](../profiling/markers-report.md).  La ilustración siguiente muestra un marcador de mensaje.  
  
## Marcadores de agregación de mensajes  
 A veces varios mensajes aparecen tan cerca uno del otro en el Visualizador de simultaneidad que no se pueden ser dibujar individualmente.  Cuando esto ocurre, se muestra *un marcador de agregación de mensajes* que representa los mensajes subyacentes.  Cuando se sitúa el puntero en uno de estos iconos, un mensaje muestra el número de los mensajes subyacentes que se representan.  Para ver los mensajes, zoom.  Si el zoom hasta el final y todavía obtiene un marcador de agregación, puede ver los mensajes subyacentes en [Informe de marcadores](../profiling/markers-report.md).  
  
## Vea también  
 [Marcadores del Visualizador de simultaneidad](../profiling/concurrency-visualizer-markers.md)   
 [SDK del Visualizador de simultaneidad](../profiling/concurrency-visualizer-sdk.md)