---
title: Informe de operaciones de disco (vista de subprocesos) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: daace3e78cca67fd9b44144cd6c8a5608dbd9a1e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202439"
---
# <a name="disk-operations-report-threads-view"></a>Informe de operaciones de disco (Vista de subprocesos)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En el informe de operaciones de disco se muestran las operaciones de E/S de disco en los canales de disco.  
  
 Para cada acceso de disco que se produce en nombre del proceso del que se está generando el perfil en la ventana de tiempo actualmente visible, se notifica la información siguiente:  
  
- El nombre y el PID del proceso que realiza el acceso al disco  
  
- El identificador del subproceso que tiene acceso el disco  
  
- El nombre del archivo al que se ha accedido  
  
- El número de lecturas por archivo  
  
- El número de bytes leídos  
  
- La latencia de lectura, en milisegundos  
  
- El número de escrituras  
  
- El número de bytes escritos  
  
- La latencia de escritura, en milisegundos  
  
## <a name="see-also"></a>Consulte también  
 [Vista Subprocesos](../profiling/threads-view-parallel-performance.md)
