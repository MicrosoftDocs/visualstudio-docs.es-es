---
title: Instrucciones Stop en Visual Basic | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 74be447f523713cdef9ee5c52876ee0acf4c25b2
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056148"
---
# <a name="stop-statements-in-visual-basic"></a>Instrucciones Stop en Visual Basic
La instrucción Stop de Visual Basic proporciona una alternativa de programación al establecimiento de un punto de interrupción. Cuando el depurador encuentra una instrucción Stop, interrumpe la ejecución del programa (entra en el modo de interrupción). Los programadores de C# pueden lograr el mismo efecto utilizando una llamada a System.Diagnostics.Debugger.Break.  
  
 Para establecer o quitar una instrucción Stop se edita el código fuente. No se pueden establecer ni borrar instrucciones Stop mediante comandos del depurador, como se hace con un punto de interrupción.  
  
 A diferencia de una instrucción End, la instrucción Stop no restablece variables ni regresa al modo de diseño. Para continuar la ejecución de la aplicación, puede elegir Continuar en el menú Depurar.  
  
 Cuando se ejecuta una aplicación de Visual Basic fuera del depurador, una instrucción Stop iniciará el depurador si está habilitada la depuración Just-In-Time. Si no está habilitada la depuración Just-In-Time, la instrucción Stop se comporta como si fuera una instrucción End y termina la ejecución. No se produce ningún evento QueryUnload o Unload, de manera que es necesario quitar todas las instrucciones Stop de la versión de lanzamiento en la aplicación de Visual Basic. Para obtener más información, consulte [depuración Just](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Para no tener que quitar instrucciones Stop, puede utilizar la compilación condicional:  
  
```cpp
#If DEBUG Then  
   Stop  
#Else  
   ' Don't stop  
#End If  
```  
  
 Otra alternativa consiste en utilizar una instrucción Assert en lugar de la instrucción Stop. Una instrucción Debug.Assert sólo interrumpe la ejecución si no se cumple una condición especificada, y se quita automáticamente cuando se compila una versión de lanzamiento. Para obtener más información, consulte [aserciones en el código administrado](../debugger/assertions-in-managed-code.md). Si desea una instrucción Assert que interrumpa siempre la ejecución en la versión de depuración, puede hacer lo siguiente:  
  
```csharp
Debug.Assert(false)  
```  
  
 Otra alternativa más consiste en utilizar el método Debug.Fail:  
  
```csharp
Debug.Fail("a clever output string goes here")  
```  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Tipos de proyectos de C#, F# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)
