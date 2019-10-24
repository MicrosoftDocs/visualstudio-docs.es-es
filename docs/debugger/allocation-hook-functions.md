---
title: Funciones de enlace de asignación | Microsoft Docs
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
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f684c6c66448fdab2ee7607a81ff7ed769a5e607
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745820"
---
# <a name="allocation-hook-functions"></a>Funciones de enlace de asignación
Se llama a una función de enlace de asignación, instalada mediante [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), cada vez que se asigna, reasigna o libera memoria. Puede usar este tipo de enlace para muchos fines diferentes. Úselo para probar cómo trata una aplicación las situaciones de memoria insuficiente, como examinar patrones de asignación o registrar información de asignación para su análisis posterior.

> [!NOTE]
> Tenga en cuenta la restricción acerca del uso de funciones de la biblioteca en tiempo de ejecución de C en una función de enlace de asignación, descrita en [Enlaces de asignación y asignaciones de memoria en tiempo de ejecución de C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).

 Una función de enlace de asignación debe tener un prototipo como el ejemplo siguiente:

```cpp
int YourAllocHook(int nAllocType, void *pvData,
        size_t nSize, int nBlockUse, long lRequest,
        const unsigned char * szFileName, int nLine )
```

 El puntero que se pasa a [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) es del tipo **_CRT_ALLOC_HOOK**, según se define en CRTDBG.H:

```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)
    (int, void *, size_t, int, long, const unsigned char *, int);
```

 Cuando la biblioteca en tiempo de ejecución llama al enlace, el argumento *nAllocType* indica qué operación de asignación está a punto de realizarse ( **_HOOK_ALLOC**, **_HOOK_REALLOC**o **_HOOK_FREE**). En una versión gratuita o en una reasignación, `pvData` tiene un puntero al artículo de usuario del bloque que se va a liberar. Sin embargo, para una asignación, este puntero es null, porque la asignación no se ha producido. Los argumentos restantes contienen el tamaño de la asignación en cuestión, su tipo de bloque, el número de solicitud secuencial asociado a él y un puntero al nombre de archivo. Si está disponible, los argumentos también incluyen el número de línea en el que se realizó la asignación. Después de que la función de enlace realiza las operaciones especificadas por su autor, debe devolver **TRUE** para indicar que la operación de asignación puede continuar, o bien **FALSE**, que indica que la operación ha resultado errónea. Un simple enlace de este tipo podría comprobar la cantidad de memoria asignada hasta entonces y devolver **FALSE** si esa cantidad supera un pequeño límite. La aplicación experimentaría entonces el tipo de errores de asignación que ocurrirían normalmente sólo cuando la memoria disponible fuera muy escasa. Mediante enlaces más complejos, se podrían registrar pautas de asignación, analizar el uso de la memoria o informar de situaciones específicas.

## <a name="see-also"></a>Vea también

- [Enlaces de asignación y asignaciones de memoria en tiempo de ejecución de C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [Creación de funciones de enlace de depuración](../debugger/debug-hook-function-writing.md)