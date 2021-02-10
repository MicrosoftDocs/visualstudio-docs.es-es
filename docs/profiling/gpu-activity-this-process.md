---
title: Actividad de GPU (este proceso) | Microsoft Docs
description: Obtenga información sobre los segmentos GPU Activity (This Process) (Actividad de GPU [Este proceso]) en la vista Threads (Subprocesos) del visualizador de simultaneidad.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bdb39504cae42e943de1864d8edc308b96e0e742
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878141"
---
# <a name="gpu-activity-this-process"></a>Actividad GPU (Este proceso)
Los segmentos **Actividad de GPU (este proceso)** en la vista de subprocesos del visualizador de simultaneidad representan los momentos en que la GPU estaba procesando solicitudes en nombre de otros procesos del sistema. Estas solicitudes se envían a la GPU como paquetes de acceso a memoria directa (DMA). La longitud de un segmento representa el tiempo que la GPU estaba procesando un paquete de DMA en nombre del proceso actual.

 Al seleccionar el segmento de actividad de GPU, el informe en la pestaña **Actual** muestra información sobre el paquete de DMA que se procesó. Esta información incluye la cantidad de tiempo que el paquete ha esperado en la cola de hardware asociada al motor de DirectX, el proceso que envió el paquete y el tiempo necesario para procesar el paquete. Puede que un proceso distinto del proceso actual haya enviado físicamente el paquete de DMA a la GPU. El visualizador de simultaneidad puede detectar cuando otro proceso ha enviado trabajo a la GPU en nombre del proceso actual.