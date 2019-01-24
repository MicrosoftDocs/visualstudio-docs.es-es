---
title: Código mixto e información que falta en la ventana Pila de llamadas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 184e1b9a189ced74f93eef92a79c1c7121fdba2b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941117"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Código mixto e información no mostrada en la ventana Pila de llamadas
Debido a las diferencias entre las pilas de llamadas para código administrado y código nativo, el depurador no siempre puede mostrar toda la pila de llamadas cuando se mezclan los tipos de código. Cuando código nativo llama a código administrado, quizá observe las siguientes discrepancias en la ventana **Pila de llamadas**:  
  
- Puede que el marco nativo inmediatamente encima del código administrado no esté en la ventana **Pila de llamadas**. Para obtener más información, vea [Cómo: Salida del código administrado cuando los marcos nativos no aparecen en la ventana Pila de llamadas](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
- En el caso de las aplicaciones en modo mixto iniciadas fuera del depurador, es posible que en la ventana **Pila de llamadas** solo se muestre el código administrado y que no se vea ninguno de los marcos nativos.  
  
  Ninguno de estos casos es habitual. En la mayoría de las llamadas nativas a código administrado, las pilas de llamadas se muestran correctamente.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: usar la ventana Pila de llamadas](../debugger/how-to-use-the-call-stack-window.md)