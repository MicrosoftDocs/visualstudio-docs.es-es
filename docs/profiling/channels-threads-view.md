---
title: Canales (Vista de subprocesos) | Microsoft Docs
description: Obtenga información sobre la vista Subprocesos al usar canales en el visualizador de simultaneidad de Visual Studio. Vea canales de subprocesos, canales de disco, canales de marcadores y canales de GPU.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.channelnames
helpviewer_keywords:
- Concurrency Visualizer, Channels (Threads View)
ms.assetid: 2f798c17-2363-42a4-be94-a5751d208eac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a4ed0a82ad7ddb67cacde2a09f595d0c9250710
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148616"
---
# <a name="channels-threads-view"></a>Canales (vista Subprocesos)
El visualizador de simultaneidad muestra cuatro tipos de canales: canales de subprocesos, de discos, de marcador y de GPU.

## <a name="thread-channels"></a>Canales de subproceso
 Un canal de subproceso muestra el estado, por color, de un solo subproceso. Al detenerse en el nombre del canal, se muestra la función de inicio del subproceso especificado. El visualizador de simultaneidad detecta varios tipos de subprocesos. Los tipos más comunes se muestran en la tabla siguiente.

|Thread|Descripción|
|-|-|
|Subproceso principal|El subproceso que inició la aplicación.|
|Subproceso de trabajo|Un subproceso creado por el subproceso principal de la aplicación.|
|Subproceso de trabajo CLR|Un subproceso de trabajo creado por Common Language Runtime (CLR).|
|Asistente de depuración|Un subproceso de trabajo creado por el depurador de Visual Studio.|
|Subproceso ConcRT|Un subproceso creado por el Runtime de simultaneidad de Microsoft.|
|Subproceso GDI|Un subproceso creado por GDIPlus.|
|Subproceso OLE/RPC|Un subproceso creado como un subproceso de trabajo RPC.|
|Subproceso RPC|Un subproceso creado como un subproceso RPC.|
|Subproceso Winsock|Un subproceso creado como un subproceso Winsock.|
|Grupo de subprocesos|Un subproceso creado por el grupo de subprocesos de CLR.|

## <a name="disk-channels"></a>Canales de disco
 Los canales de disco se corresponden con las unidades físicas del equipo. Dado que existen canales independientes para las operaciones de lectura y escritura de cada unidad física del sistema, cada unidad tiene dos canales. Los números de disco se corresponden con los nombres de dispositivo del kernel. Un canal de disco solo se muestra si hubo actividad en el disco.

## <a name="marker-channels"></a>Canales de marcador
 Los canales de marcador se corresponden con los eventos generados por la aplicación y las bibliotecas que utiliza. Por ejemplo, la biblioteca TPL, la biblioteca de patrones paralelos y C++ AMP generan eventos que se muestran como marcadores. Cada canal de marcador se asocia a un identificador de subproceso, que se muestra junto a la descripción del canal. El identificador identifica el subproceso que generó el evento. La descripción del canal incluye el nombre del proveedor de seguimiento de eventos para Windows (ETW) que generó los eventos. Si el canal muestra eventos desde el [SDK del visualizador de simultaneidad](../profiling/concurrency-visualizer-sdk.md), también se muestra el nombre de la serie.

## <a name="gpu-channels"></a>Canales de GPU
 Los canales de GPU muestran información sobre la actividad de DirectX 11 en el sistema.  Cada motor de DirectX asociado a la tarjeta gráfica tiene un canal diferente.  Los segmentos individuales representan el tiempo dedicado a procesar un paquete DMA.

## <a name="see-also"></a>Vea también
- [Vista Subprocesos](../profiling/threads-view-parallel-performance.md)