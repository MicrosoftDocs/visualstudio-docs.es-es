---
title: Cuando el punto de interrupción es el cuadro de diálogo posicionamiento | Microsoft Docs
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 560a79892ee50f3d151971f46bcc2c2b7f205d3f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845621"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Al visitar un punto de interrupción (Cuadro de diálogo)
Con este cuadro de diálogo, es posible personalizar la acción que ocurre cuando se visita un punto de interrupción.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Imprimir un mensaje**  
 Imprime un mensaje con la sintaxis de DebuggerDisplay. Para obtener más información, consulte [utilizando el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Este cuadro de texto también admite palabras clave especiales (como $ADDRESS), que se pueden utilizar por sí solas o dentro de las llaves de una expresión DebuggerDisplay. Las palabras clave disponibles se muestran en el cuadro de diálogo.  
  
 **Continuar la ejecución**  
 Este control solo se habilita cuando se selecciona **Imprimir un mensaje**. Cuando este control está seleccionado, se puede utilizar un punto de interrupción como punto de seguimiento para hacer un seguimiento la ejecución de programas, en lugar de interrumpirla cuando se visita la ubicación.  
  
## <a name="see-also"></a>Vea también  
 [Uso de puntos de interrupción](../debugger/using-breakpoints.md)   
 [Usar el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)