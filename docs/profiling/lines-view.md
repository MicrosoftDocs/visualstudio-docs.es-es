---
title: Vista Líneas | Microsoft Docs
description: Obtenga información sobre cómo la vista Líneas está disponible solo para los datos del generador de perfiles recopilados mediante el método de muestreo.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f99431faaa7bfc77bd7cd9a14be03f7cc2238127
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917833"
---
# <a name="lines-view"></a>Vista Líneas
La vista Líneas está disponible solo para los datos del generador de perfiles recopilados mediante el método de muestreo. La vista no está disponible para los datos recopilados mediante instrumentación.

 Para los datos de perfil de muestreo, la vista Líneas identifica las instrucciones de una función que se estaba ejecutando directamente cuando se recopiló la muestra. Para los datos de memoria. NET, la vista Líneas identifica las instrucciones que asignan memoria.

 En un archivo de origen, una instrucción puede abarcar más de una línea y una sola línea puede incluir más de una instrucción.

 Una instrucción se identifica mediante lo siguiente:

- El archivo de código fuente que contiene la instrucción de la función.

- La función que contiene la instrucción.

- La línea de origen donde se inicia la instrucción.

- El carácter en la línea de origen donde se inicia la instrucción.

- La línea de origen donde finaliza la instrucción.

- El carácter en la línea de origen donde finaliza la instrucción.

## <a name="see-also"></a>Consulte también
- [Vista Líneas](../profiling/lines-view-sampling-data.md)
- [Vista Líneas: muestreo](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Vista Líneas](../profiling/lines-view-contention-data.md)
