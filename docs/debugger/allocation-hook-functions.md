---
title: "Funciones de enlace de asignación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.hooks
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
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4fe5ac5ec207bb52884c097d1562a85a3414ba7d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="allocation-hook-functions"></a>Funciones de enlace de asignación
Una función de enlace de asignación, instalada mediante [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), se llama cada vez que se asigna, reasigna o libera memoria. Este tipo de enlace se puede utilizar para muchos propósitos diferentes. Utilícelo para probar, por ejemplo, el modo en que una aplicación trata las situaciones de memoria insuficiente, para examinar pautas de asignación o para guardar información de asignación para análisis posteriores.  
  
> [!NOTE]
>  Tenga en cuenta la restricción acerca del uso de funciones de la biblioteca de tiempo de ejecución de C en una función de enlace de asignación, se describe en [enlaces de asignación y asignaciones de memoria de tiempo de ejecución de C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Una función de enlace de asignación debería tener un prototipo como el siguiente:  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 El puntero que se pasa a [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) es de tipo **_CRT_ALLOC_HOOK**, tal como se define en CRTDBG. H:  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Cuando la biblioteca en tiempo de ejecución llama al enlace, el *nAllocType* argumento indica qué asignación está a punto de realizar operación (**_HOOK_ALLOC**, **_HOOK_REALLOC**, o **_HOOK_FREE**). En caso de una liberación o reasignación, `pvData` contiene un puntero al tema de usuario del bloque que se va a liberar. Sin embargo, en el caso de una asignación, este puntero es null, ya que la asignación no se ha producido aún. Los restantes argumentos contienen el tamaño de la asignación, su tipo de bloque, el número de solicitud secuencial asociado con él, así como un puntero al nombre del archivo y número de línea donde se realizó la asignación, si se dispone de él. Después de la función de enlace realiza el análisis y otras tareas de su autor, debe devolver **TRUE**, que indica que la operación de asignación puede continuar, o **FALSE**, lo que indica que el operación ha resultado errónea. Un simple enlace de este tipo podría comprobar la cantidad de memoria asignada hasta entonces y devolver **FALSE** si esa cantidad supera un pequeño límite. La aplicación experimentaría entonces el tipo de errores de asignación que ocurrirían normalmente sólo cuando la memoria disponible fuera muy escasa. Mediante enlaces más complejos, se podrían registrar pautas de asignación, analizar el uso de la memoria o informar de situaciones específicas.  
  
## <a name="see-also"></a>Vea también  
 [Enlaces de asignación y asignaciones de memoria de tiempo de ejecución de C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Creación de funciones de enlace de depuración](../debugger/debug-hook-function-writing.md)   
