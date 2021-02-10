---
title: Creación de funciones de enlace de depuración | Microsoft Docs
description: Obtenga información sobre varias funciones de enlace de depuración personalizadas que puede escribir y que le permitirán insertar su código en algunos puntos predefinidos dentro del procesamiento normal del depurador.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 76727da1ed057902d8f757594f5ed2e07bcf3cea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857550"
---
# <a name="debug-hook-function-writing"></a>Creación de funciones de enlace de depuración
Esta sección describe varias funciones de enlace de depuración personalizadas que puede escribir y que le permitirán insertar el código que desee en algunos puntos predefinidos dentro del procesamiento normal del depurador.

## <a name="in-this-section"></a>En esta sección
 [Funciones de enlace con los bloques de tipo cliente](../debugger/client-block-hook-functions.md) Proporciona instrucciones y un prototipo para escribir funciones que validan el contenido de los datos almacenados en bloques _CLIENT_BLOCK o informan de él.

 [Funciones de enlace de asignación](../debugger/allocation-hook-functions.md) Define una función de enlace de asignación, explora sus diferentes usos, señala las restricciones y proporciona un prototipo.

 [Enlaces de asignación y asignaciones de memoria en tiempo de ejecución de C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) Describe la restricción de las funciones de enlace de asignación que consiste en omitir explícitamente los bloques `_CRT_BLOCK` si realizan alguna llamada a funciones de la biblioteca en tiempo de ejecución de C que asignan memoria interna. Este tema trata también las consecuencias que se producen si la función de enlace de asignación no omite los bloques `_CRT_BLOCK` (con ejemplos) y cómo cambiar la función de enlace de asignación predeterminada, **CrtDefaultAllocHook**.

 [Funciones de enlace de informe](../debugger/report-hook-functions.md) Analiza `_CrtSetReportHook`, que se puede usar para filtrar informes para centrarse en determinados tipos de asignaciones. Este tema también proporciona un prototipo.

## <a name="related-sections"></a>Secciones relacionadas

- [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md) Proporciona vínculos a técnicas de depuración para la biblioteca en tiempo de ejecución de C, como: uso de la Biblioteca de depuración de CRT, macros para informes, diferencias entre `malloc` y `_malloc_dbg`, creación de funciones de enlace de depuración, y el montón de depuración de CRT.