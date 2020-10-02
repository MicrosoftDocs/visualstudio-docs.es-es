---
title: Código mixto e información no mostrada en la ventana Pila de llamadas
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b32fe52b31daa384718eae629d3051bade93959d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808160"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Código mixto e información no mostrada en la ventana Pila de llamadas
Debido a las diferencias entre las pilas de llamadas para código administrado y código nativo, el depurador no siempre puede mostrar toda la pila de llamadas cuando se mezclan los tipos de código. Cuando código nativo llama a código administrado, quizá observe las siguientes discrepancias en la ventana **Pila de llamadas**:

- Puede que el marco nativo inmediatamente encima del código administrado no esté en la ventana **Pila de llamadas**. Para obtener más información, vea [Cómo: Salida del código administrado cuando los marcos nativos no aparecen en la ventana Pila de llamadas](how-to-use-the-call-stack-window.md).

- En el caso de las aplicaciones en modo mixto iniciadas fuera del depurador, es posible que en la ventana **Pila de llamadas** solo se muestre el código administrado y que no se vea ninguno de los marcos nativos.

  Ninguno de estos casos es habitual. En la mayoría de las llamadas nativas a código administrado, las pilas de llamadas se muestran correctamente.

## <a name="see-also"></a>Vea también
- [Cómo: usar la ventana Pila de llamadas](../debugger/how-to-use-the-call-stack-window.md)