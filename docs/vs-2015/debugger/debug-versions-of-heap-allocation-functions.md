---
title: Versiones de funciones de asignación del montón de depuración | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a6bf3976138f385f103c6d046e2b71133a8795d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875011"
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



