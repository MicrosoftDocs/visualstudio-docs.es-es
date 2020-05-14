---
title: Versiones de depuración de las funciones de asignación del montón | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- debugging [CRT], heap allocation functions
- debugging memory leaks, CRT debug library functions
- malloc function
- memory leaks, CRT debug library functions
- heap allocation, debug
- _malloc_dbg function
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0fde776e9f2bd48aca92c7ba6d7f1fe1e23f01a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738375"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Versiones de depuración de las funciones de asignación del montón
La biblioteca en tiempo de ejecución de C contiene versiones de depuración especiales de las funciones de asignación de memoria en el montón. Estas funciones tienen los mismos nombres que las versiones de lanzamiento pero con _dbg agregado al final. Este tema describe las diferencias entre la versión de lanzamiento de una función CRT y la versión _dbg usando `malloc` y `_malloc_dbg` como ejemplos.

 Cuando se define [_DEBUG](/cpp/c-runtime-library/debug), CRT asigna todas las llamadas a [malloc](/cpp/c-runtime-library/reference/malloc) a [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). Por lo tanto, no es necesario volver a escribir el código utilizando `_malloc_dbg` en vez de `malloc` para aprovechar sus beneficios mientras se depura.

 No obstante, se puede llamar a `_malloc_dbg` explícitamente. Llamar explícitamente a `_malloc_dbg` presenta algunas ventajas adicionales:

- Seguimiento de asignaciones de tipos `_CLIENT_BLOCK`.

- Almacenamiento del archivo de código fuente y número de línea donde se produjo la solicitud de asignación de memoria.

  Si no quiere convertir las llamadas a `malloc` en `_malloc_dbg`, puede obtener la información del archivo de código fuente si define [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), lo que hace que el preprocesador asigne directamente todas las llamadas a `malloc` a `_malloc_dbg`, en vez de depender de un contenedor en torno a `malloc`.

  Para realizar un seguimiento de los tipos de asignaciones que existen en los bloques cliente de forma independiente, se debe llamar directamente a `_malloc_dbg` y asignar a `blockType` el parámetro `_CLIENT_BLOCK`.

  Cuando _DEBUG no está definido, las llamadas a `malloc` no se modifican, las llamadas a `_malloc_dbg` se resuelven en `malloc`, la definición de [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc) se omite y no se facilita la información del archivo de código fuente correspondiente a la solicitud de asignación. Como `malloc` no utiliza un parámetro de tipo bloque, las solicitudes para tipos `_CLIENT_BLOCK` se tratan como asignaciones estándar.

## <a name="see-also"></a>Vea también

- [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md)