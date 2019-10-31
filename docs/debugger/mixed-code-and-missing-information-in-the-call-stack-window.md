---
title: Código mixto e información que falta en la ventana pila de llamadas | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25fb7bc54899d8c9a079d3f2706065d690904540
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187538"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Código mixto e información no mostrada en la ventana Pila de llamadas
Debido a las diferencias entre las pilas de llamadas para código administrado y código nativo, el depurador no siempre puede mostrar toda la pila de llamadas cuando se mezclan los tipos de código. Cuando código nativo llama a código administrado, quizá observe las siguientes discrepancias en la ventana **Pila de llamadas**:

- Puede que el marco nativo inmediatamente encima del código administrado no esté en la ventana **Pila de llamadas**. Para obtener más información, vea [Cómo: salir de código administrado cuando faltan marcos nativos en la ventana pila de llamadas](how-to-use-the-call-stack-window.md).

- En el caso de las aplicaciones en modo mixto iniciadas fuera del depurador, es posible que en la ventana **Pila de llamadas** solo se muestre el código administrado y que no se vea ninguno de los marcos nativos.

  Ninguno de estos casos es habitual. En la mayoría de las llamadas nativas a código administrado, las pilas de llamadas se muestran correctamente.

## <a name="see-also"></a>Vea también
- [Cómo: Usar la ventana Pila de llamadas](../debugger/how-to-use-the-call-stack-window.md)