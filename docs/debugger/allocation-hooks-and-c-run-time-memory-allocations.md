---
title: "Enlaces de asignación y asignaciones de memoria de tiempo de ejecución de C | Documentos de Microsoft"
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
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b383deae8262f9fb53cf4494ef8ce8d65f5ce02
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2017
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Enlaces de asignación y asignaciones de memoria en tiempo de ejecución de C
Una restricción muy importante acerca de las funciones de enlace de asignación consiste en que éstas deben omitir explícitamente los bloques `_CRT_BLOCK` (las asignaciones de memoria realizadas internamente por las funciones de la biblioteca en tiempo de ejecución de C) si realizan alguna llamada a las funciones de la biblioteca en tiempo de ejecución de C que asigne memoria interna. Los bloques `_CRT_BLOCK` se pueden omitir si se incluye código como el siguiente al inicio de la función de enlace de asignación:  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Si la función de enlace de asignación no omite los bloques `_CRT_BLOCK`, entonces cualquier función de la biblioteca en tiempo de ejecución de C a la que se llame en el enlace puede hacer que el programa quede atrapado en un bucle sin fin. Por ejemplo, `printf` realiza una asignación interna. Si el código del enlace llama `printf`, a continuación, la asignación resultante hará que se llama de nuevo al enlace que se llamará **printf** nuevo, y así sucesivamente hasta que la pila se desborda. Si necesita informar de las operaciones de asignación de `_CRT_BLOCK`, una forma de evitar esta restricción consiste en utilizar funciones de la API de Windows, en vez de funciones en tiempo de ejecución de C, para operaciones de formato y salida. Como las API de Windows no utilizan el montón de la biblioteca en tiempo de ejecución de C, no bloquearán el enlace de asignación en un bucle sin fin.  
  
 Si examina los archivos de origen de la biblioteca en tiempo de ejecución, verá que la asignación predeterminada función de enlace, **CrtDefaultAllocHook** (que simplemente devuelve **TRUE**), se encuentra en un archivo independiente de su propia, DBGHOOK. C. Si desea que el enlace de asignación para llamarlo incluso para las asignaciones realizadas por el código de inicio de tiempo de ejecución que se ejecuta antes de la aplicación **principal** función, puede reemplazar esta función predeterminada con uno de sus propios, en lugar de usar [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).  
  
## <a name="see-also"></a>Vea también  
 [Creación de funciones de enlace de depuración](../debugger/debug-hook-function-writing.md)   
