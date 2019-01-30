---
title: Actividad de GPU (otros procesos) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c7d68547e0c2d0b056e2c60f1e9e183270841c6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55030267"
---
# <a name="gpu-activity-other-processes"></a>Actividad GPU (Otros procesos)
Los segmentos **Actividad de GPU (otros procesos)** en la vista de subprocesos del visualizador de simultaneidad representan los momentos en que la GPU estaba procesando solicitudes en nombre de otros procesos del sistema. Estas solicitudes se envían a la GPU como paquetes de acceso a memoria directa (DMA).  La longitud de un segmento representa la cantidad de tiempo que la GPU ha procesado el paquete.  
  
 Al seleccionar este tipo de segmento, el informe en la pestaña **Actual** muestra información sobre el paquete que se procesó.  La información incluye la cantidad de tiempo que el paquete ha esperado en la cola de hardware asociada al motor de DirectX, el proceso que envió el paquete y el tiempo necesario para procesar el paquete.