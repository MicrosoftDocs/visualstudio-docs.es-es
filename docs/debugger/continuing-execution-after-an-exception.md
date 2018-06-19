---
title: Continuar la ejecución después de una excepción | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b26fe427ba83eea9e989e492fde89ade498a114
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31466184"
---
# <a name="continuing-execution-after-an-exception"></a>Continuar la ejecución después de una excepción
Cuando el depurador interrumpe la ejecución debido a una excepción, verá el **aplicación auxiliar de excepciones**, de forma predeterminada. Si ha desactivado la **auxiliar de excepciones** en el **opciones** cuadro de diálogo, verá la **Asistente de excepciones** (C# o Visual Basic) o **(excepción)**  cuadro de diálogo) (C++).  
  
 Cuando el **aplicación auxiliar de excepciones** aparece, puede intentar corregir el problema que provocó la excepción.
  
## <a name="managed-and-native-code"></a>Código administrado y nativo  
 En el código administrado y nativo, puede continuar la ejecución en el mismo subproceso después de una excepción no controlada. El **aplicación auxiliar de excepciones** se desenreda la pila de llamadas al punto donde se produjo la excepción.
  
## <a name="mixed-code"></a>Código mixto  
 Si se produce una excepción no controlada durante la depuración de código mixto nativo y administrado, las restricciones de sistema operativo impedirán que se desenrede la pila de llamadas. Si intenta rebobinar la pila de llamadas mediante el menú contextual, aparecerá un mensaje de error que indica que el depurador no puede desenredar la pila de llamadas si se ha producido una excepción no controlada durante la depuración de código mixto.  
  
## <a name="see-also"></a>Vea también  
 [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)