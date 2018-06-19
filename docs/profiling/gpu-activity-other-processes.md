---
title: Actividad de GPU (otros procesos) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 586aeb9b2b6d674c14106a911872c967c272f3e6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31573081"
---
# <a name="gpu-activity-other-processes"></a>Actividad GPU (Otros procesos)
Los segmentos **Actividad de GPU (otros procesos)** en la vista de subprocesos del visualizador de simultaneidad representan los momentos en que la GPU estaba procesando solicitudes en nombre de otros procesos del sistema. Estas solicitudes se envían a la GPU como paquetes de acceso a memoria directa (DMA).  La longitud de un segmento representa la cantidad de tiempo que la GPU ha procesado el paquete.  
  
 Al seleccionar este tipo de segmento, el informe en la pestaña **Actual** muestra información sobre el paquete que se procesó.  La información incluye la cantidad de tiempo que el paquete ha esperado en la cola de hardware asociada al motor de DirectX, el proceso que envió el paquete y el tiempo necesario para procesar el paquete.