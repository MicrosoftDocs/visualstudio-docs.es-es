---
title: Continuación de la ejecución después de una excepción | Microsoft Docs
description: Obtenga información sobre lo que sucede cuando el depurador interrumpe la ejecución debido a una excepción no controlada. Es posible que pueda continuar la ejecución en el mismo subproceso.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9af71aba1b26c3d8160af229d8c050038800106a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865818"
---
# <a name="continuing-execution-after-an-exception"></a>Continuar la ejecución después de una excepción
Cuando el depurador interrumpa la ejecución debido a una excepción, verá la **aplicación auxiliar de excepciones** de forma predeterminada. Si ha deshabilitado la **aplicación auxiliar de excepciones** en el cuadro de diálogo **Opciones**, se mostrará el cuadro de diálogo **Aplicación auxiliar de excepciones** (C# o Visual Basic) o **Excepción**.

 Cuando aparece la **aplicación auxiliar de excepciones**, puede intentar solucionar el problema que produjo la excepción.

## <a name="managed-and-native-code"></a>Código administrado y nativo
 En el código administrado y nativo, puede continuar la ejecución en el mismo subproceso después de que se haya producido una excepción no controlada. La **aplicación auxiliar de excepciones** desenreda la pila de llamadas en el punto donde se produjo la excepción.

## <a name="mixed-code"></a>Código mixto
 Si se produce una excepción no controlada durante la depuración de código mixto nativo y administrado, las restricciones de sistema operativo impedirán que se desenrede la pila de llamadas. Si intenta rebobinar la pila de llamadas mediante el menú contextual, aparecerá un mensaje de error que indica que el depurador no puede desenredar la pila de llamadas si se ha producido una excepción no controlada durante la depuración de código mixto.

## <a name="see-also"></a>Vea también

- [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)