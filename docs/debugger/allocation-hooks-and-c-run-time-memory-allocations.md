---
title: Enlaces de asignación y asignaciones de memoria en tiempo de ejecución de C | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3f20c71ad12a64e6d8d14b91310c870477cfc6d4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53899631"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Enlaces de asignación y asignaciones de memoria en tiempo de ejecución de C
Una restricción muy importante en las funciones de enlace de asignación es que deben omitir explícitamente `_CRT_BLOCK` bloques. Estos bloques son las asignaciones de memoria realizadas internamente por las funciones de biblioteca en tiempo de ejecución de C si realizan alguna llamada a funciones de biblioteca en tiempo de ejecución de C que asignan memoria interna. Puede hacer caso omiso `_CRT_BLOCK` bloques incluyendo el código siguiente al principio de la asignación de función de enlace:  
  
```cpp
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Si el enlace de asignación no omite `_CRT_BLOCK` se bloquea, entonces cualquier función de biblioteca en tiempo de ejecución de C llamada en el enlace puede hacer que el programa en un bucle infinito. Por ejemplo, `printf` realiza una asignación interna. Si el código del enlace llama a `printf`, la asignación resultante hará que se vuelva a llamar al enlace, que llamará de nuevo a **printf**, etc. hasta que se desborde la pila. Si necesita informar de las operaciones de asignación de `_CRT_BLOCK`, una forma de evitar esta restricción consiste en utilizar funciones de la API de Windows, en vez de funciones en tiempo de ejecución de C, para operaciones de formato y salida. Dado que las API de Windows no usan el montón de la biblioteca en tiempo de ejecución de C, no interceptar el enlace de asignación en un bucle infinito.  
  
 Si examina los archivos de código fuente de la biblioteca en tiempo de ejecución, verá que la función de enlace de asignación predeterminada, **CrtDefaultAllocHook** (que simplemente devuelve **TRUE**), se encuentra en un archivo independiente, DBGHOOK.C. Si desea llamar al enlace de asignación incluso en las asignaciones realizadas por el código de inicio en tiempo de ejecución que se ejecuta antes que la función **main** de la aplicación, puede reemplazar esta función predeterminada por una propia en lugar de usar [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).  
  
## <a name="see-also"></a>Vea también  
 [Creación de funciones de enlace de depuración](../debugger/debug-hook-function-writing.md)   
