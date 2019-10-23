---
title: Cuadro de diálogo al visitar un punto de interrupción | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53b19f4dd0d4b0cb97bb33e4895f36c4dc8f670c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728139"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Al visitar un punto de interrupción (Cuadro de diálogo)
Con este cuadro de diálogo, es posible personalizar la acción que ocurre cuando se visita un punto de interrupción.

## <a name="uielement-list"></a>Lista de UIElement
 **Imprimir un mensaje** Imprime un mensaje mediante la sintaxis DebuggerDisplay. Para obtener más información, vea [Using the DebuggerDisplay Attribute](../debugger/using-the-debuggerdisplay-attribute.md).

 Este cuadro de texto también admite palabras clave especiales (como $ADDRESS), que se pueden utilizar por sí solas o dentro de las llaves de una expresión DebuggerDisplay. Las palabras clave disponibles se muestran en el cuadro de diálogo.

 **Continuar la ejecución** Este control solo está habilitado cuando se selecciona **imprimir un mensaje** . Cuando este control está seleccionado, se puede utilizar un punto de interrupción como punto de seguimiento para hacer un seguimiento la ejecución de programas, en lugar de interrumpirla cuando se visita la ubicación.

## <a name="see-also"></a>Vea también
- [Usar puntos de interrupción](../debugger/using-breakpoints.md)
- [Usar el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)