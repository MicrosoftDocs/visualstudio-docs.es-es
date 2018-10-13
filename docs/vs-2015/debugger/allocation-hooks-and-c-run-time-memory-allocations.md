---
title: Enlaces de asignación y asignaciones de memoria en tiempo de ejecución de C | Microsoft Docs
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
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22856782fb8d0ad92a19f03c7c3a474763310a60
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273720"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Enlaces de asignación y asignaciones de memoria en tiempo de ejecución de C
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una restricción muy importante acerca de las funciones de enlace de asignación consiste en que éstas deben omitir explícitamente los bloques `_CRT_BLOCK` (las asignaciones de memoria realizadas internamente por las funciones de la biblioteca en tiempo de ejecución de C) si realizan alguna llamada a las funciones de la biblioteca en tiempo de ejecución de C que asigne memoria interna. Los bloques `_CRT_BLOCK` se pueden omitir si se incluye código como el siguiente al inicio de la función de enlace de asignación:  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Si la función de enlace de asignación no omite los bloques `_CRT_BLOCK`, entonces cualquier función de la biblioteca en tiempo de ejecución de C a la que se llame en el enlace puede hacer que el programa quede atrapado en un bucle sin fin. Por ejemplo, `printf` realiza una asignación interna. Si el código del enlace llama `printf`, la asignación resultante hará que el enlace que se llame de nuevo, que llamará a **printf** nuevo, y así sucesivamente hasta que se desborde la pila. Si necesita informar de las operaciones de asignación de `_CRT_BLOCK`, una forma de evitar esta restricción consiste en utilizar funciones de la API de Windows, en vez de funciones en tiempo de ejecución de C, para operaciones de formato y salida. Como las API de Windows no utilizan el montón de la biblioteca en tiempo de ejecución de C, no bloquearán el enlace de asignación en un bucle sin fin.  
  
 Si examina los archivos de origen de la biblioteca en tiempo de ejecución, verá que la asignación predeterminada de la función de enlace, **CrtDefaultAllocHook** (que simplemente devuelve **TRUE**), se encuentra en un archivo independiente de su propia DBGHOOK. C. Si desea que el enlace de asignación a llamarse incluso para las asignaciones realizadas por el código de inicio de tiempo de ejecución que se ejecuta antes de que su aplicación **principal** función, puede reemplazar esta función predeterminada con uno propio, en lugar de uso de [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d).  
  
## <a name="see-also"></a>Vea también  
 [Función de enlace de depuración](../debugger/debug-hook-function-writing.md)   
 [Ejemplo crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)



