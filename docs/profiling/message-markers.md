---
title: Marcadores de mensaje | Microsoft Docs
description: Obtenga información sobre cómo puede exportar mensajes a un archivo de texto para usarlo con otras herramientas y colocar el puntero en un mensaje del Visualizador de simultaneidad para ver la cadena de mensaje.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.message
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d0ce91a47bb2158f3cf684e1634a684f372a044d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879948"
---
# <a name="message-markers"></a>Marcadores de mensaje
Un marcador de mensaje representa el resultado del registro. Un mensaje es una cadena emitida por un subproceso concreto en un momento determinado. Los mensajes se pueden exportar a un archivo de texto para su uso con otras herramientas. Al colocar el puntero sobre un mensaje en el visualizador de simultaneidad, se ve la cadena del mensaje. En el [Informe de marcadores](../profiling/markers-report.md) se pueden ver todos los marcadores de mensaje.  En la siguiente ilustración se muestra un marcador de mensajes.

## <a name="message-aggregation-markers"></a>Marcadores de agregación de mensajes
 En ocasiones, los mensajes aparecen tan cerca unos de otros en el visualizador de simultaneidad que no se pueden extraer individualmente. Cuando esto ocurre, se muestra un *marcador de agregación de mensajes* que representa los mensajes subyacentes. Al colocar el puntero en uno de estos iconos, se muestra información sobre el número de mensajes subyacentes que se representan. Para ver los mensajes, amplíe la imagen.  Si amplía completamente y sigue recibiendo un marcador de agregación, puede ver los mensajes subyacentes en el [Informe de marcadores](../profiling/markers-report.md).

## <a name="see-also"></a>Consulte también
- [Marcadores del Visualizador de simultaneidad](../profiling/concurrency-visualizer-markers.md)
- [SDK del visualizador de simultaneidad](../profiling/concurrency-visualizer-sdk.md)