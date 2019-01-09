---
title: Marcadores de mensaje | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.message
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13cd156263584fb65c2e69df9f86e4610fc5eb3a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846508"
---
# <a name="message-markers"></a>Marcadores de mensaje
Un marcador de mensaje representa el resultado del registro. Un mensaje es una cadena emitida por un subproceso concreto en un momento determinado. Los mensajes se pueden exportar a un archivo de texto para su uso con otras herramientas. Al colocar el puntero sobre un mensaje en el visualizador de simultaneidad, se ve la cadena del mensaje. En el [Informe de marcadores](../profiling/markers-report.md) se pueden ver todos los marcadores de mensaje.  En la siguiente ilustración se muestra un marcador de mensajes.  
  
## <a name="message-aggregation-markers"></a>Marcadores de agregación de mensajes  
 En ocasiones, los mensajes aparecen tan cerca unos de otros en el visualizador de simultaneidad que no se pueden extraer individualmente. Cuando esto ocurre, se muestra un *marcador de agregación de mensajes* que representa los mensajes subyacentes. Al colocar el puntero en uno de estos iconos, se muestra información sobre el número de mensajes subyacentes que se representan. Para ver los mensajes, amplíe la imagen.  Si amplía completamente y sigue recibiendo un marcador de agregación, puede ver los mensajes subyacentes en el [Informe de marcadores](../profiling/markers-report.md).  
  
## <a name="see-also"></a>Vea también  
 [Marcadores del Visualizador de simultaneidad](../profiling/concurrency-visualizer-markers.md)   
 [SDK del visualizador de simultaneidad](../profiling/concurrency-visualizer-sdk.md)