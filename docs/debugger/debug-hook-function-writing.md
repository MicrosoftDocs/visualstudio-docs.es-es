---
title: Función de enlace de depuración | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82145d39adc519bfd1324cc36805cea7b97b1664
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628928"
---
# <a name="debug-hook-function-writing"></a>Creación de funciones de enlace de depuración
Esta sección describe varias funciones de enlace de depuración personalizadas que puede escribir y que le permitirán insertar el código que desee en algunos puntos predefinidos dentro del procesamiento normal del depurador.

## <a name="in-this-section"></a>En esta sección
 [Funciones de enlace de bloque cliente](../debugger/client-block-hook-functions.md) proporciona orientación y un prototipo para escribir funciones que validan o informan del contenido de los datos almacenados en bloques _CLIENT_BLOCK.

 [Funciones de enlace de asignación](../debugger/allocation-hook-functions.md) define una función de enlace de asignación, explora sus diferentes usos, señala sus restricciones y proporciona un prototipo.

 [Enlaces de asignación y asignaciones de memoria CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) describe la restricción de las funciones de enlace de asignación de forma explícita omitir `_CRT_BLOCK` se bloquea si realizan alguna llamada a funciones de biblioteca en tiempo de ejecución de C que asignan memoria interna. Este tema trata también las consecuencias que se producen si la función de enlace de asignación no omite los bloques `_CRT_BLOCK` (con ejemplos) y cómo cambiar la función de enlace de asignación predeterminada, **CrtDefaultAllocHook**.

 [Funciones de enlace de informe](../debugger/report-hook-functions.md) explica `_CrtSetReportHook`, que puede utilizar para filtrar informes a centrarse en determinados tipos de asignaciones. Este tema también proporciona un prototipo.

## <a name="related-sections"></a>Secciones relacionadas

- [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md) -vínculos a técnicas de depuración para la biblioteca de tiempo de ejecución de C, incluido el uso de la biblioteca de depuración de CRT, macros para informes, diferencias entre `malloc` y `_malloc_dbg`, escribir funciones de enlace de depuración y la biblioteca CRT montón de depuración.