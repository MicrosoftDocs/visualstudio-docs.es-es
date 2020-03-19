---
title: Marcadores de mensaje | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.message
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b668f0331345e6a1022ef79105614f4a22e91d9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "62830083"
---
# <a name="message-markers"></a>Marcadores de mensaje
Un marcador de mensaje representa el resultado del registro. Un mensaje es una cadena emitida por un subproceso concreto en un momento determinado. Los mensajes se pueden exportar a un archivo de texto para su uso con otras herramientas. Al colocar el puntero sobre un mensaje en el visualizador de simultaneidad, se ve la cadena del mensaje. En el [Informe de marcadores](../profiling/markers-report.md) se pueden ver todos los marcadores de mensaje.  En la siguiente ilustración se muestra un marcador de mensajes.

## <a name="message-aggregation-markers"></a>Marcadores de agregación de mensajes
 En ocasiones, los mensajes aparecen tan cerca unos de otros en el visualizador de simultaneidad que no se pueden extraer individualmente. Cuando esto ocurre, se muestra un *marcador de agregación de mensajes* que representa los mensajes subyacentes. Al colocar el puntero en uno de estos iconos, se muestra información sobre el número de mensajes subyacentes que se representan. Para ver los mensajes, amplíe la imagen.  Si amplía completamente y sigue recibiendo un marcador de agregación, puede ver los mensajes subyacentes en el [Informe de marcadores](../profiling/markers-report.md).

## <a name="see-also"></a>Vea también
- [Marcadores del Visualizador de simultaneidad](../profiling/concurrency-visualizer-markers.md)
- [SDK del visualizador de simultaneidad](../profiling/concurrency-visualizer-sdk.md)