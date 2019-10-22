---
title: Funciones de enlace de asignación | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 81135546ffa208a4efb96569cd7968dfe560cdf9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65702521"
---
# <a name="allocation-hook-functions"></a>Funciones de enlace de asignación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una función de enlace de asignación, instalada mediante [_CrtSetAllocHook](https://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d), se llama cada vez que se asigna, reasigna o libera memoria. Este tipo de enlace se puede utilizar para muchos propósitos diferentes. Utilícelo para probar, por ejemplo, el modo en que una aplicación trata las situaciones de memoria insuficiente, para examinar pautas de asignación o para guardar información de asignación para análisis posteriores.  
  
> [!NOTE]
> Tenga en cuenta la restricción acerca del uso de funciones de la biblioteca en tiempo de ejecución de C en una función de enlace de asignación, descrita en [Enlaces de asignación y asignaciones de memoria en tiempo de ejecución de C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Una función de enlace de asignación debería tener un prototipo como el siguiente:  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 El puntero que se pasa a [_CrtSetAllocHook](https://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d) es del tipo **_CRT_ALLOC_HOOK**, según se define en CRTDBG.H:  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Cuando llama a la biblioteca en tiempo de ejecución, el enlace de la *nAllocType* argumento indica qué asignación operación está a punto de realizarse (**_HOOK_ALLOC**, **_HOOK_REALLOC**, o **_HOOK_FREE**). En caso de una liberación o reasignación, `pvData` contiene un puntero al tema de usuario del bloque que se va a liberar. Sin embargo, en el caso de una asignación, este puntero es null, ya que la asignación no se ha producido aún. Los restantes argumentos contienen el tamaño de la asignación, su tipo de bloque, el número de solicitud secuencial asociado con él, así como un puntero al nombre del archivo y número de línea donde se realizó la asignación, si se dispone de él. Después de que la función de enlace realiza las operaciones especificadas por su autor, debe devolver **TRUE** para indicar que la operación de asignación puede continuar, o bien **FALSE**, que indica que la operación ha resultado errónea. Un simple enlace de este tipo podría comprobar la cantidad de memoria asignada hasta entonces y devolver **FALSE** si esa cantidad supera un pequeño límite. La aplicación experimentaría entonces el tipo de errores de asignación que ocurrirían normalmente sólo cuando la memoria disponible fuera muy escasa. Mediante enlaces más complejos, se podrían registrar pautas de asignación, analizar el uso de la memoria o informar de situaciones específicas.  
  
## <a name="see-also"></a>Vea también  
 [Enlaces de asignación y asignaciones de memoria en tiempo de ejecución de C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Creación de funciones de enlace de depuración](../debugger/debug-hook-function-writing.md)   
 [Ejemplo crt_dbg2](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
