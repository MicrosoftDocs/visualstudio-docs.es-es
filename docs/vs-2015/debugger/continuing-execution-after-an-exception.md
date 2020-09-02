---
title: Continuación de la ejecución después de una excepción | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
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
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6ae74c51f0f738bc596fbe5c789011630927707c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702265"
---
# <a name="continuing-execution-after-an-exception"></a>Continuar la ejecución después de una excepción
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando el depurador interrumpe la ejecución debido a una excepción, aparece un cuadro de diálogo. Para Visual Basic o C#, verá el cuadro de diálogo [Asistente de excepciones](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb) de forma predeterminada. En el caso de C++, verá el cuadro de diálogo **excepción** anterior. Si usa Visual Basic o C# pero ha deshabilitado el **Asistente de excepciones** en el cuadro de diálogo **Opciones** , verá el cuadro de diálogo **excepción** .  
  
 Cuando aparezca el cuadro de diálogo **Asistente de excepciones** o **excepción** , puede intentar solucionar el problema que produjo la excepción.  
  
## <a name="managed-code"></a>Código administrado  
 En el código administrado, puede continuar la ejecución en el mismo subproceso después de que se haya producido una excepción no controlada. El **Asistente de excepciones** desenreda la pila de llamadas hasta el punto en que se produjo la excepción.  
  
## <a name="native-code"></a>Código nativo  
 En C/C++ nativo, tiene dos opciones:  
  
- Puede hacer clic en **interrumpir** e intentar corregir el problema. Mientras está en modo de interrupción, puede desenredar la pila de llamadas haciendo clic con el botón secundario en un marco de la ventana **pila de llamadas** y seleccionando **desenredar hasta este marco** en el menú contextual. Cuando siga depurando, aparecerá de nuevo el cuadro de diálogo de **excepción** si no ha corregido el problema. De lo contrario, el cuadro de diálogo **excepción** no volverá a aparecer.  
  
- Puede hacer clic en **continuar** para continuar con la ejecución sin intentar solucionar el problema. Vuelve a aparecer el cuadro de diálogo **excepción** .  
  
## <a name="mixed-code"></a>Código mixto  
 Si se produce una excepción no controlada durante la depuración de código mixto nativo y administrado, las restricciones de sistema operativo impedirán que se desenrede la pila de llamadas. Si intenta rebobinar la pila de llamadas mediante el menú contextual, aparecerá un mensaje de error que indica que el depurador no puede desenredar la pila de llamadas si se ha producido una excepción no controlada durante la depuración de código mixto.  
  
## <a name="see-also"></a>Consulte también  
 [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)
