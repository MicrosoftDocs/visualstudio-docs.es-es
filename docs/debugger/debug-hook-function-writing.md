---
title: "Creación de funciones de enlace de depuración | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.hooks
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
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30d645042908a7ff307017d090c2789b9d40b99a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="debug-hook-function-writing"></a>Creación de funciones de enlace de depuración
Esta sección describe varias funciones de enlace de depuración personalizadas que puede escribir y que le permitirán insertar el código que desee en algunos puntos predefinidos dentro del procesamiento normal del depurador.  
  
## <a name="in-this-section"></a>En esta sección  
 [Funciones de enlace con los bloques de tipo cliente](../debugger/client-block-hook-functions.md)  
 Proporciona orientación y un prototipo para escribir funciones que validan o informan del contenido de los datos almacenados en bloques _CLIENT_BLOCK.  
  
 [Funciones de enlace de asignación](../debugger/allocation-hook-functions.md)  
 Define una función de asociación de asignación, explora sus diferentes usos, señala sus restricciones y proporciona un prototipo.  
  
 [Enlaces de asignación y asignaciones de memoria CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 Describe la restricción de las funciones de enlace de asignación consistente en omitir explícitamente los bloques `_CRT_BLOCK` si realizan alguna llamada a funciones de la biblioteca en tiempo de ejecución de C que asignan memoria interna. Este tema enumeran también las consecuencias si el enlace de asignación no omite los `_CRT_BLOCK` bloques (con ejemplos) y cómo cambiar la asignación predeterminada de la función, de enlace **CrtDefaultAllocHook**.  
  
 [Funciones de enlace de informe](../debugger/report-hook-functions.md)  
 Analiza `_CrtSetReportHook`, que se puede utilizar para filtrar informes de modo que éstos se concentren en determinados tipos de asignaciones. Este tema también proporciona un prototipo.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md)  
 Proporciona vínculos a técnicas de depuración para la biblioteca en tiempo de ejecución de C, tales como: uso de la Biblioteca de depuración de CRT, macros para informes, diferencias entre `malloc` y `_malloc_dbg`, creación de funciones de enlace de depuración, y la pila de depuración de CRT.