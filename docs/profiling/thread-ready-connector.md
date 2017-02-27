---
title: "Conector listo para subprocesos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.threadready"
helpviewer_keywords: 
  - "Visualizador de simultaneidad, Preparado para subprocesos"
ms.assetid: 68e1ec38-4b10-4b01-b32f-6c9a00b2443c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Conector listo para subprocesos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Al hacer clic en un segmento de bloqueo para ver una pila de llamadas y su pila de desbloqueo, también puede aparecer el conector preparado para subprocesos.  Si el evento de desbloqueo se generara en otro subproceso del proceso actual, el conector preparado para subprocesos identifica visualmente el subproceso y el segmento de ejecución que permitieron al subproceso bloqueado reanudar la ejecución.