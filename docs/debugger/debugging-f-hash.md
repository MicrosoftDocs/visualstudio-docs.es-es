---
title: 'Depurar F # | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3a2b2651a8fc7f33ec30edc5d080d6d7e66c17e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="debugging-f"></a>Depurar F#
La depuración de F# es similar a la depuración de cualquier lenguaje administrado, con algunas excepciones:  
  
-   El **automático** ventana no muestra variables de F #.  
  
-   El modo Editar y Continuar no se admite en F#. Es posible editar código de F# durante una sesión de depuración pero se debería evitar. Dado que los cambios de código no se aplican durante la sesión de depuración, si se realizan cambios en el código de F# durante la depuración, el código fuente no se corresponderá con el código objeto de la depuración.  
  
-   El depurador no reconoce expresiones de F#. Para escribir una expresión en una ventana de depurador o un cuadro de diálogo durante la depuración de F#, se debe convertir la expresión en la sintaxis de C#. Al convertir una expresión de F# en C#, no olvide que C# usa == como operador de comparación de igualdad y que F# utiliza =.  
  
## <a name="see-also"></a>Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)
