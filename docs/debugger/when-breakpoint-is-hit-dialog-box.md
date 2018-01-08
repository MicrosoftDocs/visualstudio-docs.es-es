---
title: "Cuando el punto de interrupción es el cuadro de diálogo llamadas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c03e68315c8c0818d6b9cf6a102adde4ea4f8a10
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2018
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Al visitar un punto de interrupción (Cuadro de diálogo)
Con este cuadro de diálogo, es posible personalizar la acción que ocurre cuando se visita un punto de interrupción.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Imprimir un mensaje**  
 Imprime un mensaje con la sintaxis de DebuggerDisplay. Para obtener más información, consulte [utilizando el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Este cuadro de texto también admite palabras clave especiales (como $ADDRESS), que se pueden utilizar por sí solas o dentro de las llaves de una expresión DebuggerDisplay. Las palabras clave disponibles se muestran en el cuadro de diálogo.  
  
 **Continuar la ejecución**  
 Este control se habilita solamente cuando **imprimir un mensaje** está seleccionada. Cuando este control está seleccionado, se puede utilizar un punto de interrupción como punto de seguimiento para hacer un seguimiento la ejecución de programas, en lugar de interrumpirla cuando se visita la ubicación.  
  
## <a name="see-also"></a>Vea también  
 [Usar puntos de interrupción](../debugger/using-breakpoints.md)   
 [Usar el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)