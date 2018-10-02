---
title: Tiempo de procesamiento de la interfaz de usuario | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e35f5f37b0eced2822cb4b019732210bec94495
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580294"
---
# <a name="ui-processing-time"></a>Tiempo de procesamiento de la interfaz de usuario
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [el tiempo de procesamiento de la interfaz de usuario](https://docs.microsoft.com/visualstudio/profiling/ui-processing-time).  
  
Estos segmentos de la escala de tiempo están asociados a tiempos de bloqueo que se clasifican como procesamiento de la interfaz de usuario. Esto implica que un subproceso está generando mensajes de Windows o realizando otro trabajo de la interfaz de usuario. Durante este tiempo, se ha bloqueado un subproceso en una API que el visualizador de simultaneidad está contando como procesamiento de la interfaz de usuario. Las API como `GetMessage()` y `MsgWaitForMultipleObjects()` se incluyen en este grupo.  
  
 Si no se identifica ninguna API de bloqueo predefinida, revise las pilas de llamadas y los informes de perfil para determinar las causas subyacentes del retraso.  
  
 La categoría de procesamiento de la interfaz de usuario es importante para entender la capacidad de respuesta de las aplicaciones de interfaz gráfica de usuario y es conveniente en aplicaciones que dependen de la capacidad de respuesta de la interfaz de usuario. Por ejemplo, si el subproceso de interfaz de usuario en una aplicación alcanza el 100 % de tiempo de procesamiento de la interfaz de usuario, probablemente tenga gran capacidad de respuesta. Sin embargo, si el subproceso de interfaz de usuario emplea tiempo considerable en otras categorías, busque las causas principales y considere la posibilidad de reducir las categorías que no sean de interfaz de usuario en ese subproceso.  
  
## <a name="see-also"></a>Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)



