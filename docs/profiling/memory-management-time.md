---
title: "Tiempo de administraci&#243;n de la memoria | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.paging"
helpviewer_keywords: 
  - "Visualizador de simultaneidad, Tiempo de paginación"
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Tiempo de administraci&#243;n de la memoria
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Estos segmentos de la escala de tiempo están asociados a tiempos de bloqueo que se clasifican como Administración de memoria.  Esto implica que un subproceso está bloqueado por un evento que está asociado con una operación de administración de memoria, como Paginación.  Durante este tiempo, un subproceso se ha bloqueado en una API o estado del kernel que el Visualizador de simultaneidad está contando como administración de memoria.  Aquí se incluyen eventos como paginación y asignación de memoria.  
  
 Examine las pilas de llamadas y los informes de perfil asociados para entender mejor las razones subyacentes de los bloques que se clasifican como administración de memoria.  
  
## Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)