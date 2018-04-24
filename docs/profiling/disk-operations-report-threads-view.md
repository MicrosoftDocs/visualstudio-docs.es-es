---
title: Informe de operaciones de disco (vista de subprocesos) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: afe999ea56dbbdfd2179307f69ec12df92c612e9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="disk-operations-report-threads-view"></a>Informe de operaciones de disco (Vista de subprocesos)
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