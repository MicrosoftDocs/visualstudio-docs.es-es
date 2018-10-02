---
title: Función de enlace de depuración | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5761b0a32e7739a5611f2d3d07183f0c529fc60c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582992"
---
# <a name="debug-hook-function-writing"></a>Creación de funciones de enlace de depuración
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [creación de funciones de enlace de depuración](https://docs.microsoft.com/visualstudio/debugger/debug-hook-function-writing).  
  
Esta sección describe varias funciones de enlace de depuración personalizadas que puede escribir y que le permitirán insertar el código que desee en algunos puntos predefinidos dentro del procesamiento normal del depurador.  
  
## <a name="in-this-section"></a>En esta sección  
 [Funciones de enlace con los bloques de tipo cliente](../debugger/client-block-hook-functions.md)  
 Proporciona orientación y un prototipo para escribir funciones que validan o informan del contenido de los datos almacenados en bloques _CLIENT_BLOCK.  
  
 [Funciones de enlace de asignación](../debugger/allocation-hook-functions.md)  
 Define una función de asociación de asignación, explora sus diferentes usos, señala sus restricciones y proporciona un prototipo.  
  
 [Enlaces de asignación y asignaciones de memoria CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 Describe la restricción de las funciones de enlace de asignación consistente en omitir explícitamente los bloques `_CRT_BLOCK` si realizan alguna llamada a funciones de la biblioteca en tiempo de ejecución de C que asignan memoria interna. Este tema también enumeran las consecuencias si el enlace de asignación no omite `_CRT_BLOCK` bloques (con ejemplos) y cómo cambiar la asignación predeterminada de la función, de enlace **CrtDefaultAllocHook**.  
  
 [Funciones de enlace de informe](../debugger/report-hook-functions.md)  
 Analiza `_CrtSetReportHook`, que se puede utilizar para filtrar informes de modo que éstos se concentren en determinados tipos de asignaciones. Este tema también proporciona un prototipo.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md)  
 Proporciona vínculos a técnicas de depuración para la biblioteca en tiempo de ejecución de C, tales como: uso de la Biblioteca de depuración de CRT, macros para informes, diferencias entre `malloc` y `_malloc_dbg`, creación de funciones de enlace de depuración, y la pila de depuración de CRT.



