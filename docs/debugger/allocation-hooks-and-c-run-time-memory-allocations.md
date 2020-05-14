---
title: Enlaces de asignación y asignaciones de memoria en tiempo de ejecución de C | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79e55ec521de098a7ae0339c4460502dde3d482d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745797"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Enlaces de asignación y asignaciones de memoria en tiempo de ejecución de C
Una restricción muy importante en las funciones de enlace de asignación es que deben omitir explícitamente los bloques `_CRT_BLOCK`. Estos bloques son las asignaciones de memoria realizadas internamente por las funciones de la biblioteca en tiempo de ejecución de C si realizan alguna llamada a dichas funciones que asignan memoria interna. Pueden omitirse los bloques `_CRT_BLOCK` si se incluye código como el siguiente al inicio de la función de enlace de asignación:

```cpp
if ( nBlockUse == _CRT_BLOCK )
    return( TRUE );
```

Si la función de enlace de asignación no omite los bloques `_CRT_BLOCK`, cualquier función de la biblioteca en tiempo de ejecución de C a la que se llame en el enlace puede hacer que el programa quede atrapado en un bucle sin fin. Por ejemplo, `printf` realiza una asignación interna. Si el código del enlace llama a `printf`, la asignación resultante hará que se vuelva a llamar al enlace, que llamará de nuevo a **printf**, etc. hasta que se desborde la pila. Si necesita informar de las operaciones de asignación de `_CRT_BLOCK`, una forma de evitar esta restricción consiste en utilizar funciones de la API de Windows, en vez de funciones en tiempo de ejecución de C, para operaciones de formato y salida. Como las API de Windows no utilizan el montón de la biblioteca en tiempo de ejecución de C, no bloquearán el enlace de asignación en un bucle sin fin.

Si examina los archivos de código fuente de la biblioteca en tiempo de ejecución, verá que la función de enlace de asignación predeterminada, **CrtDefaultAllocHook** (que simplemente devuelve **TRUE**), se encuentra en un archivo independiente, DBGHOOK.C. Si desea llamar al enlace de asignación incluso en las asignaciones realizadas por el código de inicio en tiempo de ejecución que se ejecuta antes que la función **main** de la aplicación, puede reemplazar esta función predeterminada por una propia en lugar de usar [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).

## <a name="see-also"></a>Vea también
- [Creación de funciones de enlace de depuración](../debugger/debug-hook-function-writing.md)
