---
title: Actividad de GPU (este proceso) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d7fe5512cf131dfede701fb47df2ef956c01437d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31570390"
---
# <a name="gpu-activity-this-process"></a>Actividad GPU (Este proceso)
Los segmentos **Actividad de GPU (este proceso)** en la vista de subprocesos del visualizador de simultaneidad representan los momentos en que la GPU estaba procesando solicitudes en nombre de otros procesos del sistema. Estas solicitudes se envían a la GPU como paquetes de acceso a memoria directa (DMA). La longitud de un segmento representa el tiempo que la GPU estaba procesando un paquete de DMA en nombre del proceso actual.  
  
 Al seleccionar el segmento de actividad de GPU, el informe en la pestaña **Actual** muestra información sobre el paquete de DMA que se procesó. Esta información incluye la cantidad de tiempo que el paquete ha esperado en la cola de hardware asociada al motor de DirectX, el proceso que envió el paquete y el tiempo necesario para procesar el paquete. Puede que un proceso distinto del proceso actual haya enviado físicamente el paquete de DMA a la GPU. El visualizador de simultaneidad puede detectar cuando otro proceso ha enviado trabajo a la GPU en nombre del proceso actual.