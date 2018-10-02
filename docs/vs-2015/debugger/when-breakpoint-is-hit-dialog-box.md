---
title: Cuando el punto de interrupción es el cuadro de diálogo posicionamiento | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 650e390abde6f3ad99e5a0c30591c8d1530df692
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576350"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Al visitar un punto de interrupción (Cuadro de diálogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [al punto de interrupción es cuadro de diálogo visitas](https://docs.microsoft.com/visualstudio/debugger/when-breakpoint-is-hit-dialog-box).  
  
Con este cuadro de diálogo, es posible personalizar la acción que ocurre cuando se visita un punto de interrupción.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Imprimir un mensaje**  
 Imprime un mensaje con la sintaxis de DebuggerDisplay. Para obtener más información, consulte [utilizando el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Este cuadro de texto también admite palabras clave especiales (como $ADDRESS), que se pueden utilizar por sí solas o dentro de las llaves de una expresión DebuggerDisplay. Las palabras clave disponibles se muestran en el cuadro de diálogo.  
  
 **Continuar ejecución**  
 Este control está habilitado solo cuando **imprimir un mensaje** está seleccionada. Cuando este control está seleccionado, se puede utilizar un punto de interrupción como punto de seguimiento para hacer un seguimiento la ejecución de programas, en lugar de interrumpirla cuando se visita la ubicación.  
  
## <a name="see-also"></a>Vea también  
 [Usar puntos de interrupción](../debugger/using-breakpoints.md)   
 [Usar el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)



