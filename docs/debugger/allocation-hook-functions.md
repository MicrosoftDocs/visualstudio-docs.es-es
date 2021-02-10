---
title: Funciones de enlace de asignación | Microsoft Docs
description: Obtenga información sobre cómo usar las funciones de enlace de asignación, las cuales se instalan mediante _CrtSetAllocHook, para realizar la depuración en tiempo de ejecución de C (CRT) en Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c032ca57e5a046a9f2dd2295226263ffe20f99e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858012"
---
# <a name="allocation-hook-functions"></a>Funciones de enlace de asignación
Una función de enlace de asignación, instalada mediante [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), recibe una llamada cada vez que se asigna, reasigna o libera memoria. Puede usar este tipo de enlace para muchos propósitos diferentes. Por ejemplo, puede usarlo para probar el modo en que una aplicación controla las situaciones de memoria insuficiente, como examinar pautas de asignación o registrar información de asignación para análisis posteriores.

> [!NOTE]
> Tenga en cuenta la restricción acerca del uso de funciones de la biblioteca en tiempo de ejecución de C en una función de enlace de asignación, descrita en [Enlaces de asignación y asignaciones de memoria en tiempo de ejecución de C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).

 Una función de enlace de asignación debería tener un prototipo como este:

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

 Cuando la biblioteca en tiempo de ejecución llama a la función de enlace, el argumento *nAllocType* indica qué operación de asignación se va a realizar ( **_HOOK_ALLOC**, **_HOOK_REALLOC**, o **_HOOK_FREE**). En una operación de liberación o de reasignación, `pvData` tiene un puntero al artículo de usuario del bloque que se va a liberar. Pero en el caso de una asignación, este puntero es nulo porque la asignación no se ha producido. Los argumentos que quedan contienen el tamaño de la asignación, su tipo de bloque, el número de solicitud secuencial asociado con él, así como un puntero al nombre del archivo. Si está disponible, los argumentos también incluyen el número de línea en el que se realizó la asignación. Después de que la función de enlace realiza las operaciones especificadas por su autor, debe devolver **TRUE** para indicar que la operación de asignación puede continuar, o bien **FALSE**, que indica que la operación ha resultado errónea. Un simple enlace de este tipo podría comprobar la cantidad de memoria asignada hasta entonces y devolver **FALSE** si esa cantidad supera un pequeño límite. La aplicación experimentaría entonces el tipo de errores de asignación que ocurrirían normalmente sólo cuando la memoria disponible fuera muy escasa. Mediante enlaces más complejos, se podrían registrar pautas de asignación, analizar el uso de la memoria o informar de situaciones específicas.

## <a name="see-also"></a>Vea también

- [Enlaces de asignación y asignaciones de memoria en tiempo de ejecución de C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [Creación de funciones de enlace de depuración](../debugger/debug-hook-function-writing.md)