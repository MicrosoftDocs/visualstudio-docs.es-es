---
title: Tiempo de procesamiento de la interfaz de usuario | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 391b4582d03e32e738f0eade823326e72a662a43
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56615031"
---
# <a name="ui-processing-time"></a>Tiempo de procesamiento de la interfaz de usuario
Estos segmentos de la escala de tiempo están asociados a tiempos de bloqueo que se clasifican como procesamiento de la interfaz de usuario. Esto implica que un subproceso está generando mensajes de Windows o realizando otro trabajo de la interfaz de usuario. Durante este tiempo, se ha bloqueado un subproceso en una API que el visualizador de simultaneidad está contando como procesamiento de la interfaz de usuario. Las API como `GetMessage()` y `MsgWaitForMultipleObjects()` se incluyen en este grupo.

 Si no se identifica ninguna API de bloqueo predefinida, revise las pilas de llamadas y los informes de perfil para determinar las causas subyacentes del retraso.

 La categoría de procesamiento de la interfaz de usuario ayuda a entender la capacidad de respuesta de las aplicaciones de interfaz gráfica de usuario y es conveniente en aplicaciones que dependen de la capacidad de respuesta de la interfaz de usuario. Por ejemplo, si el subproceso de interfaz de usuario en una aplicación alcanza el 100 % de tiempo de procesamiento de la interfaz de usuario, es probable que tenga capacidad de respuesta. Sin embargo, si el subproceso de interfaz de usuario emplea tiempo considerable en otras categorías, busque las causas principales y considere la posibilidad de reducir las categorías que no sean de interfaz de usuario en ese subproceso.

## <a name="see-also"></a>Vea también
- [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)