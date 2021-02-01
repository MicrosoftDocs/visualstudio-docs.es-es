---
title: Segmento de escala de tiempo vacío | Microsoft Docs
description: En el visualizador de simultaneidad de Visual Studio, entienda por qué una sección de una escala de tiempo puede estar vacía (tiene un fondo blanco) para un tipo de canal.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15dc4526ce101e21c00fe083b85f81db92bcd609
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801430"
---
# <a name="empty-timeline-segment"></a>Segmento de escala de tiempo vacío
En el visualizador de simultaneidad, el motivo por el que una sección de la escala de tiempo está vacía (tiene un fondo blanco) depende del tipo de canal.

- Un canal de subproceso de CPU, significa que el subproceso no existió durante esta parte de la escala de tiempo. Si está interesado en el subproceso, puede encontrar su sección en ejecución mediante el control de zoom o el desplazamiento horizontal.

- Para un canal de E/S, significa que no se ha producido ningún acceso al disco en nombre del proceso de destino en ese momento.

- Para un canal de DirectX, significa que no se ha realizado ningún trabajo de GPU en nombre del proceso de destino durante esta parte de la escala de tiempo.

- Un canal de marcador, significa que no se generó ningún marcador.

## <a name="see-also"></a>Vea también
- [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)
- [Control de zoom (vista Subprocesos)](../profiling/zoom-control-threads-view.md)