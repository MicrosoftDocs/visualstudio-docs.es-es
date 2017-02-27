---
title: "Tiempo de procesamiento de la interfaz de usuario | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.uiprocessing"
helpviewer_keywords: 
  - "Visualizador de simultaneidad, Tiempo de procesamiento de la interfaz de usuario"
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Tiempo de procesamiento de la interfaz de usuario
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Estos segmentos de la escala de tiempo están asociados a tiempos de bloqueo que se clasifican como Procesamiento de IU.  Esto implica que un subproceso está generando mensajes de Windows o realizando otro trabajo de la interfaz de usuario.  Durante este período de tiempo, un subproceso se ha bloqueado en una API que el visualizador de simultaneidad identifica como Procesamiento de IU.  Las API como `GetMessage()` y `MsgWaitForMultipleObjects()` se incluyen en este grupo.  
  
 Si no se identifica ninguna API de bloqueo predefinida, revise las pilas de llamadas y los informes del perfil para determinar las causas subyacentes del retraso.  
  
 La categoría Procesamiento de IU es importante para entender la capacidad de respuesta de las aplicaciones GUI y es conveniente en aplicaciones que dependen de la capacidad de respuesta de la interfaz de usuario.  Por ejemplo, si el subproceso de la interfaz de usuario de una aplicación consigue registrar un tiempo de 100% en Procesamiento de IU, probablemente tenga una capacidad de respuesta muy elevada.  Sin embargo, si el subproceso de la interfaz de usuario invierte una gran cantidad de tiempo en otras categorías, busque las causas principales y considere la posibilidad de reducir las categorías no relacionadas con la interfaz de usuario en ese subproceso.  
  
## Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)