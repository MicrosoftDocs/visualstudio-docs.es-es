---
title: instrucción ' Return ' fuera de la función | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 32eadcf5ae88dbe64c8ccdb3effbb85bc79f9b32
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816740"
---
# <a name="return-statement-outside-of-function"></a>'return' instrucción fuera de función
Usó una `return` instrucción en el ámbito global del código. La `return` instrucción solo debe aparecer dentro del cuerpo de una función.  
  
 La invocación de una función con el `()` operador es una expresión. Todas las expresiones tienen valores; la `return` instrucción se utiliza para especificar el valor devuelto por una función. El formato general es:  
  
```js
  
return [ expression ];  
```  
  
 Cuando `return` se ejecuta la instrucción, *Expression* se evalúa y se devuelve como el valor de la función. Si no hay ninguna expresión, se devuelve **undefined** .  
  
 La ejecución de la función se detiene cuando `return` se ejecuta la instrucción, incluso si todavía quedan otras instrucciones en el cuerpo de la función. La excepción a esta regla es si la instrucción **Return** se produce dentro de un bloque **try** y hay un bloque **Finally** correspondiente, el código del bloque **Finally** se ejecutará antes de que se devuelva la función.  
  
 Si una función devuelve porque alcanza el final del cuerpo de la función sin ejecutar una `return` instrucción, el valor devuelto es el valor **indefinido** (esto significa que el resultado de la función no se puede usar como parte de una expresión mayor).  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Quite la `return` instrucción del cuerpo principal del código (ámbito global).  
  
## <a name="see-also"></a>Consulte también  
 [Instrucción return](../../javascript/reference/return-statement-javascript.md)   
 [Objeto de función](../../javascript/reference/function-object-javascript.md)   
 [caller (Propiedad, Function)](../../javascript/reference/caller-property-function-javascript.md)