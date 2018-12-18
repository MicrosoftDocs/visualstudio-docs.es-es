---
title: Continuar la ejecución después de una excepción | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 947a17993fe0e8366149d1cef79c26c68b11d22a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730029"
---
# <a name="continuing-execution-after-an-exception"></a>Continuar la ejecución después de una excepción
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando el depurador interrumpe la ejecución debido a una excepción, aparece un cuadro de diálogo. Para Visual Basic o C#, verá el [Asistente de excepciones](http://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb) cuadro de diálogo, de forma predeterminada. Para C++, verá la versión anterior **excepción** cuadro de diálogo. Si está utilizando Visual Basic o C# pero se ha deshabilitado la **Asistente de excepciones** en el **opciones** cuadro de diálogo, verá el **excepción** cuadro de diálogo.  
  
 Cuando el **Asistente de excepciones** o **excepción** aparece el cuadro de diálogo, puede intentar corregir el problema que provocó la excepción.  
  
## <a name="managed-code"></a>Código administrado  
 En el código administrado, puede continuar la ejecución en el mismo subproceso después de que se haya producido una excepción no controlada. El **Asistente de excepciones** se desenreda la pila de llamadas al punto donde se produjo la excepción.  
  
## <a name="native-code"></a>Código nativo  
 En C/C++ nativo, tiene dos opciones:  
  
-   Puede hacer clic en **interrumpir** e intentar corregir el problema. Mientras está en modo de interrupción, puede desenredar la pila de llamadas con el botón secundario en un marco de la **pila de llamadas** ventana y seleccione **desenredar hasta este marco** en el menú contextual. Al continuar con la depuración, la **excepción** aparece el cuadro de diálogo nuevo si no se ha corregido el problema. En caso contrario, el **excepción** no volverá a aparecer el cuadro de diálogo.  
  
-   Puede hacer clic en **continuar** para continuar la ejecución sin intentar corregir el problema. El **excepción** vuelve a aparecer el cuadro de diálogo.  
  
## <a name="mixed-code"></a>Código mixto  
 Si se produce una excepción no controlada durante la depuración de código mixto nativo y administrado, las restricciones de sistema operativo impedirán que se desenrede la pila de llamadas. Si intenta rebobinar la pila de llamadas mediante el menú contextual, aparecerá un mensaje de error que indica que el depurador no puede desenredar la pila de llamadas si se ha producido una excepción no controlada durante la depuración de código mixto.  
  
## <a name="see-also"></a>Vea también  
 [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)





