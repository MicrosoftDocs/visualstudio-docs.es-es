---
title: Versiones de funciones de asignación del montón de depuración | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26d81d7b2aaa3bd8661e0da4b1590e9c8c0d0191
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988634"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Versiones de depuración de las funciones de asignación del montón
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La biblioteca en tiempo de ejecución de C contiene versiones de depuración especiales de las funciones de asignación de memoria en el montón. Estas funciones tienen los mismos nombres que las versiones de lanzamiento pero con _dbg agregado al final. Este tema describe las diferencias entre la versión de lanzamiento de una función CRT y la versión _dbg usando `malloc` y `_malloc_dbg` como ejemplos.  
  
 Cuando [_DEBUG](http://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) está definido, CRT asigna todas [malloc](http://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) las llamadas a [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb). Por lo tanto, no es necesario volver a escribir el código utilizando `_malloc_dbg` en vez de `malloc` para aprovechar sus beneficios mientras se depura.  
  
 No obstante, se puede llamar a `_malloc_dbg` explícitamente. Llamar explícitamente a `_malloc_dbg` presenta algunas ventajas adicionales:  
  
- Seguimiento de asignaciones de tipos `_CLIENT_BLOCK`.  
  
- Almacenamiento del archivo de código fuente y número de línea donde se produjo la solicitud de asignación de memoria.  
  
  Si no desea convertir su `malloc` las llamadas a `_malloc_dbg`, puede obtener la información del archivo de código fuente definiendo [_CRTDBG_MAP_ALLOC](http://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b), que hace que el preprocesador asigne directamente todas las llamadas a `malloc` a `_malloc_dbg` en lugar de confiar en un contenedor alrededor de `malloc`.  
  
  Para realizar un seguimiento de los tipos de asignaciones que existen en los bloques cliente de forma independiente, se debe llamar directamente a `_malloc_dbg` y asignar a `blockType` el parámetro `_CLIENT_BLOCK`.  
  
  Si no está definido _DEBUG, las llamadas a `malloc` no se ven afectados, las llamadas a `_malloc_dbg` se resuelven en `malloc`, la definición de [_CRTDBG_MAP_ALLOC](http://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b) se omite y del origen de información de archivo correspondiente a la no se proporcionó la solicitud de asignación. Como `malloc` no utiliza un parámetro de tipo bloque, las solicitudes para tipos `_CLIENT_BLOCK` se tratan como asignaciones estándar.  
  
## <a name="see-also"></a>Vea también  
 [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md)
