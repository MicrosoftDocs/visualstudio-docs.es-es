---
title: Informe de operaciones de disco (vista de subprocesos) | Microsoft Docs
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
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe16116131c1ed6d0233abbd2e0480946b5a5423
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574244"
---
# <a name="disk-operations-report-threads-view"></a>Informe de operaciones de disco (Vista de subprocesos)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [informe de operaciones de disco (vista subprocesos)](https://docs.microsoft.com/visualstudio/profiling/disk-operations-report-threads-view).  
  
En el informe de operaciones de disco se muestran las operaciones de E/S de disco en los canales de disco.  
  
 Para cada acceso de disco que se produce en nombre del proceso del que se está generando el perfil en la ventana de tiempo actualmente visible, se notifica la información siguiente:  
  
-   El nombre y el PID del proceso que realiza el acceso al disco  
  
-   El identificador del subproceso que tiene acceso el disco  
  
-   El nombre del archivo al que se ha accedido  
  
-   El número de lecturas por archivo  
  
-   El número de bytes leídos  
  
-   La latencia de lectura, en milisegundos  
  
-   El número de escrituras  
  
-   El número de bytes escritos  
  
-   La latencia de escritura, en milisegundos  
  
## <a name="see-also"></a>Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)



