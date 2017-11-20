---
title: "&#39; devuelto &#39; instrucción fuera de función | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07b633c87dc11b291a5a5783f8121b2a368996d6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="39return39-statement-outside-of-function"></a>&#39; devuelto &#39; instrucción fuera de función
Se usa un `return` instrucción en el ámbito global del código. El `return` instrucción sólo debe aparecer dentro del cuerpo de una función.  
  
 Invocar una función con el `()` operador es una expresión. Todas las expresiones tienen valores; el `return` instrucción se utiliza para especificar el valor devuelto por una función. La forma general es:  
  
```  
  
return [ expression ];  
```  
  
 Cuando el `return` se ejecuta la instrucción, *expresión* se evalúa y se devuelve como el valor de la función. Si no hay ninguna expresión, **indefinido** se devuelve.  
  
 La ejecución de la función detiene cuando el `return` se ejecuta la instrucción, incluso si hay cualquier otra instrucción en el cuerpo de la función. La excepción a esta regla es si la **devolver** instrucción se produce dentro de un **intente** bloque, y no hay correspondiente **finalmente** bloquear, el código el  **Por último,** bloque se ejecutará antes de que la función devuelve.  
  
 Si una función termina porque llega al final del cuerpo de la función sin ejecutar una `return` (instrucción), el valor devuelto es el **indefinido** valor (Esto significa que el resultado de la función no se puede usar como parte de una expresión mayor ).  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Quitar el `return` instrucción desde el cuerpo principal del código (el ámbito global).  
  
## <a name="see-also"></a>Vea también  
 [Return (instrucción)](../../javascript/reference/return-statement-javascript.md)   
 [Objeto de función](../../javascript/reference/function-object-javascript.md)   
 [caller (Propiedad, Function)](../../javascript/reference/caller-property-function-javascript.md)