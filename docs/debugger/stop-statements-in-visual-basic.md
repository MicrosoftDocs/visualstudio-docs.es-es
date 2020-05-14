---
title: Instrucciones Stop en Visual Basic | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f9ab4ef453a921371ab7ef4f272cd0e38f4108a
ms.sourcegitcommit: 4d2620bee4688fb881e09a07ea4a264b99f0743e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322532"
---
# <a name="stop-statements-in-visual-basic"></a>Instrucciones Stop en Visual Basic

La instrucción Stop de Visual Basic proporciona una alternativa de programación al establecimiento de un punto de interrupción. Cuando el depurador encuentra una instrucción Stop, interrumpe la ejecución del programa (entra en el modo de interrupción). Los programadores de C# pueden lograr el mismo efecto mediante una llamada a <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>.

Para establecer o quitar una instrucción Stop se edita el código fuente. No se pueden establecer ni borrar instrucciones Stop mediante comandos del depurador, como se hace con un punto de interrupción.

A diferencia de una instrucción End, la instrucción Stop no restablece variables ni regresa al modo de diseño. Para continuar la ejecución de la aplicación, puede elegir Continuar en el menú Depurar.

Cuando se ejecuta una aplicación de Visual Basic fuera del depurador, una instrucción Stop inicia el depurador si está habilitada la depuración Just-In-Time. Si no está habilitada la depuración Just-In-Time, la instrucción Stop se comporta como si fuera una instrucción End y finaliza la ejecución. No se produce ningún evento QueryUnload o Unload, de manera que es necesario quitar todas las instrucciones Stop de la versión de lanzamiento en la aplicación de Visual Basic. Para obtener más información, vea [Depuración Just-In-Time](just-in-time-debugging-in-visual-studio.md).

 Para no tener que quitar instrucciones Stop, puede utilizar la compilación condicional:

```vb
#If DEBUG Then
   Stop
#Else
   ' Don't stop
#End If
```

Otra alternativa consiste en usar una instrucción <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> en lugar de la instrucción Stop. Una instrucción <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> interrumpe la ejecución solo cuando no se cumple una condición especificada. Las instrucciones <xref:System.Diagnostics.Debug.Assert%2A> se quitan de forma automática al compilar una versión de lanzamiento. Para obtener más información, vea [Aserciones en el código administrado](assertions-in-managed-code.md). Si quiere una instrucción <xref:System.Diagnostics.Debug.Assert%2A> que interrumpa siempre la ejecución en la versión de depuración, puede hacer lo siguiente:

```csharp
Debug.Assert(false);
```

```vb
Debug.Assert(False)
```

Otra alternativa consiste en usar el método <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>:

```csharp
Debug.Fail("a clever output string goes here");
```

```vb
Debug.Fail("a clever output string goes here")
```

## <a name="see-also"></a>Vea también

- [Seguridad del depurador](debugger-security.md)
- [Tipos de proyectos de C#, F# y Visual Basic](debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Depurar código administrado](debugging-managed-code.md)
