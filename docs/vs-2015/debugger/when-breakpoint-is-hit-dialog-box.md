---
title: Cuadro de diálogo Al visitar un punto de interrupción | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a7cd140a22c435df0875c089a69476d3e1e61cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149412"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Al visitar un punto de interrupción (Cuadro de diálogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con este cuadro de diálogo, es posible personalizar la acción que ocurre cuando se visita un punto de interrupción.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Imprimir un mensaje**  
 Imprime un mensaje con la sintaxis de DebuggerDisplay. Para obtener más información, vea [Usar el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Este cuadro de texto también admite palabras clave especiales (como $ADDRESS), que se pueden utilizar por sí solas o dentro de las llaves de una expresión DebuggerDisplay. Las palabras clave disponibles se muestran en el cuadro de diálogo.  
  
 **Continuar la ejecución**  
 Este control solo se habilita cuando se selecciona **Imprimir un mensaje**. Cuando este control está seleccionado, se puede utilizar un punto de interrupción como punto de seguimiento para hacer un seguimiento la ejecución de programas, en lugar de interrumpirla cuando se visita la ubicación.  
  
## <a name="see-also"></a>Consulte también  
 [Usar puntos de interrupción](../debugger/using-breakpoints.md)   
 [Usar el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
