---
title: Informe de operaciones de disco (vista de subprocesos) | Microsoft Docs
description: En el informe de operaciones de disco se muestran las operaciones de E/S de disco en los canales de disco. Consulte la información notificada para cada acceso al disco.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44975999c71b1c331d90aa10f709071cef466cb1
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686537"
---
# <a name="disk-operations-report-threads-view"></a>Informe de operaciones de disco (Vista de subprocesos)
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

## <a name="see-also"></a>Vea también
- [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)