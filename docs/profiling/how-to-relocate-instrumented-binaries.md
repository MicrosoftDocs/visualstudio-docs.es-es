---
title: Cambiar la ubicación de binarios instrumentados | Microsoft Docs
description: Obtenga más información sobre cómo se insertan análisis en el binario para medir el rendimiento de la aplicación durante la instrumentación.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7c63a1ce67095696d590670327a1a33e2471c145
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907084"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Procedimiento Reubicar archivos binarios instrumentados

Durante la instrumentación, se insertan análisis en el binario para medir el rendimiento de la aplicación. Si opta por reubicar el binario instrumentado, se instrumenta una copia del binario original y se coloca en la ubicación especificada. Esta opción es útil si no desea que el generador de perfiles cambie el nombre del binario original. Si el binario no se reubica, se sobrescribe su versión original.

## <a name="to-relocate-instrumented-binary"></a>Para reubicar un binario instrumentado

1. En el **Explorador de rendimiento**, haga clic con el botón derecho del mouse en la sesión de rendimiento y, después, haga clic en **Propiedades**.

2. En **Páginas de propiedades**, haga clic en las propiedades de **Binario** .

3. Active la casilla **Reubicar archivos binarios instrumentados** .

4. Especifique la ubicación del binario instrumentado.

## <a name="see-also"></a>Vea también

[Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)
[VSInstr](../profiling/vsinstr.md)
