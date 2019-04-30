---
title: "'return' instrucción fuera de función | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 01ef96385d5fe3dccf14a7491e67983d39913280
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63006411"
---
# <a name="return-statement-outside-of-function"></a>'return' instrucción fuera de función
Ha utilizado un `return` instrucción en el ámbito global de su código. El `return` instrucción solo debe aparecer dentro del cuerpo de una función.  
  
 Invocar una función con el `()` operador es una expresión. Todas las expresiones tienen valores; el `return` instrucción se utiliza para especificar el valor devuelto por una función. El formato general es:  
  
```js
  
return [ expression ];  
```  
  
 Cuando el `return` se ejecuta la instrucción, *expresión* se evalúa y se devuelve como el valor de la función. Si no hay ninguna expresión, **indefinido** se devuelve.  
  
 Ejecución de la función detiene cuando el `return` se ejecuta la instrucción, incluso si hay cualquier otra instrucción en el cuerpo de la función. La excepción a esta regla es si el **devolver** instrucción se produce en un **intente** bloque, y no hay correspondiente **finalmente** bloque, el código en el  **Por último** bloque se ejecutará antes de que vuelva la función.  
  
 Si una función devuelve porque llega al final del cuerpo de función sin ejecutar un `return` instrucción, el valor devuelto es el **indefinido** valor (Esto significa que el resultado de la función no se puede usar como parte de una expresión mayor ).  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Quitar el `return` instrucción del cuerpo principal del código (el ámbito global).  
  
## <a name="see-also"></a>Vea también  
 [Return (instrucción)](../../javascript/reference/return-statement-javascript.md)   
 [Objeto de función](../../javascript/reference/function-object-javascript.md)   
 [caller (Propiedad, Function)](../../javascript/reference/caller-property-function-javascript.md)