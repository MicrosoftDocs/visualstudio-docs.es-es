---
title: Actividad de GPU (otros procesos) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a5b38423bd629dee0f518e0f62eedcf7c55c1db0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789842"
---
# <a name="gpu-activity-other-processes"></a>Actividad GPU (Otros procesos)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los segmentos **Actividad de GPU (otros procesos)** en la vista de subprocesos del visualizador de simultaneidad representan los momentos en que la GPU estaba procesando solicitudes en nombre de otros procesos del sistema. Estas solicitudes se envían a la GPU como paquetes de acceso a memoria directa (DMA).  La longitud de un segmento representa la cantidad de tiempo que la GPU ha procesado el paquete.  
  
 Al seleccionar este tipo de segmento, el informe en la pestaña **Actual** muestra información sobre el paquete que se procesó.  La información incluye la cantidad de tiempo que el paquete ha esperado en la cola de hardware asociada al motor de DirectX, el proceso que envió el paquete y el tiempo necesario para procesar el paquete.



