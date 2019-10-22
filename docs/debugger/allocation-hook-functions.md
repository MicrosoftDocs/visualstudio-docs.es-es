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
ms.openlocfilehash: 406647ae086285df8dfdfc00daf4b62be66e74a2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402694"
---
# <a name="allocation-hook-functions"></a>Funciones de enlace de asignación
Una función de enlace de asignación, instalada mediante [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), se llama cada vez que se asigna, reasigna o libera memoria. Puede usar este tipo de enlace para muchos propósitos diferentes. Para probar cómo una aplicación controla las situaciones de memoria insuficiente, como para examinar pautas de asignación o registrar información de asignación para su análisis posterior.

> [!NOTE]
> Tenga en cuenta la restricción acerca del uso de funciones de la biblioteca en tiempo de ejecución de C en una función de enlace de asignación, descrita en [Enlaces de asignación y asignaciones de memoria en tiempo de ejecución de C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).

 Una función de enlace de asignación debe tener un prototipo similar al ejemplo siguiente:

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

 Cuando llama a la biblioteca en tiempo de ejecución, el enlace de la *nAllocType* argumento indica qué asignación operación está a punto de realizarse (**_HOOK_ALLOC**, **_HOOK_REALLOC**, o **_HOOK_FREE**). En una liberación o reasignación, `pvData` tiene un puntero para el artículo de usuario del bloque que se va a liberar. Sin embargo de asignación, este puntero es null, porque no se ha producido la asignación. Los restantes argumentos contienen el tamaño de la asignación en cuestión, su tipo de bloque, el número de solicitud secuencial asociado con la base de datos y un puntero al nombre de archivo. Si está disponible, los argumentos incluyen también el número de línea en el que se realizó la asignación. Después de que la función de enlace realiza las operaciones especificadas por su autor, debe devolver **TRUE** para indicar que la operación de asignación puede continuar, o bien **FALSE**, que indica que la operación ha resultado errónea. Un simple enlace de este tipo podría comprobar la cantidad de memoria asignada hasta entonces y devolver **FALSE** si esa cantidad supera un pequeño límite. La aplicación experimentaría entonces el tipo de errores de asignación que ocurrirían normalmente sólo cuando la memoria disponible fuera muy escasa. Mediante enlaces más complejos, se podrían registrar pautas de asignación, analizar el uso de la memoria o informar de situaciones específicas.

## <a name="see-also"></a>Vea también

- [Enlaces de asignación y asignaciones de memoria en tiempo de ejecución de C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [Creación de funciones de enlace de depuración](../debugger/debug-hook-function-writing.md)