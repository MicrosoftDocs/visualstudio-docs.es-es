---
title: Escala de tiempo de la vista Núcleos | Microsoft Docs
description: 'Obtenga más información sobre los conceptos básicos de la escala de tiempo: cómo determinar qué subproceso se ejecutó en qué núcleo en un momento específico, y cómo acercar y alejar la vista.'
custom.ms: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.timeline.threads
helpviewer_keywords:
- Concurrency Visualizer, Cores View Timeline
ms.assetid: 10f0c666-ac2f-4ac5-9fb5-a88f660ab840
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: de09394bfc071cbe3dd1fedad52d1e5a511b62c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882900"
---
# <a name="cores-view-timeline"></a>Escala de tiempo de la vista Núcleos
Cada fila de la escala de tiempo representa un núcleo de procesador lógico del sistema para el que se genera el perfil. Para cada fila, el eje horizontal muestra qué subproceso se estaba ejecutando en un núcleo lógico en un momento dado. Puede desplazar el puntero sobre un color de interés en una escala de tiempo para devolver información que identifica el subproceso. Para facilitar la identificación del subproceso, la leyenda en la parte inferior de la ventana muestra qué representa cada color. Utilice la herramienta Zoom para acercar y alejar; para ello, haga clic y arrastre o presione la tecla Ctrl y mueva la rueda del mouse. La coherencia de zoom se mantiene al cambiar entre la vista de núcleos y subprocesos.

## <a name="see-also"></a>Consulte también
- [Vista de núcleos](../profiling/cores-view.md)
- [Control de zoom (vista Subprocesos)](../profiling/zoom-control-threads-view.md)