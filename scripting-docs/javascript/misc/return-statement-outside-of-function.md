---
title: "'return' instrucción fuera de función | Microsoft Docs"
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82ba1488692f8e8b59063b8f9a52b0682d27e7f8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096452"
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
  
-   Quitar el `return` instrucción del cuerpo principal del código (el ámbito global).  
  
## <a name="see-also"></a>Vea también  
 [Return (instrucción)](../../javascript/reference/return-statement-javascript.md)   
 [Objeto de función](../../javascript/reference/function-object-javascript.md)   
 [caller (Propiedad, Function)](../../javascript/reference/caller-property-function-javascript.md)