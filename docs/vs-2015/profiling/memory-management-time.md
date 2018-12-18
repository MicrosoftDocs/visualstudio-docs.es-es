---
title: Tiempo de administración de la memoria | Microsoft Docs
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
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3fc38abb47c70949b63b44958e96e3b168589fd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729415"
---
# <a name="memory-management-time"></a>Tiempo de administración de la memoria
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Estos segmentos de la escala de tiempo están asociados a tiempos de bloqueo que se clasifican como Administración de memoria. Esto implica que un subproceso está bloqueado por un evento que está asociado a una operación de administración de memoria como la paginación. Durante este tiempo, un subproceso se ha bloqueado en una API o estado del kernel que el visualizador de simultaneidad está contando como administración de memoria. Esto incluye eventos como la paginación y la asignación de memoria.  
  
 Examine las pilas de llamadas asociadas y los informes de perfil para entender mejor las razones subyacentes de los bloqueos que se clasifican como Administración de memoria.  
  
## <a name="see-also"></a>Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)



